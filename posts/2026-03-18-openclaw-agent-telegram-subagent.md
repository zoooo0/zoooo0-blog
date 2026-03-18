---
title: 我对 OpenClaw 又改观了：让 Agent 既能私聊，又能被调度协作
date: 2026-03-18
category: AI
tags: OpenClaw
top: 29
---

今天在 Linux.do 看到一篇挺实用的 OpenClaw 配置经验帖，核心是在 **同一个 OpenClaw 体系里，让不同 Agent 既能作为独立 Telegram Bot 私聊，又能被主 Agent 当作 subagent 调度协作**。

我把关键思路整理成一版更适合回看的笔记。

## 这篇文章主要讲了什么

原帖标题：**《我对 Openclaw 又改观了。如何让你的 Agent 可以跟你私聊，还能够被调度、协作？》**  
原文地址：<https://linux.do/t/topic/1684138>

作者的核心思路是三层拆分：

1. **入口层**：给每个 Agent 配一个独立的 Telegram Bot Token
2. **路由层**：把不同 Telegram 账号路由到不同 Agent
3. **权限层**：通过 `subagents.allowAgents` 指定谁可以调度谁

这样做完之后，一个 Agent 就不只是“后台工具人”，而是：

- 平时可以作为独立 Bot 跟你单聊
- 需要联动时，又能被主 Agent 拉去当 subagent 协作

这个思路一下就把 OpenClaw 从“单机器人”变成了“多 Agent 组织架构”。

---

## 第一层：给每个 Agent 一个独立 Telegram 入口

文章先从 `channels.telegram.accounts` 下手。

大意就是：

- `default` 对应主 Bot
- `study` 对应学习 Agent
- `finance` 对应理财 Agent

示例结构像这样：

```json
{
  "channels": {
    "telegram": {
      "accounts": {
        "default": {
          "enabled": true,
          "botToken": "主指挥官 token",
          "dmPolicy": "pairing"
        },
        "study": {
          "enabled": true,
          "botToken": "学习 Agent token",
          "dmPolicy": "pairing"
        },
        "finance": {
          "enabled": true,
          "botToken": "理财 Agent token",
          "dmPolicy": "pairing"
        }
      }
    }
  }
}
```

这一步解决的是：**每个 Agent 都有自己的对外入口，可以被单独聊天。**

---

## 第二层：把 Telegram 账号路由到对应 Agent

只有 Bot Token 还不够，还需要告诉 OpenClaw：

- 哪个 Telegram account 对应哪个 Agent

文章里用的是 `bindings`。

类似：

```json
{
  "bindings": [
    {
      "agentId": "commander",
      "match": { "channel": "telegram", "accountId": "default" }
    },
    {
      "agentId": "study",
      "match": { "channel": "telegram", "accountId": "study" }
    },
    {
      "agentId": "finance",
      "match": { "channel": "telegram", "accountId": "finance" }
    }
  ]
}
```

做到这里，多个 Telegram Bot 就真正“各归其位”了。

也就是说：

- 你找 `study` 这个 Bot，说话的就是 `study` Agent
- 你找 `finance` 这个 Bot，说话的就是 `finance` Agent

这就不再是“一个 Bot 套多个身份”，而是多入口多 Agent 的真实路由。

---

## 第三层：让主 Agent 能调度其他 Agent

这一步是整篇最关键的地方。

文章提到，要在 `agents.list` 里给主 Agent 配：

- `subagents.allowAgents`

例如：

```json
{
  "agents": {
    "list": [
      {
        "id": "commander",
        "name": "中央指挥官",
        "subagents": {
          "allowAgents": ["study", "finance", "research"]
        }
      },
      {
        "id": "study",
        "name": "学习训练 Agent"
      },
      {
        "id": "finance",
        "name": "理财 Agent"
      }
    ]
  }
}
```

这意味着：

- `commander` 可以把 `study / finance / research` 当成小弟调度
- 但这些 Agent 自己仍然保留独立 Telegram 身份

这个设计非常像一个轻量组织架构：

- 每个 Agent 有自己的岗位和入口
- 主 Agent 负责分工协作
- 各自又能单独服务

---

## 第四层（可选）：允许互相调度

文章还提到一个更进阶的玩法：

如果你想让 Agent 之间互相调度，还需要提高嵌套深度，比如：

```json
{
  "agents": {
    "defaults": {
      "subagents": {
        "maxSpawnDepth": 2,
        "maxChildrenPerAgent": 5
      }
    }
  }
}
```

也就是说：

- 不只是老板派任务给组长
- 组长还可以继续派任务给组员

不过这一层复杂度就明显高了，适合已经比较熟悉 OpenClaw 结构的人继续玩。

---

## 第五层：如果不想反复收配对码

原帖还顺手解决了一个很实际的问题：

**Bot 私聊时，如果老是要配对 / 收验证码，会很烦。**

做法是在账号下加 `allowFrom`，把固定 user id 放进去：

```json
{
  "channels": {
    "telegram": {
      "accounts": {
        "study": {
          "dmPolicy": "pairing",
          "allowFrom": ["12345678"]
        }
      }
    }
  }
}
```

这样之后就会顺手很多。

---

## 这篇文章最有价值的地方

我觉得它真正有价值的，不只是几个配置片段，而是**思路变了**。

以前容易把 OpenClaw 理解成：

- 一个 Bot
- 一个 Agent
- 一个对话入口

但这篇文章给出的角度是：

- **多个 Agent = 多个岗位**
- **多个 Telegram Bot = 多个入口**
- **主 Agent = 调度中心**
- **subagent = 业务执行单元**

一旦这么看，OpenClaw 的玩法就不是“聊天机器人”，而更像是：

- 一个小型 AI 团队
- 一个可调度的数字组织
- 或者一个多工种的自动化工作流系统

这也是我觉得它“让人改观”的地方。

---

## 我顺手想到的实际用法

如果把这个模式放到真实场景里，其实可以很自然地拆成：

- **commander**：总控 / 跟主人对话
- **study**：学习、资料整理、写总结
- **finance**：账单、理财、消费记录
- **research**：联网搜索、抓资料、生成调研
- **content**：写博客、整理素材、润色发布

然后每个 Agent：

- 自己能私聊
- 也能在需要时被上级调度

这套东西一旦稳下来，OpenClaw 的体验会比“单 Agent 一把梭”清晰很多。

---

## 总结

想实现“每个 Agent 都有独立 Telegram，同时还能被主 Agent 调度”，至少要同时搞定三层：

- **accounts**：给每个 Agent 配 bot token
- **bindings**：把入口绑到对应 Agent
- **subagents.allowAgents**：规定谁能调谁

原帖作者后来甚至扩展到了更大的组织结构：

- 一个董事长
- 四个组长
- 每组两个人
- 再加组群和全体群

这已经不是单个 Bot 的玩法了，而是接近“AI 组织架构试验”。

如果你也在折腾 OpenClaw，多 Agent 协作这条线，确实值得认真玩一下。

---

## 来源

- 原帖：<https://linux.do/t/topic/1684138>
- 标题：**我对 Openclaw 又改观了。如何让你的Agent可以跟你私聊，还能够被调度、协作？更新具体架构**
- 发布时间：2026-03-03
