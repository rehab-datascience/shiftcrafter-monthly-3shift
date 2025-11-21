---
name: Custom issue template
about: Describe this issue template's purpose here.
title: ''
labels: ''
assignees: ''

---

name: 🤝 カスタム相談 / Custom request
description: 設定や仕様の個別カスタマイズ相談（要件ヒアリング）
title: "[Consulting]: "
labels: ["consulting"]
body:
  - type: markdown
    attributes:
      value: |
        カスタムのご相談をありがとうございます。個人情報は送らないでください。可能なら匿名のダミーデータをご用意ください。
  - type: input
    id: contact
    attributes:
      label: 連絡先（任意）
      placeholder: 例) メール or XのDM
  - type: textarea
    id: context
    attributes:
      label: 背景と課題
      placeholder: 例) 病棟Aで三交代。Night明けのDay禁止を厳密にしたい 等
    validations:
      required: true
  - type: textarea
    id: requirements
    attributes:
      label: 必須要件（必ず満たしたい条件）
      placeholder: 箇条書きで3〜5点
  - type: textarea
    id: dataset
    attributes:
      label: データ形式（添付予定/共有方法）
      placeholder: 例) CSV（匿名化済みサンプルを後ほど添付）
