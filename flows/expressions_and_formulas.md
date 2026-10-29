# Expressions, Formulas & OData Queries (進階語法與查詢)

本文件紀錄 Power Automate 工作流中使用的核心表達式 (Expressions) 與 OData 查詢語法，確保系統運作的動態性與低維護成本。

## 1. OData Filter Query (動態路由查詢)
為了實現「主數據驅動 (Master Data Driven)」，避免在流程中硬編碼 (Hardcode) 監工的電郵地址，系統使用 `Get items` 動作並配合 OData 查詢。

* **Action:** `取得多個項目 (Get items)` - SharePoint
* **Target List:** `Demo-Supervisor-Directory`
* **Filter Query:**
  ```odata
  Title eq '@{triggerOutputs()?['body/SupervisorName']}'

```

* **邏輯說明:** 擷取 Forms 中工頭選擇的「監工姓名」，精準比對名冊清單中的 `Title` 欄位，從而動態提取該監工的 Email。

## 2. Markdown 超連結組合 (Dynamic Links in Approvals)

在 Approvals 卡片的 `Details` 欄位中，使用 Markdown 語法將 SharePoint 項目連結包裝成易於點擊的按鈕。

* **語法結構:**
```markdown
👉 [點此開啟上傳現場相片](@{outputs('Create_item')?['body/{Link}']})

```


* **邏輯說明:** 將 `Create item` 動態生成的原生 `{Link}` 變數，嵌入 Markdown 的 `[顯示文字](URL)` 結構中，提升高管的 UI/UX 體驗。

## 3. Array Unwrapping (迴圈自動解包)

在微軟 Power Automate 的底層邏輯中，`Get items`（即使只返回一筆資料）與 `Wait for an approval` 的回應皆為陣列 (Array) 格式。

* **架構處理:**
系統自動生成的 `For each` 迴圈是安全且必要的。它確保在提取 `SupervisorEmail` (監工電郵) 以及審批者的 `Responses Comments` (回應註解) 時，資料類型能被正確解析並寫入後續的 `Update item` 與 `Send an email (V2)` 動作中，不會產生型別衝突 (Type Mismatch)。

```
