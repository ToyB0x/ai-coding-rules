# Documentation System for People and LLMs to Work Together

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
