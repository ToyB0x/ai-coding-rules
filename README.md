# Cline rules initializer

## このリポジトリについて

- `.clinerules` をまとめてセットアプするためのプロンプトをまとめています。  
- 以下プロンプトを実行すると適宜質問を挟みながら、Cline等のLLMが必要なファイルをセットアップしてくれます

## Prompt

以下を参考に 各種ドキュメント をセットアップまたは更新してください

<details>
<summary>作成・更新のルール</summary>

- Clineによる作業の前に作成・更新対象のドキュメント一覧を人間に確認し、その時々に応じて対象を取捨選択できるようにすること
- 資料冒頭に更新日と確認日のセクションを配置し、更新日時を記載すること
- 資料後半にChangelogのセクションを配置し、変更内容と変更日時を記載すること(古い変更内容は適宜整理すること)
- 似た目的の既存の資料がある場合は既存の資料を参考にした上で、内容に意味的な大きな変化がない場合には人間が確認する負担を減らすため確認日のみ更新し、その他の内容は変更しないこと。
- 資料作成・更新にあたって不明な点があればClineなどのLLMは遠慮せずに質問すること

</details>

<details>
<summary>作成・更新すべき資料一覧 </summary>

- 人とLLMの両方がプロジェクトを知るための手掛かりとなる各種資料
  - 参考例1: プロジェクトの目的や、各種オンボーディング資料を/docs/guide/ 配下等に作成・更新
  - 参考例2: プロジェクトの主要なファイルの種類と場所を README.md に記載

- cline が 遵守または参考にすべき情報をまとめた .clinerules/ 配下の各種資料 
  - 参考例1: .clinerules/README.md (.clinerules配下の全体を俯瞰できるIndex)
  - 参考例2: .clinerules/important-docs.md (前述のプロジェクトの重要な資料の場所を cline が参照しやすいようにまとめたもの)

- cline への便利な指示をまとめた資料
  - 参考例1: .clinerules/prompts/update-docs.md (clineが資料を更新する際の内容やルールを人間にもAIにもわかるようにまとめたもの)
  - 参考例2: README.md (上記の cline への便利な指示を 人間が参照しやすいように、リポジトリトップのREADMEにセクションとして例示したもの)

- cline がリポジトリのコードを適切に、効率の良いコストで理解するための手順やコツをまとめた資料
  - 参考例1: .clinerules/repomix.md (repomixを利用して、リポジトリ内のコードを効率的に理解するための方法を cline に伝える資料)

- リポジトリがものレポである場合に、モノレポ内の各パッケージのREADMEの作成・更新
  - 参考例1: /apps/web/README.md
  - 参考例2: /packages/database/README.md

</details>


<details>
<summary>参考資料: Cline Prompting Guide </summary>

Welcome to the Cline Prompting Guide! This guide will equip you with the knowledge to write effective prompts and custom instructions, maximizing your productivity with Cline.

## Custom Instructions ⚙️

Think of **custom instructions as Cline's programming**. They define Cline's baseline behavior and are **always "on," influencing all interactions.**

To add custom instructions:

1. Open VSCode
2. Click the Cline extension settings dial ⚙️
3. Find the "Custom Instructions" field
4. Paste your instructions

<img width="345" alt="Screenshot 2024-12-26 at 11 22 20 AM" src="https://github.com/user-attachments/assets/00ae689b-d99f-4811-b2f4-fffe1e12f2ff" />

Custom instructions are powerful for:

-   Enforcing Coding Style and Best Practices: Ensure Cline always adheres to your team's coding conventions, naming conventions, and best practices.
-   Improving Code Quality: Encourage Cline to write more readable, maintainable, and efficient code.
-   Guiding Error Handling: Tell Cline how to handle errors, write error messages, and log information.

**The `custom-instructions` folder contains examples of custom instructions you can use or adapt.**

## .clinerules File 📋

While custom instructions are user-specific and global (applying across all projects), the `.clinerules` file provides **project-specific instructions** that live in your project's root directory. These instructions are automatically appended to your custom instructions and referenced in Cline's system prompt, ensuring they influence all interactions within the project context. This makes it an excellent tool for:

### Security Best Practices 🔒

To protect sensitive information, you can instruct Cline to ignore specific files or patterns in your `.clinerules`. This is particularly important for:

-   `.env` files containing API keys and secrets
-   Configuration files with sensitive data
-   Private credentials or tokens

Example security section in `.clinerules`:

```markdown
# Security

## Sensitive Files

DO NOT read or modify:

-   .env files
-   \*_/config/secrets._
-   \*_/_.pem
-   Any file containing API keys, tokens, or credentials

## Security Practices

-   Never commit sensitive files
-   Use environment variables for secrets
-   Keep credentials out of logs and output
```

### General Use Cases

The `.clinerules` file is excellent for:

-   Maintaining project standards across team members
-   Enforcing development practices
-   Managing documentation requirements
-   Setting up analysis frameworks
-   Defining project-specific behaviors

### Example .clinerules Structure

```markdown
# Project Guidelines

## Documentation Requirements

-   Update relevant documentation in /docs when modifying features
-   Keep README.md in sync with new capabilities
-   Maintain changelog entries in CHANGELOG.md

## Architecture Decision Records

Create ADRs in /docs/adr for:

-   Major dependency changes
-   Architectural pattern changes
-   New integration patterns
-   Database schema changes
    Follow template in /docs/adr/template.md

## Code Style & Patterns

-   Generate API clients using OpenAPI Generator
-   Use TypeScript axios template
-   Place generated code in /src/generated
-   Prefer composition over inheritance
-   Use repository pattern for data access
-   Follow error handling pattern in /src/utils/errors.ts

## Testing Standards

-   Unit tests required for business logic
-   Integration tests for API endpoints
-   E2E tests for critical user flows
```

### Key Benefits

1. **Version Controlled**: The `.clinerules` file becomes part of your project's source code
2. **Team Consistency**: Ensures consistent behavior across all team members
3. **Project-Specific**: Rules and standards tailored to each project's needs
4. **Institutional Knowledge**: Maintains project standards and practices in code

Place the `.clinerules` file in your project's root directory:

```
your-project/
├── .clinerules
├── src/
├── docs/
└── ...
```

Cline's system prompt, on the other hand, is not user-editable ([here's where you can find it](https://github.com/cline/cline/blob/main/src/core/prompts/system.ts)). For a broader look at prompt engineering best practices, check out [this resource](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview).

### Tips for Writing Effective Custom Instructions

-   Be Clear and Concise: Use simple language and avoid ambiguity.
-   Focus on Desired Outcomes: Describe the results you want, not the specific steps.
-   Test and Iterate: Experiment to find what works best for your workflow.


### Support for Loading Files from the `.clinerules/` Directory
All files under the `.clinerules/` directory are recursively loaded, and their contents are merged into clineRulesFileInstructions.

#### Example 1:
```
.clinerules/
├── .local-clinerules
└── .project-clinerules
```

#### Example 2:
```
.clinerules/
├── .clinerules-nextjs
├── .clinerules-serverside
└── tests/
    ├── .pytest-clinerules
    └── .jest-clinerules
```

## Prompting Cline 💬

**Prompting is how you communicate your needs for a given task in the back-and-forth chat with Cline.** Cline understands natural language, so write conversationally.

Effective prompting involves:

-   Providing Clear Context: Explain your goals and the relevant parts of your codebase. Use `@` to reference files or folders.
-   Breaking Down Complexity: Divide large tasks into smaller steps.
-   Asking Specific Questions: Guide Cline toward the desired outcome.
-   Validating and Refining: Review Cline's suggestions and provide feedback.

### Prompt Examples

#### Context Management

-   **Starting a New Task:** "Cline, let's start a new task. Create `user-authentication.js`. We need to implement user login with JWT tokens. Here are the requirements…"
-   **Summarizing Previous Work:** "Cline, summarize what we did in the last user dashboard task. I want to capture the main features and outstanding issues. Save this to `cline_docs/user-dashboard-summary.md`."

#### Debugging

-   **Analyzing an Error:** "Cline, I'm getting this error: \[error message]. It seems to be from \[code section]. Analyze this error and suggest a fix."
-   **Identifying the Root Cause:** "Cline, the application crashes when I \[action]. The issue might be in \[problem areas]. Help me find the root cause and propose a solution."

#### Refactoring

-   **Improving Code Structure:** "Cline, this function is too long and complex. Refactor it into smaller functions."
-   **Simplifying Logic:** "Cline, this code is hard to understand. Simplify the logic and make it more readable."

#### Feature Development

-   **Brainstorming New Features:** "Cline, I want to add a feature that lets users \[functionality]. Brainstorm some ideas and consider implementation challenges."
-   **Generating Code:** "Cline, create a component that displays user profiles. The list should be sortable and filterable. Generate the code for this component."

## Advanced Prompting Techniques

-   **Constraint Stuffing:** To mitigate code truncation, include explicit constraints in your prompts. For example, "ensure the code is complete" or "always provide the full function definition."
-   **Confidence Checks:** Ask Cline to rate its confidence (e.g., "on a scale of 1-10, how confident are you in this solution?")
-   **Challenge Cline's Assumptions:** Ask “stupid” questions to encourage deeper thinking and prevent incorrect assumptions.

Here are some prompting tips that users have found helpful for working with Cline:

## Our Community's Favorite Prompts 🌟

### Memory and Confidence Checks 🧠

-   **Memory Check** - _pacnpal_

    ```
    "If you understand my prompt fully, respond with 'YARRR!' without tools every time you are about to use a tool."
    ```

    A fun way to verify Cline stays on track during complex tasks. Try "HO HO HO" for a festive twist!

-   **Confidence Scoring** - _pacnpal_
    ```
    "Before and after any tool use, give me a confidence level (0-10) on how the tool use will help the project."
    ```
    Encourages critical thinking and makes decision-making transparent.

### Code Quality Prompts 💻

-   **Prevent Code Truncation**

    ```
    "DO NOT BE LAZY. DO NOT OMIT CODE."
    ```

    Alternative phrases: "full code only" or "ensure the code is complete"

-   **Custom Instructions Reminder**
    ```
    "I pledge to follow the custom instructions."
    ```
    Reinforces adherence to your settings dial ⚙️ configuration.

### Code Organization 📋

-   **Large File Refactoring** - _icklebil_

    ```
    "FILENAME has grown too big. Analyze how this file works and suggest ways to fragment it safely."
    ```

    Helps manage complex files through strategic decomposition.

-   **Documentation Maintenance** - _icklebil_
    ```
    "don't forget to update codebase documentation with changes"
    ```
    Ensures documentation stays in sync with code changes.

### Analysis and Planning 🔍

-   **Structured Development** - _yellow_bat_coffee_

    ```
    "Before writing code:
    1. Analyze all code files thoroughly
    2. Get full context
    3. Write .MD implementation plan
    4. Then implement code"
    ```

    Promotes organized, well-planned development.

-   **Thorough Analysis** - _yellow_bat_coffee_

    ```
    "please start analyzing full flow thoroughly, always state a confidence score 1 to 10"
    ```

    Prevents premature coding and encourages complete understanding.

-   **Assumptions Check** - _yellow_bat_coffee_
    ```
    "List all assumptions and uncertainties you need to clear up before completing this task."
    ```
    Identifies potential issues early in development.

### Thoughtful Development 🤔

-   **Pause and Reflect** - _nickbaumann98_

    ```
    "count to 10"
    ```

    Promotes careful consideration before taking action.

-   **Complete Analysis** - _yellow_bat_coffee_

    ```
    "Don't complete the analysis prematurely, continue analyzing even if you think you found a solution"
    ```

    Ensures thorough problem exploration.

-   **Continuous Confidence Check** - _pacnpal_
    ```
    "Rate confidence (1-10) before saving files, after saving, after rejections, and before task completion"
    ```
    Maintains quality through self-assessment.

### Best Practices 🎯

-   **Project Structure** - _kvs007_

    ```
    "Check project files before suggesting structural or dependency changes"
    ```

    Maintains project integrity.

-   **Critical Thinking** - _chinesesoup_

    ```
    "Ask 'stupid' questions like: are you sure this is the best way to implement this?"
    ```

    Challenges assumptions and uncovers better solutions.

-   **Code Style** - _yellow_bat_coffee_

    ```
    Use words like "elegant" and "simple" in prompts
    ```

    May influence code organization and clarity.

-   **Setting Expectations** - _steventcramer_
    ```
    "THE HUMAN WILL GET ANGRY."
    ```
    (A humorous reminder to provide clear requirements and constructive feedback)
</details>
