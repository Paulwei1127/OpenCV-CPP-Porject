# OpenCV & C++ Projects Collection

這是我使用 C++ 結合 OpenCV 函式庫開發的電腦視覺與幾何運算專案合集。本 Repository 包含兩個主要專案，分別處理相機校正與多邊形重疊計算。

This repository contains a collection of computer vision and computational geometry projects developed using C++ and OpenCV.

## 專案列表 (Project List)

1. **Camera_Calibration**: 相機內參校正與影像去畸變。
2. **Image_Overlap_Calculation**: 多邊形幾何運算與重疊率計算。

---

## 開發環境與依賴 (Prerequisites)

* **Language**: C++
* **Library**: OpenCV (Open Source Computer Vision Library)
* **IDE**: Visual Studio

---

## 1. Camera_Calibration

### 簡介 (Introduction)
此專案旨在解決相機鏡頭的畸變問題。透過讀取一系列棋盤格（Chessboard）圖片，利用 OpenCV 的校正演算法計算相機的內參矩陣 (Intrinstic Matrix) 與畸變係數 (Distortion Coefficients)，並將原始影像還原為無畸變的影像。

### 檔案結構 (File Structure)
* `main.cpp`: 主程式碼，包含角點偵測、校正與去畸變邏輯。
* `case1.txt`: 索引檔，列出所有待處理的圖片路徑。
* `*.jpg`: 用於校正的棋盤格範例圖片 (e.g., 1_L.jpg)。

### 功能特點 (Features)
* **批次讀取**: 讀取 txt 列表中的多張圖片進行運算。
* **角點偵測**: 使用 `findChessboardCorners` 自動定位。
* **亞像素優化**: 使用 `cornerSubPix` 提升精確度。
* **相機校正**: 計算相機矩陣、R 向量與 T 向量。
* **影像去畸變**: 輸出 `Undistort` 後的結果對比。

---

## 2. Image_Overlap_Calculation

### 簡介 (Introduction)
此專案專注於幾何圖形的交集運算。程式會解析 JSON 格式的多邊形數據，並與預定義的測試多邊形進行重疊區域計算，最後將結果視覺化。

### 檔案結構 (File Structure)
* `Source.cpp`: 主程式碼，包含幾何演算法與 OpenCV 繪圖邏輯。
* `26.json`: 數據檔，包含多邊形 (Class A) 的頂點座標資訊。

### 功能特點 (Features)
* **JSON 解析**: 讀取並提取特定類別的多邊形座標。
* **幾何演算法**:
    * `Ptinpolygon`: 射線法判斷點位。
    * `cross`: 計算線段交點。
    * `Area`: 鞋帶公式 (Shoelace Formula) 計算面積。
* **重疊率計算**: 計算 Intersection 面積與重疊百分比 (Overlap Rate)。
* **視覺化**: 使用 OpenCV 繪製多邊形及重疊區域。