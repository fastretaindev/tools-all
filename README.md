# Urmart Tools 

Urmart 內部使用的靜態小工具集合，目前包含兩個純前端 CSV 處理工具，可直接在瀏覽器開啟使用，無需後端服務。

線上入口網頁：[tools.urmart.com](https://tools.urmart.com)

## 專案內容

### 1. 工具首頁

- 路徑：`/index.html`
- 用途：提供各工具的統一入口頁

### 2. Packing List / Commercial Invoice 產生工具

- 路徑：`/packing-inv/index.html`
- 用途：匯入 Catalog CSV 與訂單 CSV，產出 Excel 檔案
- 支援模式：
  - Packing List
  - Commercial Invoice
- 技術：
  - Bootstrap 5
  - PapaParse
  - SheetJS

此工具會在前端完成：

- 解析 Catalog CSV，建立商品條碼對照資料
- 預覽訂單 CSV 內容
- 計算箱數、淨重、毛重、金額等欄位
- 下載 `.xlsx` 檔案

補充說明請見 `packing-inv/README.md`。

### 3. 財務 AccountAnalysis 轉換工具

- 路徑：`/account-analysis/index.html`
- 用途：將財務匯出的 CSV 重新整理為固定欄位順序，再下載為新的 CSV
- 支援模式：
  - 原版本 11 欄
  - 包含外幣 15 欄
- 技術：
  - Tailwind CSS CDN
  - PapaParse
  - canvas-confetti

此工具會在前端完成：

- 上傳並解析 CSV
- 根據模式抽取指定欄位
- 保留字串格式輸出
- 下載轉換後的 `converted.csv`

## 專案結構

```text
tools-all/
├── CNAME
├── README.md
├── index.html
├── account-analysis/
│   └── index.html
└── packing-inv/
    ├── Copy of Product Catalog.csv
    ├── README.md
    └── index.html
```

## 使用方式

### 本機直接開啟

1. 進入專案根目錄。
2. 用瀏覽器開啟 `index.html`。
3. 從首頁選擇要使用的工具。

這個專案目前沒有 build step，也不需要安裝 Node.js 或其他後端環境。

### 使用靜態伺服器

如果你希望用本機網址測試，也可以啟動任一簡單靜態伺服器，例如：

```bash
python3 -m http.server 8000
```

然後開啟：

```text
http://localhost:8000
```

## 部署說明

本專案是靜態網站結構，適合部署到 GitHub Pages 或其他靜態託管平台。

目前有使用以下 CDN 資源：

- Bootstrap
- Tailwind CSS
- PapaParse
- SheetJS
- canvas-confetti

因此部署環境需要可連外存取上述 CDN。

## 注意事項

- 兩個工具目前都以 CSV 為主要輸入格式。
- `packing-inv` 會輸出 Excel 檔案 `.xlsx`。
- `account-analysis` 會輸出重新整理後的 `.csv`。
- 若使用者上傳的是 Excel 檔案，`account-analysis` 目前不支援直接轉換，需先另存成 CSV。

## 維護建議

- 若新增工具，請同步更新根目錄 `index.html` 的入口按鈕。
- 若新增子工具資料夾，建議在各自目錄下維護獨立 README。
- 若變更路徑名稱，請同步檢查首頁連結與部署設定。
