# Frontline Safety Questionnaire (前線安全自檢表單架構)

為達成「極簡採集」與「零門檻」，前端採用 **Microsoft Forms (免登入公開連結)**，並結合 QR Code 張貼於工地現場。

## 1. 基本資料區 (Basic Information)
* **地盤名稱** (Text - Required)
* **施工位置** (Text - Required)
* **工作內容** (Text - Required)
* **檢查日期** (Date - Required)

## 2. 核心高危安全自檢 (13-Point Safety Checklist)
*所有選項統一為單選題 (Choice)：`合格 (Pass)` / `不合格 (Fail)` / `不適用 (N/A)`*

1. **工作許可証** (Hot Work / Confined Space Permit)
2. **電力工具檢查標籤** (Electrical Tools Tag)
3. **電工具配件** (Hand Tools Condition)
4. **梯具** (Ladders - EN Code Standards)
5. **滅火筒** (Fire Extinguishers)
6. **防火設備** (Fire Protection Blankets)
7. **圍封** (Warning Tape / Barricades)
8. **合適的個人防護裝備** (PPE)
9. **離地/高空工作** (Working at Height / Platforms)
10. **吊運工作** (Lifting Operations / Walkie Talkie)
11. **密閉空間工作** (Confined Space Gas Test)
12. **風煤工作** (Welding / Flashback Arrestor)
13. **機械操作** (Machinery Operations / Certificates)

* **不合格項目描述及整改說明** (Long Text - Required if any item fails)

## 3. 電子簽認與聲明 (Electronic Signatures & Declarations)
*設計理念：在免登入環境下，透過雙人實名輸入落實責任制。*

* **檢查工友姓名** (Text - Required)
* **檢查工友工種** (Text - Required)
* **確認工頭姓名** (Text - Required)
* **確認工頭職位** (Text - Required)
* **請選擇負責監工** (Drop-down - Required) ➔ *連動 SharePoint 進行動態路由*
