---
name: Bug report
about: Create a report to help us improve
title: ''
labels: ''
assignees: ''

---

name: 🐞 バグ報告 / Bug report
description: 期待どおりに動かない・エラーが出る
labels: [bug]
body:
  - type: textarea
    id: summary
    attributes:
      label: 概要 / Summary (EN)
      description: 何が起きたかを1〜2行で。Please summarize in 1–2 lines.
      placeholder: 例）深夜→翌早の禁止が効かず割当が発生
    validations:
      required: true
  - type: textarea
    id: steps
    attributes:
      label: 再現手順 / Steps to Reproduce
      description: 再現手順を番号付きで。Numbered steps, please.
      placeholder: |
        1. 対象月と必要人数を入力
        2. 職員/希望休を貼り付け
        3. [シフト自動作成] をクリック
        4. ...
    validations:
      required: true
  - type: input
    id: version
    attributes:
      label: バージョン/コミット / Version or Commit
      placeholder: v0.3.x or commit hash
  - type: textarea
    id: expected
    attributes:
      label: 期待結果 / Expected
  - type: textarea
    id: actual
    attributes:
      label: 実際の結果 / Actual
  - type: textarea
    id: attachments
    attributes:
      label: 参考データ / Attachments
      description: サンプルCSV/入力テキスト/スクリーンショット等
