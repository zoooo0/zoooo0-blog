---
title: BestBlogs Issue #85：Harness Engineering（全文抓取）
date: 2026-03-09
category: 技术
tags: [AI周报]
top: 11
---

# BestBlogs Issue #85：Harness Engineering（全文抓取）

> 来源：BestBlogs.dev Newsletter  
> 原文链接：https://www.bestblogs.dev/newsletter/issue85

BestBlogs Issue #85: Harness Engineering
========================================

Hey there! Welcome to BestBlogs.dev Issue #85.

One keyword threads through this week's articles: harnessing. Essays published on martinfowler.com argue that developers' core work is shifting from writing code to building the harness agents depend on—specs, quality gates, and workflow guides. A Chinese podcast title puts it more bluntly: stop working, start setting up the office for your AI. OpenAI's team shipped a million lines of Codex-generated code over five months, not by using a stronger model, but by enforcing structured knowledge bases and rigid architectural constraints. As agents grow more capable, the real competitive edge isn't whether you use AI, but whether you can harness it.

On the BestBlogs.dev front, we've been going deep on AI coding to build out version 2.0. The focus is custom subscription sources and personalized feeds, so everyone can shape their reading experience around their own interests. I'm also developing Skills on top of open APIs for content search, deep reading, and daily operations—all aimed at truly harnessing the future of reading.

Here are 10 highlights worth your attention this week:

🤖 GPT-5.4 lands as OpenAI's first model to unify reasoning, coding, native computer use, deep search, and million-token context in a single package. The standout is native computer use: the model reads screenshots, moves the mouse, and types on the keyboard, surpassing average human performance on OSWorld desktop tasks. A tool-search mechanism cuts agent token consumption by 47%, achieving high capability and low cost simultaneously. Meanwhile, GPT-5.3 Instant optimizes for feel over benchmarks, reducing web hallucination rates by 26.8%—a meaningful step toward making ChatGPT a reliable daily tool.

🏗️ Two essays on martinfowler.com form a cohesive argument this week. The first positions developers "on the loop": the core job becomes building and maintaining the harness that agents run on, with an agentic flywheel where agents not only execute tasks but continuously improve the harness itself. The second introduces a Design-First collaboration framework, aligning on capabilities, components, interactions, interfaces, and implementation before any code is generated, preventing architectural decisions from being silently embedded by AI.

🎬 Pragmatic Engineer sat down with Boris Cherny, the creator of Claude Code, tracing its journey from an Anthropic side project to one of the fastest-growing developer tools. Boris ships 20–30 PRs daily, all 100% AI-generated, without editing a single line by hand. The conversation also reveals the internal debate at Anthropic over whether to release it publicly, how code review is evolving in the AI era, and the layered security architecture behind Claude Code.

🔧 Alibaba's Tmall engineering team identifies the real bottleneck in enterprise AI coding: not agent execution capability, but accurately conveying complex task goals to AI. Their solution is a layered, unified expert knowledge base for systematic entropy reduction, driving a shift from tool-based efficiency to knowledge-driven intelligent development. OpenAI's Codex practice confirms the same insight: 1,500 PRs over five months with zero human coding, scaled through structured knowledge management, rigid architectural constraints, and periodic code entropy cleanup.

📁 Tencent Cloud published what may be the most thorough Chinese-language teardown of OpenClaw's context management, covering a three-tier defense system: preemptive pruning, LLM-based summarization, and post-overflow recovery, plus a cost analysis of each operation's impact on provider KV cache. Essential reading for anyone building long-session agents.

⚡ Small models are rewriting performance expectations. Qwen3.5 releases four models from 0.8B to 9B parameters, all Apache 2.0, fine-tunable on consumer GPUs. The 4B stands out for multimodal and agent capabilities, while 9B punches close to much larger models. Xiaohongshu's open-source FireRed-OCR takes a different angle, turning Qwen3-VL-2B into a dedicated document parsing model through three-stage progressive training, scoring 92.94% on OmniDocBench v1.5 and ranking first among end-to-end solutions, with support for formulas, tables, and handwriting. Both projects prove the same point: targeted training strategies beat brute-force parameter scaling.

🎨 Anthropic's head of design Jenny Wen shares a striking observation: the traditional design process is dead, not because designers chose to change, but because engineers shipping at AI speed forced the shift. Her time on polished mockups dropped from 60–70% to 30–40%, replaced by direct pairing with engineers and even editing code herself. Design work is splitting into two tracks: real-time collaboration supporting engineering execution, and vision design that sets direction 3 to 6 months out.

💡 A three-hour conversation between Meng Yan and Li Jigang starts from one powerful premise: the industrial revolution took away physical labor, AI is taking away mental labor, what remains for humans is heart force. The dialogue extends into the nature of vector spaces, business models shifting from weaving nets to digging wells, and education transforming from pouring water to lighting fire. Two insights worth unpacking on their own: "Your feed is your fate" and "prompts have shapes."

📈 Zapier's VP of Product shares first-hand lessons from running 800 AI agents internally, emphasizing that technology adoption and business transformation must be treated as separate efforts, and that leadership must personally use AI tools for transformation to stick. Insight Partners' co-founder goes further: autonomous agents are the real core of this wave, SaaS per-seat pricing will give way to consumption-based models, and white-collar job displacement will become an election issue within two years.

🌐 A thought experiment written from a 2028 vantage point deserves attention: white-collar job losses trigger consumer spending contraction, which triggers private credit defaults, which pressures mortgage markets, forming a negative feedback loop with no natural brake. Not a prediction, but a systematic framework for reasoning about left-tail risks. Worth a careful read for anyone thinking about AI's economic impact.

Hope this issue sparks some new ideas. Stay curious, and see you next week!

[Subscribe Now](https://www.bestblogs.dev/en#subscribe "Subscribe Now")

Narrow

Table of Contents

Contents
--------

*   [1 GPT-5.4 Released: OpenAI's First Unified Model, Truly Native](https://www.bestblogs.dev/newsletter/issue85#6f17468b)
*   [2 OpenAI Drops New Default GPT-5.3 Model Overnight! Focus on 'De-cringing'! Hands-on: Blazing Fast Instant Gratification! Enhanced Search! OpenAI Staff Reveal Model Switching Strategy](https://www.bestblogs.dev/newsletter/issue85#825a3674)
*   [3 Qwen3.5 Small-Size Models Are Here!](https://www.bestblogs.dev/newsletter/issue85#a8c5578b)
*   [4 FireRed-OCR Open Source Release: New End-to-End SOTA! Xiaohongshu Proposes Low-Cost Document Recognition Training Paradigm](https://www.bestblogs.dev/newsletter/issue85#44e28dc2)
*   [5 The Architecture Behind Open-Source LLMs](https://www.bestblogs.dev/newsletter/issue85#e94961a3)
*   [6 Building Claude Code with Boris Cherny](https://www.bestblogs.dev/newsletter/issue85#8f3d453)
*   [7 Humans and Agents in Software Engineering Loops](https://www.bestblogs.dev/newsletter/issue85#03980cf2)
*   [8 Design-First Collaboration](https://www.bestblogs.dev/newsletter/issue85#0c84d443)
*   [9 Reflections on AI Coding: From Tool Efficiency to Paradigm Shift—What Are We Still Missing?](https://www.bestblogs.dev/newsletter/issue85#7088e92f)
*   [10 Deep Dive into OpenClaw's Context Window Compression: All for Performance and Cost Savings](https://www.bestblogs.dev/newsletter/issue85#83d23d4f)
*   [11 Stop Talking About '10x Developers': AI Agents Aren't Accelerating the SDLC, They're Ending It](https://www.bestblogs.dev/newsletter/issue85#fa13c8a0)
*   [12 1,500 PRs, 0 Humans Coding: Codex-Driven Million-Line Internal Product Practice](https://www.bestblogs.dev/newsletter/issue85#997b2ba8)
*   [13 Stop Working! Go Set Up an Office for AI!](https://www.bestblogs.dev/newsletter/issue85#d72dca9)
*   [14 The design process is dead. Here’s what’s replacing it. | Jenny Wen (head of design at Claude)](https://www.bestblogs.dev/newsletter/issue85#516ace7)
*   [15 Zapier VP of Product on Orchestrating 800+ AI Agents to Manage Everything](https://www.bestblogs.dev/newsletter/issue85#209e104)
*   [16 Deep Dive into Nano Banana 2: Fun Use Cases, High Speed, and High Quality!](https://www.bestblogs.dev/newsletter/issue85#8dce015c)
*   [17 Four Steps of AI Transformation: Individual, Organization, Product, and Business (Part 2)](https://www.bestblogs.dev/newsletter/issue85#b741844)
*   [18 E45 Meng Yan in Conversation with Li Jigang: How Humans Find Their Place](https://www.bestblogs.dev/newsletter/issue85#17ad4f7)
*   [19#445. 20VC: Why Cursor is Dead | The AI Tsunami is Coming, and You Need to be Ready](https://www.bestblogs.dev/newsletter/issue85#31911b6)
*   [20 The 2028 Global Intelligence Crisis: Who Pays the Price?](https://www.bestblogs.dev/newsletter/issue85#6fedf503)

1
[GPT-5.4 Released: OpenAI's First Unified Model, Truly Native](https://www.bestblogs.dev/en/article/6f17468b)
-------------------------------------------------------------------------------------------------------------

[量子位](https://www.bestblogs.dev/articles?sourceId=SOURCE_371003)[qbitai.com](https://www.qbitai.com/2026/03/384345.html)

03-06

4124 words · 17 min

94

![Image 2: GPT-5.4 Released: OpenAI's First Unified Model, Truly Native](https://image.jido.dev/20260306013348_fb5421d8fc51628a29ab215487da1d12.webp)

OpenAI's GPT-5.4 marks the first time reasoning, coding, native computer use, deep web search, and million-token context have been unified in a single model — without sacrificing performance in any individual area. The standout capability is native computer operation: the model interprets screen state and executes mouse and keyboard actions, surpassing human average on desktop benchmarks. A new tool search mechanism also cuts token usage by 47% for Agent tasks, making this a rare case where capability gains and cost efficiency arrive together.

2
[OpenAI Drops New Default GPT-5.3 Model Overnight! Focus on 'De-cringing'! Hands-on: Blazing Fast Instant Gratification! Enhanced Search! OpenAI Staff Reveal Model Switching Strategy](https://www.bestblogs.dev/en/article/825a3674)
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[51CTO技术栈](https://www.bestblogs.dev/articles?sourceId=SOURCE_aef4e8)[mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MjM5ODI5Njc2MA==&mid=2655936771&idx=1&sn=e82b144c32165174666901de0676eb3e)

03-04

3461 words · 14 min

93

![Image 3: OpenAI Drops New Default GPT-5.3 Model Overnight! Focus on 'De-cringing'! Hands-on: Blazing Fast Instant Gratification! Enhanced Search! OpenAI Staff Reveal Model Switching Strategy](https://image.jido.dev/20260306051541_a371b70.png)

GPT-5.3 Instant skips benchmark chasing and focuses on the user experience: fewer preachy disclaimers, sharper intent detection, and better search integration. With hallucination rates down 26.8% in connected mode, it's a meaningful step toward making ChatGPT a reliable daily tool.

3
[Qwen3.5 Small-Size Models Are Here!](https://www.bestblogs.dev/en/article/a8c5578b)
------------------------------------------------------------------------------------

[通义大模型](https://www.bestblogs.dev/articles?sourceId=SOURCE_2ce88a)[mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MzkxMTYyMTAzNA==&mid=2247499936&idx=1&sn=6e7da548b8562ff4e22abcf723af4fe0)

03-03

174 words · 1 min

93

![Image 4: Qwen3.5 Small-Size Models Are Here!](https://image.jido.dev/20260306052225_c568be5.png)

Qwen3.5 releases four compact models from 0.8B to 9B under Apache 2.0, fine-tunable on consumer GPUs. The 4B impresses for multimodal and Agent tasks; the 9B rivals larger models — both well-suited for cost-efficient vertical deployment.

4
[FireRed-OCR Open Source Release: New End-to-End SOTA! Xiaohongshu Proposes Low-Cost Document Recognition Training Paradigm](https://www.bestblogs.dev/en/article/44e28dc2)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[小红书技术REDtech](https://www.bestblogs.dev/articles?sourceId=SOURCE_fb78bd)[mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=Mzg4OTc2MzczNg==&mid=2247494972&idx=1&sn=1c6a1be0908cbe25194a5256b1eec48a)

03-02

4293 words · 18 min

93

![Image 5: FireRed-OCR Open Source Release: New End-to-End SOTA! Xiaohongshu Proposes Low-Cost Document Recognition Training Paradigm](https://image.jido.dev/20260306051816_4418840.jpeg)

FireRed-OCR fine-tunes Qwen3-VL-2B into a specialized document parser via three-stage progressive training, achieving 92.94% on OmniDocBench v1.5 — the top end-to-end result. It handles formulas, tables, and handwriting at industrial quality, and is fully open-source.

5
[The Architecture Behind Open-Source LLMs](https://www.bestblogs.dev/en/article/e94961a3)
-----------------------------------------------------------------------------------------

[ByteByteGo Newsletter](https://www.bestblogs.dev/articles?sourceId=SOURCE_996ae6)[blog.bytebytego.com](https://blog.bytebytego.com/p/the-architecture-behind-open-source)

03-02

1654 words · 7 min

92

![Image 6: The Architecture Behind Open-Source LLMs](https://image.jido.dev/20260302170628_0b745b95-60a3-498f-baf4-cfef00f0f9d4_3042x1626.png)

A concise comparative breakdown of six leading open-weight LLMs, covering MoE design, attention mechanism tradeoffs, and post-training strategies — with practical guidance on what to actually evaluate when choosing a model. Essential reading for engineers navigating the current open-source landscape.

6
[Building Claude Code with Boris Cherny](https://www.bestblogs.dev/en/video/8f3d453)
------------------------------------------------------------------------------------

[The Pragmatic Engineer](https://www.bestblogs.dev/articles?sourceId=SOURCE_45e77651)[youtube.com](https://www.youtube.com/watch?v=julbw1JuAz0)

03-04

21313 words · 86 min

94

![Image 7: Building Claude Code with Boris Cherny](https://image.jido.dev/20260305070617_hqdefault.jpg)

Pragmatic Engineer sits down with Boris Cherny, the creator of Claude Code, tracing its journey from an internal Anthropic side project to one of the fastest-growing developer tools available. Boris walks through his daily workflow — 20-30 PRs per day, 100% AI-generated, not a single line written by hand — and shares the internal debate over whether to release it at all. The conversation covers how code review is evolving in an AI-first environment, the layered security design behind Claude Code's architecture, and Boris's take on which engineering skills will matter most going forward. The printing press analogy running through the episode makes for a thought-provoking listen.

7
[Humans and Agents in Software Engineering Loops](https://www.bestblogs.dev/en/article/03980cf2)
------------------------------------------------------------------------------------------------

[Martin Fowler](https://www.bestblogs.dev/articles?sourceId=SOURCE_913551)[martinfowler.com](https://martinfowler.com/articles/exploring-gen-ai/humans-and-agents.html)

03-04

1603 words · 7 min

93

![Image 8: Humans and Agents in Software Engineering Loops](https://image.jido.dev/20260206060522_donkey-card.png)

This article offers a clear framework for thinking about the developer's role in an AI-assisted workflow, identifying three positions: humans outside the loop (vibe coding), humans inside the loop (manually reviewing every artifact), and humans on the loop. The author argues the third is the right place to be — where developers shift from writing code to building and maintaining the "harness" that guides agents: the specs, quality checks, and workflow instructions that shape what agents produce. The piece goes further to describe an "agentic flywheel," where agents not only execute tasks but continuously evaluate and improve the harness itself.

8
[Design-First Collaboration](https://www.bestblogs.dev/en/article/0c84d443)
---------------------------------------------------------------------------

[Martin Fowler](https://www.bestblogs.dev/articles?sourceId=SOURCE_913551)[martinfowler.com](https://martinfowler.com/articles/reduce-friction-ai/design-first-collaboration.html)

03-03

2226 words · 9 min

93

The author identifies a core problem with AI-assisted coding: AI skips the design phase entirely, silently embedding every architectural decision into generated code and turning code review into an exhausting exercise in reverse-engineering. The proposed solution, "Design-First," structures the collaboration into five sequential levels — capabilities, components, interactions, contracts, implementation — with no code until the design is agreed at each step. This isn't process ceremony; it's cognitive load management that forces decisions to happen at the right level of abstraction. For developers who regularly use AI coding assistants, this article offers a practical and well-reasoned collaboration framework worth adopting.

9
[Reflections on AI Coding: From Tool Efficiency to Paradigm Shift—What Are We Still Missing?](https://www.bestblogs.dev/en/article/7088e92f)
--------------------------------------------------------------------------------------------------------------------------------------------

[大淘宝技术](https://www.bestblogs.dev/articles?sourceId=SOURCE_efc2de)[mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MzAxNDEwNjk5OQ==&mid=2650542970&idx=1&sn=231a9b78e5c7e1054aa26e86556e8ed8)

03-02

7601 words · 31 min

92

![Image 9: Reflections on AI Coding: From Tool Efficiency to Paradigm Shift—What Are We Still Missing?](https://image.jido.dev/20260302124143_b705d48.png)

A thoughtful piece from Alibaba's Tmall tech team: the core bottleneck in enterprise AI Coding isn't agent execution, but accurately conveying complex task goals to AI. The solution is a layered, unified expert knowledge base that reduces information entropy and drives a shift from tool-level efficiency gains to a knowledge-driven intelligent development paradigm.

10
[Deep Dive into OpenClaw's Context Window Compression: All for Performance and Cost Savings](https://www.bestblogs.dev/en/article/83d23d4f)
-------------------------------------------------------------------------------------------------------------------------------------------

[腾讯云开发者](https://www.bestblogs.dev/articles?sourceId=SOURCE_efac5b)[mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MzI2NDU4OTExOQ==&mid=2247694674&idx=1&sn=acae1fec749562f39219e2b13af9f065)

03-04

9892 words · 40 min

92

![Image 10: Deep Dive into OpenClaw's Context Window Compression: All for Performance and Cost Savings](https://image.jido.dev/20260304033618_281b31f.jpeg)

A deep dive into OpenClaw's context management source code, covering its three-layer defense — preventive pruning, LLM-based compaction, and overflow recovery — plus a detailed analysis of how each operation affects Provider KV cache costs. One of the most thorough technical breakdowns of long-session context management for AI agents available in Chinese.

11
[Stop Talking About '10x Developers': AI Agents Aren't Accelerating the SDLC, They're Ending It](https://www.bestblogs.dev/en/article/fa13c8a0)
-----------------------------------------------------------------------------------------------------------------------------------------------

[InfoQ 中文](https://www.bestblogs.dev/articles?sourceId=SOURCE_8f2a9f)[mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MjM5MDE0Mjc4MA==&mid=2651276696&idx=2&sn=d8c3bd5cd6a2d3c96df4b87948831b24)

03-01

3384 words · 14 min

92

![Image 11: Stop Talking About '10x Developers': AI Agents Aren't Accelerating the SDLC, They're Ending It](https://image.jido.dev/20260302001659_9ebbfe7.png)

This piece makes a sharp argument: AI agents aren't accelerating the software development lifecycle — they're ending it. The author works through each SDLC phase systematically: requirements become a byproduct of iteration, design emerges through collaboration, tests are generated alongside code, PR review becomes a legacy ritual, and observability evolves from a passive dashboard into the feedback loop driving the entire system. The conclusion is that only two core capabilities survive: context engineering and observability. A clearly argued piece worth engaging with seriously.

12
[1,500 PRs, 0 Humans Coding: Codex-Driven Million-Line Internal Product Practice](https://www.bestblogs.dev/en/article/997b2ba8)
--------------------------------------------------------------------------------------------------------------------------------

[AI前线](https://www.bestblogs.dev/articles?sourceId=SOURCE_458cfe)[mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MzU1NDA4NjU2MA==&mid=2247657188&idx=2&sn=a68f1062d1f1e0faa8b076849cfb42e9)

03-01

6416 words · 26 min

92

OpenAI's engineering team used Codex to generate 1 million lines of code and 1,500 PRs over 5 months — with no human-written code. The article distills what made it work: structured knowledge management, rigid architectural constraints, agent-accessible observability tooling, and periodic entropy cleanup. A concise blueprint for scaling agent-driven development.

13
[Stop Working! Go Set Up an Office for AI!](https://www.bestblogs.dev/en/podcast/d72dca9)
-----------------------------------------------------------------------------------------

[AI炼金术](https://www.bestblogs.dev/podcasts?sourceId=SOURCE_29b54a)[xiaoyuzhoufm.com](https://www.xiaoyuzhoufm.com/episode/69a6dc8ba374f44ffa797457)

03-03

28034 words · 113 min

93

![Image 12: Stop Working! Go Set Up an Office for AI!](https://image.jido.dev/20251127045527_cef25284)

Two AI founders share their engineering workflow in the Agent era: the job has shifted from writing code to building environments for AI, a three-step flow (plan → run → validate) is now the daily norm, and judgment bandwidth — not execution speed — is the new productivity ceiling. Worth listening to for anyone curious about what AI-first engineering actually looks like in practice.

14
[The design process is dead. Here’s what’s replacing it. | Jenny Wen (head of design at Claude)](https://www.bestblogs.dev/en/video/516ace7)
--------------------------------------------------------------------------------------------------------------------------------------------

[Lenny's Podcast](https://www.bestblogs.dev/articles?sourceId=SOURCE_8e0b51)[youtube.com](https://www.youtube.com/watch?v=eh8bcBIAAFo)

03-01

6060 words · 25 min

93

![Image 13: The design process is dead. Here’s what’s replacing it. | Jenny Wen (head of design at Claude)](https://image.jido.dev/20260306045125_hqdefault.jpg)

Anthropic's head of design Jenny Wen shares her firsthand observations on how the design role is transforming in the AI era. Her core argument: the traditional "discover-diverge-converge" design process is dead — not because designers chose to abandon it, but because engineers shipping at AI-assisted speed forced the change. Design work is now splitting into two modes: real-time execution support alongside engineers, and shorter-horizon vision work spanning 3 to 6 months rather than years. She also details her own workflow shift — time spent on polished mockups has dropped from 60-70% to 30-40%, with far more time now spent on paired collaboration with engineers and direct code-level work. A valuable firsthand account for any designer navigating this transition.

15
[Zapier VP of Product on Orchestrating 800+ AI Agents to Manage Everything](https://www.bestblogs.dev/en/video/209e104)
-----------------------------------------------------------------------------------------------------------------------

[Product School](https://www.bestblogs.dev/articles?sourceId=SOURCE_22ca64)[youtube.com](https://www.youtube.com/watch?v=05wREBRW-40)

03-03

11522 words · 47 min

92

![Image 14: Zapier VP of Product on Orchestrating 800+ AI Agents to Manage Everything](https://image.jido.dev/20260306021824_hqdefault.jpg)

Zapier's VP of Product shares firsthand enterprise AI transformation practices: 800 internal AI agents, a clear distinction between adoption and transformation, and a strong argument that leadership must personally use AI tools for change to take hold. The core difference between traditional and agentic workflows? The ability to reason and dynamically reroute.

16
[Deep Dive into Nano Banana 2: Fun Use Cases, High Speed, and High Quality!](https://www.bestblogs.dev/en/article/8dce015c)
---------------------------------------------------------------------------------------------------------------------------

[阿真Irene](https://www.bestblogs.dev/articles?sourceId=SOURCE_581a19)[mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MzkxNzYzODgwNw==&mid=2247496575&idx=1&sn=b73502454851b048d618096de62d5c03)

03-04

13755 words · 56 min

92

![Image 15: Deep Dive into Nano Banana 2: Fun Use Cases, High Speed, and High Quality!](https://image.jido.dev/20260304135841_b7cbc2e.png)

A thorough hands-on review of Gemini 3.1 Flash Image: improved text rendering accuracy, significantly better character consistency, and new support for extreme aspect ratios like 1:4 and 1:8. Comes with extensive ready-to-use prompts — useful for anyone looking to iterate quickly on design and content creation at lower cost.

17
[Four Steps of AI Transformation: Individual, Organization, Product, and Business (Part 2)](https://www.bestblogs.dev/en/podcast/b741844)
-----------------------------------------------------------------------------------------------------------------------------------------

[AI炼金术](https://www.bestblogs.dev/podcasts?sourceId=SOURCE_29b54a)[xiaoyuzhoufm.com](https://www.xiaoyuzhoufm.com/episode/69a58d3186a265e92b788771)

03-02

2573 words · 11 min

92

The biggest mistake in AI product development is adding AI to features instead of helping users complete real jobs. This podcast presents a three-step framework — deconstruct, redesign, disrupt — and maps out four AI-native startup paths: unlocking new markets, wrapping mature tech, selling infrastructure, and transforming traditional industries. Practical and grounded with real-world examples throughout.

18
[E45 Meng Yan in Conversation with Li Jigang: How Humans Find Their Place](https://www.bestblogs.dev/en/podcast/17ad4f7)
------------------------------------------------------------------------------------------------------------------------

[无人知晓](https://www.bestblogs.dev/podcasts?sourceId=SOURCE_33e2dd)[xiaoyuzhoufm.com](https://www.xiaoyuzhoufm.com/episode/69a64629de29766da93331ec)

03-03

3805 words · 16 min

94

![Image 16: E45 Meng Yan in Conversation with Li Jigang: How Humans Find Their Place](https://image.jido.dev/20260303232418_440f92c.png)

This three-hour conversation between Meng Yan and Li Jigang centers on a deceptively simple premise: the Industrial Revolution took physical labor, AI is taking cognitive labor, and what remains for humans is what they call "heart force" — will, intuition, and aesthetic sensibility. From there, the conversation moves through the nature of the vector world, the shift in business models from "weaving networks" to "drilling deep wells," the fork between amplifying human distinctiveness through AI versus withdrawing from thinking altogether, and the evolution of education from knowledge-pouring to spark-finding. Li Jigang's two observations — "Your feed is your fate" and "prompts have shape" — are each worth sitting with independently. Worth listening to for anyone thinking seriously about what it means to be human in the AI era, beyond the technical discussion.

19
[#445. 20VC: Why Cursor is Dead | The AI Tsunami is Coming, and You Need to be Ready](https://www.bestblogs.dev/en/podcast/31911b6)
-----------------------------------------------------------------------------------------------------------------------------------

[跨国串门儿计划](https://www.bestblogs.dev/podcasts?sourceId=SOURCE_938310)[xiaoyuzhoufm.com](https://www.xiaoyuzhoufm.com/episode/69a5a5b5a22480add6b6be30)

03-02

1576 words · 7 min

92

Insight Partners co-founder Jerry Murdock argues autonomous agents are the real core of this AI wave — tools like Cursor are already facing obsolescence, seat-based SaaS pricing will give way to consumption models, and white-collar displacement will become an election issue within two years.

20
[The 2028 Global Intelligence Crisis: Who Pays the Price?](https://www.bestblogs.dev/en/article/6fedf503)
---------------------------------------------------------------------------------------------------------

[Datawhale](https://www.bestblogs.dev/articles?sourceId=SOURCE_4688eb)[mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MzIyNjM2MzQyNg==&mid=2247719943&idx=1&sn=ad3690fe18437d8254227099bea28bcd)

02-27

12468 words · 50 min

92

![Image 17: The 2028 Global Intelligence Crisis: Who Pays the Price?](https://image.jido.dev/20260306050154_e7d5bf7.jpeg)

A thought experiment written from a 2028 vantage point, tracing AI's economic left-tail risks: white-collar displacement → consumer spending contraction → private credit defaults → mortgage market stress — a feedback loop with no natural brake. Not a prediction, but a rigorous risk scenario worth reading carefully for anyone thinking about AI's macroeconomic implications.
