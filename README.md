# Documentation system for people and LLMs to work together

## 利用方法

Cline または Roo Code に以下を指示して下さい

```bash
# Step1: ドキュメンテーションガイドラインの策定
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md の内容を参考に Step1 のドキュメンテーションガイドラインを策定して

# Step2: 現状とのギャップ分析
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md の内容を参考に Step2 のドキュメンテーションガイドラインの現状とのギャップ分析を行って

# Step3: ドキュメンテーションガイドラインの適用計画の策定
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md の内容を参考に Step3 のドキュメンテーションガイドラインの適用計画を策定して

# Step4: ドキュメンテーションガイドラインの適用計画の実行
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md の内容を参考に Step4 のドキュメンテーションガイドラインの適用計画を実行して

# Step5: 定期的な検査と更新
@https://raw.githubusercontent.com/ToyB0x/ai-coding-rules/refs/heads/main/Guideline.md の内容を参考に Step5 のドキュメンテーションガイドラインの定期的な検査と更新を行って
```

## Memo

### Memory Bank を利用すべきかどうか

<details>
<summary>詳細を表示/非表示</summary>

- Memory Bank自体もトークンを消費するので、Memory Bankを利用するかどうかはプロジェクトの状況に応じて判断が必要そう。
- Memory Bank自体の利用有無に関わらず、大規模なドキュメント群だと、全部読み込ませると10 万トークンを超えることがあるので、段階的にアクセスできることが大切である(Memory Bankはこれを半自動でやってくれるだけ)
- 私個人は以下が疑問だったので試しはしたが、あまり積極的には利用していない
  - activeContext.md    普通に会話のContextで良いのでは
  - decisionLog.md      個人で使う分には会話のContextで良いし、人も理解すべきチームの判断は整理された場所にCommitすべき
  - productContext.md   人もLLMもプロダクトの概要を理解するために、普通にCommitすべきでは(半分使い捨て、自動生成に頼るよりも、しっかり人間合意のもとで作るべきでは)
  - progress.md         個人で使う分には会話のContextで良いし、人も理解すべきチームの進捗は整理された場所にCommitすべき
  - systemPatterns.md   個人で使う分には会話のContextで良いし、人も理解すべき構造は整理された場所にCommitすべき
- 一方で振り返りと改善.md みたいなもので個人レベルの振り返りを半自動でためておき、ある程度のまとまりで知見がたまったらsystem interactionにコミットするのは良いかもしれない(改善の自動化)
  - ただ、これもLLMによる commit に commit の応答Historyを含ませた上で、週次でCIで commit 履歴から自動で振り返りさせて、提案PRを自動で作るとかの方が個人的には良い気がする
</details>
