# Documentation System for People and LLMs to Work Together

## STEP FLOW

The documentation system usage flow consists of the following 5 steps:

<details>
<summary>1. <b>Create Documentation Guidelines</b>: Define the ideal state declaratively.</summary>

- Understanding best practices
- Understanding current project characteristics
- Creating documentation guidelines
- Reviewing existing guidelines for improvement
</details>

<details>
<summary>2. <b>Gap Analysis</b>: Analyze the gap between the established guidelines and the current state.</summary>

- Understanding the documentation guidelines
- Understanding the current project state
- Analyzing the gaps between them
</details>

<details>
<summary>3. <b>Implementation Plan Creation</b>: Plan the steps to fill the identified gaps.</summary>

- Understanding the gaps
- Planning improvement steps
- Prioritizing and implementing in stages
</details>

<details>
<summary>4. <b>Execute Implementation Plan</b>: Implement improvements based on the plan.</summary>

- Understanding the implementation plan
- Understanding the current project state
- Executing improvements
</details>

<details>
<summary>5. <b>Regular Review and Updates</b>: Update or reapply guidelines according to project changes.</summary>

- Understanding current guidelines
- Improving and adjusting guidelines
- Repeating from step 2 as needed
</details>

```mermaid
graph TD
    A[1. Create Documentation Guidelines] --> B[2. Gap Analysis]
    B --> C[3. Implementation Plan Creation]
    C --> D[4. Execute Implementation Plan]
    D --> E[5. Regular Review and Updates]
    E -->|as needed| B
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style B fill:#bbf,stroke:#333,stroke-width:1px
    style C fill:#bbf,stroke:#333,stroke-width:1px
    style D fill:#bbf,stroke:#333,stroke-width:1px
    style E fill:#bbf,stroke:#333,stroke-width:1px
```

## How to Use

Use the following commands with Cline or Roo Code:

```bash
# Step 1: Create Documentation Guidelines
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md Create documentation guidelines following Step 1

# Step 2: Gap Analysis
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md Perform gap analysis between current state and guidelines following Step 2

# Step 3: Implementation Plan
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md Create an implementation plan for documentation guidelines following Step 3

# Step 4: Execute Implementation Plan
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md Execute the implementation plan following Step 4

# Step 5: Regular Review and Updates
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md Perform regular review and updates of documentation guidelines following Step 5
```

## Notes

### Considerations on Using Memory Bank

<details>
<summary>Show/Hide Details</summary>

- Memory Bank consumes tokens, so its usage should be evaluated based on project requirements
- Regardless of Memory Bank usage, large document collections can exceed 100k tokens, making incremental access important
- Personal observations on Memory Bank files:
  - activeContext.md: Regular conversation context may be sufficient
  - decisionLog.md: Team decisions should be properly committed to repositories
  - productContext.md: Product overviews should be committed with human consensus rather than auto-generated
  - progress.md: Team progress should be documented in organized repositories
  - systemPatterns.md: System structures should be documented in organized repositories
- Semi-automated reflection documents might be useful when accumulated insights can be committed to system interactions
  - A potentially better approach: include response history in LLM commits and use CI to automatically generate weekly retrospectives and improvement PRs
</details>
