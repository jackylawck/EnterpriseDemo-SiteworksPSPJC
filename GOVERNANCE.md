# EnterpriseDemo-SiteworksPSPJC 
## Governance, Compliance & Privacy Statement (企業治理、合規與隱私聲明)

**Document Version:** 1.0.0  
**Classification:** Public (Open Source Demo)  

This document outlines the governance framework, compliance mapping, and security architecture of the `EnterpriseDemo-SiteworksPSPJC` project. It is designed to demonstrate adherence to international security and privacy standards while explicitly defining the architectural boundaries of the system.

本文件概述本專案之治理框架、合規對應與安全架構，旨在展示系統如何遵循國際資安與隱私標準，並明確界定本系統的技術與法規邊界。

---

### 1. Statement of Non-Applicability: Artificial Intelligence (AI 豁免與不適用聲明)

To ensure regulatory clarity, it is formally declared that **this system does NOT utilize, integrate, or deploy any Artificial Intelligence (AI)**, Machine Learning (ML), Large Language Models (LLM), or Automated Decision-Making (ADM) algorithms.

為確保合規清晰度，特此正式聲明：**本系統並未開發、整合或部署任何人工智慧 (AI)**、機器學習 (ML)、大型語言模型 (LLM) 或自動化決策 (ADM) 演算法。

*   **Rule-Based Architecture (規則導向架構):** The workflow is entirely built upon a deterministic State Machine and sequential logic within Microsoft Power Automate and SharePoint. All approval decisions are made explicitly by human actors (Supervisors and Managers).
    （本工作流完全建立於 M365 生態內的決定性狀態機與順序邏輯，所有核准決策均由人類（監工與經理）實質作出。）
*   **Regulatory Exemption (法規豁免):** Consequently, the following AI-specific regulations and standards are **NOT APPLICABLE** to this project:
    （因此，以下針對 AI 之特定法規與標準 **不適用** 於本專案：）
    *   **EU AI Act (歐洲人工智慧法案)**
    *   **CAC Regulations on Generative AI (中國國家網信辦《生成式人工智能服務管理暫行辦法》)**
    *   **ISO/IEC 42001:2023 (Artificial Intelligence Management System)**

---

### 2. Privacy & Data Protection (隱私保護與個資治理)

While this is a demonstration environment containing no real-world production data, the architecture is designed to comply with global privacy frameworks, assuming deployment in a live enterprise tenant.

儘管本開源專案為不含真實生產數據之示範環境，其底層架構設計完全遵循全球隱私框架（假設部署於企業真實環境中）。

*   **Compliance Mapping (合規對應):**
    *   **HK PCPD (香港《個人資料（私隱）條例》Cap. 486):** Aligns with Data Protection Principles (DPP 1-6), ensuring fair collection, strict purpose limitation (site safety validation only), and secure retention.
    *   **GDPR (General Data Protection Regulation):** Adheres to Article 5 principles (Data Minimization, Purpose Limitation, Confidentiality). 
    *   **ISO/IEC 27701:2019 (Privacy Information Management):** Implements Privacy by Design (PbD) by limiting data collection to strictly necessary operational attributes (e.g., Worker Name, Trade, Supervisor Email).
*   **Data Minimization & Sanitization (資料最小化與脫敏):** This repository has undergone strict sanitization. All emails, tenant endpoints, and organizational names are fictional placeholders (e.g., `@jumboorient.com.hk` replaced with `@companydemo.com`).

---

### 3. Information Security Architecture (資訊安全架構)

The system architecture leverages the foundational security controls of the Microsoft 365 ecosystem, demonstrating alignment with **ISO/IEC 27001:2022 (Information Security Management Systems)**.

本系統架構充分利用 Microsoft 365 生態系統之基礎安全控制，展示其與 **ISO/IEC 27001:2022 (資訊安全管理系統)** 標準之對齊。

*   **Access Control (A.8.3 - Information Access Restriction):** 
    Utilizes SharePoint's Role-Based Access Control (RBAC). The Microsoft Forms frontend operates namelessly (no-login required for frontline capture), while backend data in the SharePoint State Machine is restricted exclusively to authorized Site Supervisors and PMs.
    （運用 SharePoint 角色基礎存取控制 (RBAC)。前端 Forms 採免登入採集，後端狀態機數據庫則嚴格限制僅授權之監工與經理方可讀取。）
*   **Data Integrity & Audit Logging (A.8.10 - Information Deletion/Immutability):** 
    The State Machine design inherently prevents unauthorized status manipulation. Every approval step generates an immutable timestamp and audit trail within the M365 compliance center.
    （狀態機設計從根本上防止未經授權的狀態竄改。所有審批節點皆於 M365 合規中心生成不可篡改之時間戳記與審計軌跡。）

---

### 4. Legal Disclaimer & Limitation of Liability (法律免責聲明與責任限制)

**By using, cloning, or referencing this repository, you acknowledge and agree to the following:**

**透過使用、複製或參考本儲存庫，您知悉並同意以下條款：**

1.  **Not Legal or Compliance Advice (非法律或合規建議):** This repository is provided for educational, architectural demonstration, and academic purposes only. It does not constitute legal, regulatory, or health and safety advice.
    （本專案僅供教育、架構示範與學術交流之用，不構成任何法律、合規或職業安全健康建議。）
2.  **Fictional Data (虛構資料):** All structural names, organizational charts, sample JSON payloads, and user identities are entirely fictitious. Any resemblance to real persons or actual corporate entities is purely coincidental.
    （所有架構名稱、組織圖、範例數據與使用者身分皆為純粹虛構。如有雷同，純屬巧合。）
3.  **No Warranty ("AS IS" Basis - 按「現狀」提供):** The author(s) provide this code "AS IS" without warranty of any kind, express or implied. The author(s) shall not be liable for any claims, damages, or liabilities arising from the use of this architecture in any production environment, including but not limited to safety incidents or compliance breaches.
    （作者按「現狀」提供代碼，不附帶任何明示或暗示之擔保。對於在任何生產環境中使用此架構而產生之任何索賠、損害或責任（包括但不限於工安意外或合規違規），作者概不負責。）

---
*Created and maintained as a Best Practice Portfolio.*
