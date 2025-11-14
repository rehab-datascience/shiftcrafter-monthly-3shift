# ShiftCrafter 3-Shift — Part 3：1か月・三交代（ブラウザのみ）

**三交代制（日勤・準夜・深夜）の1か月シフト自動割当ツール**です。インストール不要、ブラウザだけで動作し、データは外部送信しません。

- デモ（GitHub Pages）：`https://<your-gh-username>.github.io/shiftcrafter-monthly-3shift/`
- ソースコード： `https://github.com/<your-gh-username>/shiftcrafter-monthly-3shift`
- ライセンス：MIT（予定）

---

## 3行まとめ
- 三交代制（**日勤・準夜・深夜**）の**1か月**シフトを自動割当する、ブラウザ完結のWebツール  
- **CSV / ICS / 検証CSV**出力対応。データはブラウザ内のみで処理、外部送信なし  
- ルール（MVP）：**準夜→翌日の日勤NG**、**同日複数シフトNG**、**深夜の週/月上限**、**希望休尊重**

---

## 使い方（最短3ステップ）
1. 上のデモURLをPCブラウザで開く  
2. 左フォームに「対象月・必要人数（各シフト共通最小）・上限（深夜のみ）・職員リスト・休み希望」を入力  
3. **「シフト自動作成」→「CSV / ICS / 検証CSV」**をダウンロード（表計算・カレンダー・検証に利用）

---

## 入力仕様（MVP）
- 必要人数：対象月の全日で共通（将来：日別プロファイルに拡張予定）  
- 休み希望：`YYYY-MM-DD 氏名` を1行1件  
- ルール：**準夜→翌日の日勤禁止**／**同日複数シフト禁止**  
- 深夜上限：**週**および（任意で）**月**をチェック

---

## 出力
- **schedule_monthly_3shift.csv**：`date,dow,need_day,need_eve,need_night,day_staff_*,eve_staff_*,night_staff_*`  
- **shift_monthly_3shift_all.ics**：Asia/Tokyo  
  - 日勤 09:00–17:00、準夜 16:30–翌00:30、深夜 00:30–09:00（※施設に合わせて `buildICS()` で変更可）  
- **validation_summary_3shift.csv**（主な列）  
  - `required_slots_filled_pct`：月間の必要枠充足率（全員同値）  
  - `off_fulfillment_pct`：個人の希望休がどれだけ叶ったか（%）  
  - `weekly_night_cap_violations / monthly_night_cap_violation`：深夜上限違反  
  - `consec_night_2plus`：**連続深夜（2連以上）**件数  
  - `day_after_evening_violation`：**準夜→翌日の日勤**が発生した件数（MVPでは0を想定）

---

## 実装メモ
- 先に**深夜→準夜→日勤**の順に充当（難しい枠から確保）。  
- ランキング：  
  - 深夜：`夜勤月回数→夜勤週回数→総割当→名前`  
  - 準夜：`準夜月回数→総割当→名前`  
  - 日勤：`総割当→夜勤月回数→準夜月回数→名前`  
- 文字コード：CSVはBOM付UTF-8、ICSはUTF-8

---

## 免責
- 本ツールは**教育・業務補助**を目的としたクライアントサイドWebアプリです。  
- **データはブラウザ内のみで処理**され、外部サーバへは送信されません。  
- 本ツールの利用によって生じた結果・損害について、作者は一切の責任を負いません。  
- 実運用時は所属施設の規程・労務基準・個人情報保護方針に従ってください。