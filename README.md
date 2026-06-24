# Optimize User Prompt

## 中文

一个用于 Codex 的提示词优化 skill，可以把用户粗略的提示词改写成更清晰、更可靠、更容易测试的 LLM 指令。

这个 skill 参考了 Prompt Engineering Guide 中的实践模式，包括提示词要素、零样本提示、少样本提示、任务拆解、RAG/基于资料的回答、ReAct 风格工具流程，以及提示词注入防护。

### 功能

适用于以下场景：

- 优化、润色或重写粗略提示词
- 补充更清晰的任务指令、上下文、约束和输出格式
- 把模糊需求转换成结构化提示词
- 在格式、风格或边界案例重要时加入 few-shot 示例
- 改进抽取、分类、推理、代码、RAG 或工具调用类提示词
- 降低歧义、幻觉风险和提示词注入风险

### 使用示例

调用方式：

```text
Use $optimize-user-prompt to improve this prompt:

帮我写一篇介绍人工智能的文章。
```

输出风格示例：

```text
优化后的提示词：

请为高中生写一篇介绍人工智能的中文文章。

要求：
- 800-1000 字
- 用通俗语言解释概念，避免堆砌术语
- 包含 3 个日常应用例子
- 结尾总结人工智能的机会与风险

输出结构：
标题
引言
正文
总结

为什么这样改：
- 明确了受众、长度、语言风格和输出结构。
- 把“介绍人工智能”拆成可检查的内容要求。
```

### 安装

把本文件夹复制到 Codex skills 目录：

```text
~/.codex/skills/optimize-user-prompt
```

Windows 通常是：

```text
C:\Users\<you>\.codex\skills\optimize-user-prompt
```

安装后如未立即生效，可以重启或重新加载 Codex。

### 文件结构

```text
optimize-user-prompt/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── prompt-optimization-guide.md
```

- `SKILL.md`：核心工作流和触发描述。
- `agents/openai.yaml`：Codex UI 元数据。
- `references/prompt-optimization-guide.md`：详细的提示词优化规则、模板和改写模式。

### 参考来源

本 skill 基于本地中文 Prompt Engineering Guide 导出内容，以及公开网站：

[https://www.promptingguide.ai/zh](https://www.promptingguide.ai/zh)

---

## English

A Codex skill for rewriting rough user prompts into clearer, more reliable, and easier-to-test LLM instructions.

This skill is based on practical patterns from the Prompt Engineering Guide, including prompt elements, zero-shot prompting, few-shot prompting, task decomposition, RAG/source-grounded prompting, ReAct-style tool workflows, and prompt injection resistance.

### What It Does

Use this skill when you want to:

- Optimize, polish, or rewrite a rough prompt
- Add clearer task instructions, context, constraints, and output formats
- Convert vague requests into structured prompts
- Add few-shot examples when format, style, or edge cases matter
- Improve prompts for extraction, classification, reasoning, coding, RAG, or tool-use workflows
- Reduce ambiguity, hallucination risk, and prompt injection exposure

### Example

Invoke the skill with:

```text
Use $optimize-user-prompt to improve this prompt:

Write an article introducing artificial intelligence.
```

Expected style of output:

```text
Optimized prompt:

Write a Chinese article introducing artificial intelligence for high school students.

Requirements:
- 800-1000 Chinese characters
- Explain concepts in plain language and avoid jargon overload
- Include 3 everyday application examples
- End with a brief summary of AI opportunities and risks

Output structure:
Title
Introduction
Body
Conclusion

Why this works:
- It defines the audience, length, language style, and output structure.
- It turns a broad topic into concrete, checkable requirements.
```

### Installation

Copy this folder into your Codex skills directory:

```text
~/.codex/skills/optimize-user-prompt
```

On Windows, this is typically:

```text
C:\Users\<you>\.codex\skills\optimize-user-prompt
```

After installation, restart or reload Codex if needed so the skill can be discovered.

### Files

```text
optimize-user-prompt/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── prompt-optimization-guide.md
```

- `SKILL.md`: Core workflow and trigger description.
- `agents/openai.yaml`: UI metadata for Codex.
- `references/prompt-optimization-guide.md`: Detailed prompt optimization heuristics, templates, and rewrite patterns.

### Source Basis

This skill was created from a local Chinese export of the Prompt Engineering Guide and the public guide at:

[https://www.promptingguide.ai/zh](https://www.promptingguide.ai/zh)
