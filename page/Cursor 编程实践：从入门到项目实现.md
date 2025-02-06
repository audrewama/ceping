# Cursor 编程实践：从入门到项目实现

自从9月份开始，我完全转向使用 Cursor 进行编程，并在短短几个月内成功开发了五六个小型网站。通过论坛中各位大佬分享的技巧和教程，我学到了很多。现在，我想分享一下我的使用心得，希望能对大家有所帮助。

## Cursor 的敏捷开发体验

在过去的几个月中，我主要利用 Cursor 进行个人项目的敏捷开发。每个项目的开发周期基本控制在10天以内，因此项目体量不大，基本都是从零开始逐步规划和实现。项目类型主要集中在 LLM 擅长的 Web 开发领域，整体使用体验非常流畅，最终呈现的效果也让我非常满意。

## Cursor 的高效使用技巧

在 Cursor 的使用过程中，我并没有过多折腾工具，而是以实用至上。以下是我总结的一些高效使用技巧，供大家参考。

### 1. 快捷键操作

- **`Ctrl+L`**：唤起聊天栏。这是最基础的功能。
- **`Ctrl+K`**：编辑代码块。选中部分代码后使用该快捷键，可以直接让 LLM 修改或生成代码片段。适合处理具体的代码细节，如方法调整或生成内容。
- **`Ctrl+回车`**：使用整个项目文件作为上下文进行提问。这个功能在大方向提问时非常有用，但需要注意适合选择使用。

### 2. 模型选择

我绝大多数时候使用的是 `claude-3-5-sonnet-20241022` 模型。它响应速度快，理解能力强，偶尔还能用幽默的语气回答问题，使用体验非常棒。

### 3. Prompt 集成

在 `cursor setting` -> `general` -> `Rules for Al` 中，可以填入以下 prompt，以优化 LLM 的回答质量：

markdown
DO NOT GIVE ME HIGH LEVEL STUFF, IF I ASK FOR FIX OR EXPLANATION, I WANT ACTUAL CODE OR EXPLANATION!!! I DON'T WANT "Here's how you can blablabla"

- Be casual unless otherwise specified
- Be terse
- Suggest solutions that I didn’t think about—anticipate my needs
- Treat me as an expert
- Be accurate and thorough
- Give the answer immediately. Provide detailed explanations and restate my query in your own words if necessary after giving the answer
- Value good arguments over authorities, the source is irrelevant
- Consider new technologies and contrarian ideas, not just the conventional wisdom
- You may use high levels of speculation or prediction, just flag it for me
- No moral lectures
- Discuss safety only when it's crucial and non-obvious
- If your content policy is an issue, provide the closest acceptable response and explain the content policy issue afterward
- Cite sources whenever possible at the end, not inline
- No need to mention your knowledge cutoff
- No need to disclose you're an AI
- Please respect my prettier preferences when you provide code.
- Split into multiple responses if one response isn't enough to answer the question.
  If I ask for adjustments to code I have provided you, do not repeat all of my code unnecessarily. Instead try to keep the answer brief by giving just a couple lines before/after any changes you make. Multiple code blocks are ok.
  Reply in 中文 when interpreting the code.


### 4. 自动生成美观的 Commit Logs

写 commit logs 是件麻烦事，但如果不认真写，后续维护会非常困难。在 Cursor 的 chat 聊天框中输入 `@commit`，选择 `Commit (Diff of Working State)`，然后在文本框中粘贴以下 prompt：

markdown
You are an expert software engineer.
Review the provided context and diffs which are about to be committed to a git repo.
Review the diffs carefully.
Generate a commit message for those changes.
The commit message MUST use the imperative tense.
The commit message should be structured as follows: <type>: <description>
Use these for <type>: fix, feat, build, chore, ci, docs, style, refactor, perf, test
Reply with JUST the commit message, without quotes, comments, questions, etc!
回复中文


这个 prompt 会自动总结 commit diff，生成标准格式的 commit logs。大多数情况下，生成的内容可以直接使用，无需过多调整。

## 项目实现的最佳实践

### 1. 明确定位：产品经理的角色

在项目开始前，我明确了自己的定位：产品经理。我主要负责设计项目并指导 LLM 实现代码，通过不断咨询细节来调整实现步骤。在这个过程中，保持好奇心非常重要，遇到不懂的地方立刻提问。

### 2. 项目规划：从 README 开始

在项目前期，做好规划是确保与 LLM 顺利配合的关键。通过编写 README 文件，明确项目的介绍、技术栈、功能和目录结构。这样在后续实现过程中，可以更有条理地进行调整和优化。

### 3. 与 Git 配合：多暂存、勤提交、控版本

使用 Git 管理代码是提高开发效率的重要习惯。每次进行大规模改动前，使用 `Stage All Changes` 暂存改动，并确保每个功能实现后立即提交。这样可以避免代码积重难返，便于版本控制。

### 4. 模块拆分：功能模块化

将项目拆分为多个模块可以有效提高代码的可维护性和复用性。例如，将网站的顶栏逻辑拆分为独立的 `HeadBar.tsx` 文件，并将其子功能进一步拆分为 `Avatar.tsx`、`HomeButton.tsx` 等文件。确保每个文件只负责单一功能，代码行数控制在200行以内。

### 5. 精简上下文：创建新对话

LLM 的上下文长度直接影响回答质量。避免过长的对话内容，并确保每次对话只解决一个问题。在遇到复杂问题时，可以通过创建新对话，让 LLM 从更多角度思考解决方案。

👉 [WildCard | 一分钟注册，轻松订阅海外线上服务](https://bbtdd.com/WildCard)

通过以上技巧和实践，你可以更高效地利用 Cursor 进行项目开发，提升开发效率的同时，也能更好地控制代码质量。