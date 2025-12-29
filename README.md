# Rembg Tool - 圖片去背工具

使用 Flask 開發的網頁小工具，使用 AI 模型，提供圖片自動去背與物件偵測功能。

![rembg_demo](https://github.com/user-attachments/assets/e212a903-624a-4ca8-a56b-7db2f7d21bce)


## 主要功能

- **圖片去背 (Background Removal)**: 使用 `rembg` (U^2-Net) 自動移除圖片背景。
- **物件偵測 (Object Detection)**: 使用 `ultralytics` YOLO11 模型，提供物件偵測 API。
- **互動式使用者介面**:
  - 支援拖曳上傳 (Drag & Drop)。
  - 提供 "Before & After" 圖片對比滑桿，方便檢視去背效果。
  - 當無圖片時提供範例快速測試。
  - 根據圖片中的物件產生對應的 emoji 視覺特效。
- **RESTful API**: 提供後端 API 供整合使用。

## 使用工具

- **Backend**: Python, Flask
- **AI Models**: 
  - [rembg](https://github.com/danielgatis/rembg) (去背)
  - [Ultralytics YOLO](https://github.com/ultralytics/ultralytics) (用於 emoji 特效物件偵測 - `yolo11n.pt`)
- **Frontend**: HTML5, Bootstrap 5, jQuery, CSS3

## 快速開始

### 1. 安裝環境

建議使用 Python 3.9 環境。

```bash
# 複製專案
git clone https://github.com/Leo890728/rembg_tool.git
cd rembg_tool

# 建議建立虛擬環境 (Optional)
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

# 安裝套件
pip install -r requirements.txt
```

### 2. 下載模型 (自動)

首次執行時，`rembg` 和 `ultralytics` 會自動下載所需的權重檔案 (`u2net` 和 `yolo11n.pt`)。

### 3. 啟動

```bash
python app.py
```

啟動後，瀏覽器打開 [http://localhost:5000](http://localhost:5000) 即可使用。

## API 使用說明

除了網頁介面，也可以直接調用 API。

### 去背 API (`POST /removebg`)

- **URL**: `/removebg`
- **Method**: `POST`
- **Form Data**: `file` (圖片檔案, 支援 .jpg, .png)
- **Response**: 回傳去背後的 PNG 圖片

### 物件偵測 API (`POST /detect`)

- **URL**: `/detect`
- **Method**: `POST`
- **Form Data**: `file` (圖片檔案, 支援 .jpg, .png)
- **Response**: JSON 格式的偵測結果

## 專案結構

```
rembg_tool/
├── app.py              # Flask 主程式
├── requirements.txt    # 專案依賴套件
├── yolo11n.pt          # YOLO 模型權重
├── templates/
│   └── index.html      # 前端頁面
└── static/
    ├── css/            # 樣式表
    ├── js/             # 前端 JavaScript
    └── img/            # 圖片資源
```
