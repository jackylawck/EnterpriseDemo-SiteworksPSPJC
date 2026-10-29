# Approvals Markdown Templates (審批卡片範本)

本專案在 Power Automate 的 `Start and wait for an approval` 動作中，採用高度結構化的 Markdown 語法，確保管理層在 Outlook 與 Teams 收到卡片時能「一目了然、迅速決策」。

## 1. 監工初審卡片 (Supervisor First-Tier Review)

**Title:** `【開工自檢初審】@{triggerOutputs()?['body/SiteName']} - @{triggerOutputs()?['body/Location']}`

**Details (Markdown):**
```text
前線已提交開工自檢表，請監工至現場巡查覆核：

• 地盤名稱：@{triggerOutputs()?['body/SiteName']}
• 施工位置：@{triggerOutputs()?['body/Location']}
• 工作內容：@{triggerOutputs()?['body/JobDescription']}
• 檢查工友：@{triggerOutputs()?['body/WorkerName']}（@{triggerOutputs()?['body/WorkerTrade']}）
• 確認工頭：@{triggerOutputs()?['body/ForemanName']}（@{triggerOutputs()?['body/ForemanTitle']}）
• 不合格整改：@{triggerOutputs()?['body/RectificationRemarks']}

--------------------------------------------------
📷【現場相片上傳與補充條款】
請點擊下方清單連結，拍照上傳現場照片或填寫附加條款：
👉 [點此開啟上傳現場相片](@{outputs('Create_item')?['body/{Link}']})
--------------------------------------------------
確認無誤後，請於本卡片點擊 Approve 批准開工。

```

## 2. 經理終審卡片 (Manager Final-Tier Approval)

**Title:** `【開工終審批准】@{triggerOutputs()?['body/SiteName']} - @{triggerOutputs()?['body/Location']}`

**Details (Markdown):**

```text
監工已完成現場初審並確認合格，請經理進行開工終審：

• 地盤名稱：@{triggerOutputs()?['body/SiteName']}
• 施工位置：@{triggerOutputs()?['body/Location']}
• 負責監工：@{outputs('Get_Supervisor_Data')?['body/Title']}
• 監工巡查意見：@{outputs('Supervisor_Approval')?['body/ResponsesComments']}

📷 現場相片與自檢詳情：
👉 [點此檢視現場相片與完整記錄](@{outputs('Create_item')?['body/{Link}']})

確認符合開工條件後，請點擊 Approve 簽發開工許可。

```
