# SharePoint Database Schema (狀態機與數據庫結構)

本專案採用 Microsoft SharePoint Online 作為關聯式數據庫與狀態機 (State Machine) 引擎。透過分離「主數據」與「業務單據」，確保系統可擴充性與權限隔離。

## 1. 監工名冊主數據庫 (Master Data)
* **List Name:** `Demo-Supervisor-Directory`
* **Purpose:** 用於 Power Automate 動態路由 (Dynamic Routing)。當前線在 Forms 選擇監工姓名時，系統透過 OData Filter Query 查詢此表獲取對應的電郵地址，避免將電郵硬編碼 (Hardcode) 於流程中。

| Column Name (顯示名稱) | Internal Name (內部名稱) | Data Type | Description |
| :--- | :--- | :--- | :--- |
| **Title (監工姓名)** | `Title` | Single line of text | 必須與 Forms 下拉選單的選項完全一致 |
| **Email (監工電郵)** | `SupervisorEmail` | Person or Group / Text | 用於派發 Approvals 審批卡片 |
| **Region (負責區域)** | `Region` | Choice | (Optional) 用於進階的分區路由邏輯 |
| **Status (狀態)** | `ActiveStatus` | Boolean (Yes/No) | `Yes` 代表在職，`No` 代表離職停用 |

---

## 2. 開工自檢表記錄 (State Machine Database)
* **List Name:** `Demo-Site-Inspection-Records`
* **Purpose:** 作為流程的核心狀態機，承載 Forms 寫入的自檢數據、附件連結以及雙層審批的決策備註。

### A. 系統狀態欄位 (State Control)
| Column Name | Data Type | Permitted Values (狀態流轉限制) |
| :--- | :--- | :--- |
| **審批狀態 (Approval Status)** | Choice | `待監工審核` ➔ `待經理審核` ➔ `已批准/已歸檔` <br> *(例外阻斷狀態：`監工已拒絕`, `經理已拒絕`)* |

### B. 業務數據欄位 (Business Data)
| Column Name | Data Type | Source | Description |
| :--- | :--- | :--- | :--- |
| **Title (工單編號)** | `Title` | Power Automate | 自動生成 (e.g., `PSPJC-20261029-001`) |
| **地盤名稱 (Site Name)** | Single line of text | Forms | 地盤/項目名稱 |
| **施工位置 (Location)** | Single line of text | Forms | 具體施工樓層或區域 |
| **13項自檢結果總匯** | Multiple lines of text | Forms | 匯總 13 項安全檢查之 JSON 或純文本字串 |
| **不合格整改描述** | Multiple lines of text | Forms | 前線填寫之整改說明 |
| **檢查工友姓名** | Single line of text | Forms | 實名電子聲明 |
| **確認工頭姓名** | Single line of text | Forms | 實名電子聲明 |

### C. 審計與決策欄位 (Audit & Decision)
| Column Name | Data Type | Source | Description |
| :--- | :--- | :--- | :--- |
| **監工附加條款與備註** | Multiple lines of text | Approvals | 監工於卡片輸入的巡查意見 |
| **經理審批備註** | Multiple lines of text | Approvals | 經理終審時的放行或否決指令 |
