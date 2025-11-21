---
name: Feature request
about: Suggest an idea for this project
title: ''
labels: ''
assignees: ''

---

name: ✨ 機能要望 / Feature request
description: 追加したい機能や改善案
labels: [enhancement]
body:
  - type: textarea
    id: summary
    attributes:
      label: 要望の要点 / Summary (EN)
      placeholder: 例）準夜→深夜の最小インターバルを可変に
    validations:
      required: true
  - type: dropdown
    id: shift_mode
    attributes:
      label: 対象シフト / Target shift
      options:
        - 全体 / Global
        - 早 / Early
        - 日 / Day
        - 深 / Night
        - 準夜 / Evening
    validations:
      required: true
  - type: textarea
    id: rationale
    attributes:
      label: 背景・理由 / Rationale
  - type: textarea
    id: spec
    attributes:
      label: 簡易仕様 / Minimal spec
      description: 入力/出力/制約・UIの想定など
  - type: textarea
    id: acceptance
    attributes:
      label: 受け入れ基準 / Acceptance Criteria
      placeholder: 条件付きのシナリオで動作を確認できる基準
