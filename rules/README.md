# 規則庫 | Rules Database

**規則庫是系統的憲法。** 本目錄存放內政部「住宅租賃定型化契約應記載及不得記載事項」的結構化版本。

---

## 架構

```
rules/
├── README.md (本文件)
├── metadata.json (版本、更新日期、來源鏈接)
├── applicable-items.json (應記載事項)
├── prohibited-items.json (不得記載事項)
└── severity-standards.md (嚴重度分級標準)
```

---

## 版本管理

每個規則庫版本對應一個官方規範快照：

| 版本 | 日期 | 官方來源 | 說明 |
|------|------|---------|------|
| v1.0 | 2026-06-11 | 內政部官網 (待補鏈接) | 初始化結構化入庫 |

---

## 快照 + 哨兵模式

- **快照** (`applicable-items.json`, `prohibited-items.json`)
  - 凍結版本的結構化規範
  - 評測報告中引用的唯一真實來源
  - 版本號不變 = 評測結果可重現

- **哨兵** (自動化 Agent，每月執行一次)
  - 定期檢測官方規範更新
  - 檢測到變動 → 自動開 GitHub Issue
  - 人工審核 + 合併 → 版本號 +1

---

## 條目結構範例

```json
{
  "item_id": "應01",
  "original_text": "[官方條文原文]",
  "plain_language": "[租客視角的白話解釋]",
  "common_violations": [
    {
      "violation": "[常見違規樣態]",
      "example": "[實測案例]"
    }
  ],
  "severity": "high|medium|low",
  "severity_reason": "[嚴重度判定依據]",
  "keywords": ["關鍵詞1", "關鍵詞2"],
  "last_updated": "2026-06-11",
  "notes": "[補充說明]"
}
```

---

## 貢獻規則修正

發現規則庫中的錯誤或遺漏？

1. 開啟 GitHub Issue，附上：
   - 官方文件連結
   - 現行規則中的問題
   - 建議修正
2. 核心團隊驗證
3. 合併至下一版本

---

## 可 Fork 的資產

移植到其他國家時，只需替換本目錄：
1. 下載當地官方規範
2. 用相同的 `metadata.json`、`severity-standards.md` 結構
3. 更新 `applicable-items.json` 和 `prohibited-items.json`

三大鐵律和評測標準保持不變。

---

*版本 v1.0 | 2026-06-11*
