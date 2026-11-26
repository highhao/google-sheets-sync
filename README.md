# 試算表專案追蹤同步

**技術：** Google Sheets、Google Apps Script（JavaScript）。

## 處理的問題

員工在各自工作表更新專案資料後，需要同步回主控資料。流程記錄欄位級最後更新時間，供主控流程判斷同步值。

## 元件與職責

- **員工工作表範本**：建立一致欄位與分表結構。
- **共用 LWW Library**：由安裝型 `onEdit` trigger 呼叫，記錄欄位編輯時間。
- **模板載入腳本**：連結共用函式庫並建立 trigger。
- **主控中心**：維護人員清單、建立員工分表並同步資料。

![建立與同步流程](docs/assets/workflow.svg)

## 後續優化方向（設計建議）

- 明確定義欄位時間戳相同時的決勝規則，並記錄同步來源與結果。
- 使用批次讀寫並加入失敗重試與配額監控，控制 Apps Script 執行時間及 API 呼叫量。

English: A Google Sheets and Apps Script workflow for field-level change tracking and synchronization.
