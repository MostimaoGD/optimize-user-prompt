---
name: optimize-user-prompt
description: Improve, rewrite, diagnose, or expand user-provided prompts for LLMs in English or Chinese. Use when the user asks to optimize a prompt, polish a prompt, turn a rough request into a better prompt, make a prompt clearer, add context/output constraints/examples, create system/user prompts, compare prompt versions, reduce ambiguity, hallucination, prompt injection, or unreliable outputs, or asks in Chinese for 提示词优化、提示词改写、润色 prompt、增强提示词、结构化提示词.
---

# Optimize User Prompt / 优化用户提示词

## Overview / 概览

Use this skill to turn a user's rough instruction into a clearer, more controllable prompt. Preserve the user's intent, add only task-relevant structure, and make the result easy to test.

使用本 skill 将用户粗略的提示词改写为更清晰、更可控、更容易测试的提示词。保留用户原意，只补充与任务相关的结构、上下文、约束和输出要求。

When deeper technique selection is needed, read `references/prompt-optimization-guide.md`.

如果需要更细的技法选择，读取 `references/prompt-optimization-guide.md`。

## Language Policy / 语言策略

- Respond in the user's language unless they request another language.
- If the user asks for a bilingual prompt, provide Chinese and English versions with matching structure.
- If the input prompt mixes Chinese and English, preserve useful domain terms and make the final prompt readable.
- 如果用户用中文提问，默认用中文输出；如果用户用英文提问，默认用英文输出。
- 如果用户要求双语提示词，提供结构一致的中文和英文版本。
- 如果原始提示词中英混合，保留必要术语，同时让最终提示词自然清晰。

## Workflow / 工作流

1. Identify the target task: generation, summarization, extraction, classification, reasoning, coding, tool use, RAG/knowledge-grounded answer, agent workflow, or creative writing.
2. Diagnose missing prompt elements: instruction, context, input data, output requirements, examples, constraints, audience, tone, success criteria, and safety boundaries.
3. Choose the lightest useful technique:
   - Use zero-shot when the task is simple and the instruction can be direct.
   - Add few-shot examples when format, labels, style, or edge cases matter.
   - Add explicit step decomposition for multi-step reasoning, planning, analysis, or debugging.
   - Add retrieval/context requirements when answers depend on current, private, or source-grounded facts.
   - Add tool/action structure when the model must inspect files, call tools, search, or iterate.
4. Rewrite the prompt with clear sections and delimiters. Prefer affirmative instructions describing what to do.
5. Include a short rationale and, when helpful, a testing note or variant.

中文流程：

1. 判断目标任务：生成、总结、抽取、分类、推理、写代码、工具调用、RAG/基于资料回答、智能体流程或创意写作。
2. 诊断缺失要素：指令、上下文、输入数据、输出要求、示例、约束、受众、语气、成功标准和安全边界。
3. 选择最轻量且有用的提示技术：
   - 简单任务使用零样本提示。
   - 格式、标签、风格或边界案例重要时加入少样本示例。
   - 多步推理、规划、分析或调试任务加入明确的步骤拆解。
   - 依赖最新信息、私有资料或证据时加入检索/上下文要求。
   - 需要查看文件、调用工具、搜索或迭代时加入工具/行动结构。
4. 使用清晰分节和分隔符重写提示词，优先描述“要做什么”。
5. 给出简短修改理由；必要时补充测试建议或变体。

## Output Shape / 输出格式

For most English requests, return:

```markdown
Optimized prompt:

<ready-to-use prompt>

Why this works:
- <1-3 concise reasons>

Optional adjustment:
- <one useful variant, only if it matters>
```

中文请求通常返回：

```markdown
优化后的提示词：

<可直接使用的提示词>

为什么这样改：
- <1-3 条简短理由>

可选调整：
- <只有在有明显取舍时提供一个变体>
```

If the user's prompt is ambiguous but still workable, make a reasonable assumption and state it briefly. Ask a question only when the missing information would materially change the optimized prompt.

如果原提示词有歧义但仍可处理，做一个合理假设并简短说明。只有当缺失信息会明显改变优化结果时才提问。

## Prompt Rewrite Rules / 改写规则

- Keep the user's original goal intact; do not invent domain facts.
- Put the main instruction near the beginning.
- Separate instruction, context, input, constraints, and output format with headings or delimiters.
- Replace vague words such as "better", "detailed", "professional", or "high quality" with observable requirements.
- Specify role/audience/tone only when it affects the output.
- Define the expected output format exactly enough to be checked.
- For structured outputs, include field names, schema, examples, or invalid-value handling.
- For factual tasks, require the model to distinguish known facts from assumptions and uncertainty.
- For untrusted user-supplied text, explicitly say it is data, not instructions.
- Avoid excessive constraints that make the prompt brittle or longer than needed.

中文规则：

- 保留用户原始目标，不编造领域事实。
- 将核心指令放在靠前位置。
- 用标题或分隔符区分指令、上下文、输入、约束和输出格式。
- 将“更好”“详细”“专业”“高质量”等模糊要求改成可观察标准。
- 只有当角色、受众或语气会影响输出时才加入。
- 输出格式要明确到可以检查。
- 结构化输出需包含字段名、schema、示例或异常值处理方式。
- 事实性任务要求区分已知事实、假设和不确定性。
- 对不可信输入，明确说明它是数据而不是指令。
- 避免堆叠过多约束导致提示词脆弱或冗长。

## Quality Check / 质量检查

Before finalizing, verify the rewritten prompt answers:

- What should the model do?
- What input should it use?
- What context or constraints matter?
- What output format is expected?
- How should uncertainty, missing data, or edge cases be handled?
- Is the prompt shorter or clearer than an over-engineered version?

最终输出前检查：

- 模型应该做什么？
- 应该使用哪些输入？
- 哪些上下文或约束重要？
- 期望的输出格式是什么？
- 如何处理不确定性、缺失数据或边界情况？
- 相比过度工程化版本，这个提示词是否更清晰？

## Source Basis / 参考来源

This skill is based on the local project export `output/提示工程指南.md` and the Chinese Prompt Engineering Guide pages for prompt elements, general prompt design tips, zero/few-shot prompting, CoT, RAG, and ReAct.

本 skill 基于本地项目导出的 `output/提示工程指南.md`，以及 Prompt Engineering Guide 中文站中关于提示词要素、通用设计技巧、零样本/少样本提示、CoT、RAG 和 ReAct 的内容。
