```markdown
# 系統架構與規格說明書 (System Architecture & Specification)

## 1. 專案介紹

### 1.1 系統目的簡介
**三峽職人：手路尋蹤 (Sanxia Artisan Quest)**
本專案為一款結合地方創生與數位互動設計的單頁式 Web 應用程式 (SPA)。透過沈浸式的情境心理測驗分析使用者的「靈魂屬性」，系統會自動派發專屬的三峽在地職人職業（如木雕匠人、藍染魔法師等），並生成專屬角色卡與任務憑證。此平台旨在將純數位的互動轉化為 O2O（Online To Offline）實體導流，引導旅人進入三峽老街進行實體體驗，進而推動地方文化傳承與商圈永續發展。

* **前端技術：** HTML5, JavaScript (ES6+), Tailwind CSS, html2canvas
* **後端/雲端技術：** Serverless / Static Web Hosting (GitHub Pages)
* **資料庫/外部 API：** Web Share API, Google Maps URL Scheme, 靜態 JSON 狀態管理

---

## 2. 系統架構與範圍

### 2.1 系統架構圖
本系統採邊緣運算思維，將所有業務邏輯實作於 Client 端的無伺服器架構。以下為系統運作的架構關係圖：

```mermaid
graph TD
    classDef client fill:#0f172a,stroke:#f59e0b,stroke-width:2px,color:#fff;
    classDef cloud fill:#1e293b,stroke:#38bdf8,stroke-width:2px,color:#fff;
    classDef data fill:#334155,stroke:#10b981,stroke-width:2px,color:#fff;

    subgraph Client 層 [用戶端 展示層]
        U[使用者 Browser/Mobile]:::client --> UI[Tailwind CSS UI 渲染]:::client
        U --> Event[DOM 事件與音效觸發]:::client
    end

    subgraph Logic 層 [邊緣運算 業務邏輯層]
        UI --> Engine[測驗計分引擎 Logic Engine]:::cloud
        Event --> Engine
        Engine --> Canvas[html2canvas 渲染引擎]:::cloud
    end

    subgraph External 層 [外部數據與 API 整合]
        Canvas --> Image[輸出 PNG 角色卡]:::data
        Engine --> Config[本地靜態題庫與職業 Data]:::data
        Engine --> Map[Google Maps 導航 API]:::data
        Engine --> Share[Web Share API / Clipboard]:::data
    end
```

### 2.2 系統範圍
* **展示層 (Presentation Layer)：** 處理 RWD 響應式佈局（適配手機與桌面版）、掃描線復古濾鏡效果、環境音效（BGM）播放控制、以及動畫轉場。
* **業務邏輯層 (Business Logic Layer)：** 掌管 SPA 狀態管理（`step`, `scores`, `finalResult`）、MBTI 類型的計分權重演算法、同分隨機抽選機制、以及 HTML 到 Canvas 的 DOM 解析轉換。
* **數據存取/整合層 (Data Access/Integration Layer)：** 管理題庫陣列與職業屬性常數（Config Object），並負責橋接手機端原生的分享功能（Navigator.share）及外部地圖深度連結。

### 2.3 交付項目
1. `index.html` (核心應用程式檔案，含全部樣式與腳本)
2. `assets/images/` (職人角色背景圖資源)
3. `assets/audio/` (五大職業專屬環境音軌)
4. `README.md` (本系統規格說明書)

---

## 3. 業務功能需求

| 需求編號 | 功能名稱 | 參與者 | 功能描述 | 業務邏輯 / 備註 |
| :--- | :--- | :--- | :--- | :--- |
| **F01** | 情境互動測驗 | 一般訪客 | 提供 5 道情境選擇題，每次點擊自動進入下一題，並記錄使用者偏好的屬性。 | 採用內存陣列記錄分數 (`wood`, `metal`, `ferm`, `dye`, `tea`)，題庫更換不需重啟伺服器。 |
| **F02** | 靈魂屬性演算 | 系統 | 當第 5 題回答完畢，系統比對各屬性得分，產生專屬職人角色。 | 包含防呆與同分處理機制，當多屬性同分時，採用 `Math.random()` 隨機分發確保多樣性。 |
| **F03** | 動態角色卡生成 | 一般訪客 | 將使用者的測驗結果、雷達圖數據與專屬說明，封裝成高畫質圖片供下載。 | 使用 `html2canvas` 進行 DOM 截圖，支援 CORS 跨域圖片載入與錯誤佔位圖 (`onerror`) 處理。 |
| **F04** | O2O 任務導航 | 一般訪客 | 提供專屬任務憑證，並按鈕一鍵跳轉至 Google Maps 的對應實體店家地圖。 | URL Scheme 組合：`http://googleusercontent.com/maps.google.com/{店家編號}`。 |
| **F05** | 社群招募擴散 | 一般訪客 | 產生「尋找互補隊友」的專屬連結，方便用戶在社群發佈招募貼文。 | 優先呼叫行動裝置原生 `navigator.share`；若無支援則降級使用 Clipboard API 並跳出 Toast 提示。 |

---

## 4. 非業務功能需求

### 4.1 安全性要求 (Security)
* **去識別化運作：** 系統全程於 Client-side 運算，無需使用者註冊登入，不收集任何 PII (個人可識別資訊)，無個資外洩風險。
* **資源防護：** 載入外部資源時具備跨域限制防護 (`crossorigin="anonymous"`)，避免 Canvas 污染導致截圖失敗。

### 4.2 系統效能 (Performance)
* **輕量化設計：** 單一 HTML 檔案交付，降低 HTTP 請求次數；使用 Tailwind CSS CDN 確保樣式渲染效率。
* **音訊延遲載入：** 環境音效 (`Audio`) 需等待使用者首次互動 (`unlockAudio`) 後才進行解鎖與緩存，符合現代瀏覽器的自動播放規範並節省頻寬。

### 4.3 可用性與準確性 (Availability & Reliability)
* **RWD & 跨平台相容：** 包含 `viewport-fit=cover` 與針對行動裝置優化的觸控區域配置，防止畫面超出邊界。
* **無縫降級機制 (Graceful Degradation)：** 分享機制及圖片載入皆具備備援機制 (Fallback)，確保舊版瀏覽器或網路不穩時，系統仍能正常運作。

---

## 5. 系統介面設計 (API 規格)

由於系統採用無伺服器前端架構，以下定義核心組件之間的資料拋接規格（內部 Pseudo-API）與 URL 傳參規格。

### 5.1 社群擴散入口路由規格
* **Endpoint:** `GET /?need={partner_type}`
* **Description:** 當使用者點擊朋友分享的連結進入平台時，系統會解析 URL 參數以客製化歡迎畫面。
* **Payload Example (JSON Representation):**
```json
{
  "query_parameters": {
    "need": "dye"
  },
  "expected_behavior": "系統將顯示：『你的朋友正在尋找【藍染水魔法師】的隊友！』之客製化 UI"
}
```

### 5.2 職人屬性資料結構 (Data Schema)
* **Endpoint:** `Internal State: results[finalResult]`
* **Description:** 系統結算時取用的靜態資料庫結構，用於動態渲染角色卡片與任務內容。
* **Response Example (JSON):**
```json
{
  "class": "木雕匠人",
  "title": "Lv.1 沉穩的木雕匠人",
  "attr": "專注 / 雕琢 / 棟樑",
  "stats": {
    "str": 60,
    "agi": 40,
    "int": 85,
    "focus": 99
  },
  "description": "你擁有極高的專注力，在細節中尋找完美。三峽的木雕職人與你有著同樣的頻率...",
  "action": "接取任務：前往木雕工作室獲得 5 分鐘微體驗",
  "mapUrl": "[https://www.google.com/maps/search/?api=1&query=三峽老街+木雕](https://www.google.com/maps/search/?api=1&query=三峽老街+木雕)",
  "partner": "dye"
}
```

---

## 6. 專案安裝與部署

### 6.1 前置需求
* 支援 HTML5 之現代瀏覽器（Chrome, Safari, iOS Safari, Edge）。
* 本專案為靜態網頁，無需設定 Node.js 或 Database 環境。

### 6.2 部署步驟
1. **檔案備妥：** 將 `index.html` 以及 `assets/` 目錄放置於同一根目錄下。
2. **本地測試：** * 由於 `html2canvas` 在處理本地圖片時可能會遇到 CORS 限制，建議使用本地伺服器進行測試。
   * 可使用 Python：`python -m http.server 8000` 或 VS Code 的 Live Server 擴充套件。
3. **雲端部署：**
   * 將檔案 Commit 至 GitHub 儲存庫。
   * 於儲存庫設定 (Settings) 中開啟 **GitHub Pages**，指向主分支的 `root` 目錄即可完成自動發佈。
