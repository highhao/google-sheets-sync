# 試算表專案追蹤同步

讓多人透過各自工作表更新資料，並依欄位更新時間同步回主資料表。

## 同步流程

```mermaid
flowchart TB
    A[主控腳本建立員工分表] --> B[員工編輯欄位]
    B --> C[onEdit trigger 記錄欄位時間]
    C --> D[主控流程比較欄位最新時間]
    D --> E[更新主資料表]
```

## 架構心智圖

```mermaid
mindmap
  root((試算表同步))
    主控腳本
      建立員工分表
      執行同步
    員工工作表
      分開編輯範圍
      欄位資料
    onEdit trigger
      記錄欄位更新時間
    共用 Library
      欄位級最新時間優先
    主資料表
      接收同步結果
```

## 設計與技術

- **設計重點：** 以欄位級更新時間判定較新的值，避免整列覆寫造成不同欄位更新互相覆蓋。
- **技術：** Google Sheets、Google Apps Script（JavaScript）、安裝型 `onEdit` trigger。
