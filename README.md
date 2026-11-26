# 試算表專案追蹤同步

使用員工分表協作更新資料，再將欄位變更同步回主資料表。

## 技術

Google Sheets、Google Apps Script（JavaScript）。

## 同步流程

1. 主控腳本建立員工工作表。
2. 安裝型 `onEdit` trigger 記錄欄位更新時間。
3. 共用 Library 依欄位最後更新時間判定最新值。
4. 主控腳本將變更同步回主資料表。
