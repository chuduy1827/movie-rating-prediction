# Movie Rating Prediction

Dự án xây dựng mô hình Machine Learning để dự đoán rating phim từ dataset **MovieLens 20M** (20 triệu đánh giá).

## Phân công nhiệm vụ

| Thành viên | Nhiệm vụ | Kỹ năng sử dụng |
|------------|----------|------------------|
| **Duy** | Đọc dữ liệu, làm sạch, Baseline model | Python, Pandas, LaTeX |
| **Phúc** | EDA, Feature Selection, vẽ biểu đồ | Pandas, Matplotlib, Seaborn |
| **Tuân** | Tiền xử lý, Linear Regression | Scikit-learn, Pandas |
| **Thịnh** | Random Forest/XGBoost, đánh giá, viết báo cáo | Scikit-learn, Matplotlib |

## Kết quả chính

| Mô hình | MAE | RMSE | R² | Người thực hiện |
|---|---:|---:|---:|---|
| Baseline (Mean) | 0.8405 | 1.0522 | - | Duy |
| Linear Regression | 0.8221 | 1.0315 | 0.0374 | Tuân |
| Random Forest | ? | ? | ? | Thịnh |

> 📌 *> Linear Regression đã hoàn thành và cho kết quả tốt hơn Baseline. Random Forest sẽ được cập nhật sau.*

## Cấu trúc dự án

movie-rating-prediction/
│
├── notebooks/
│   └── baseline.ipynb          # Code của Duy (đọc dữ liệu, làm sạch, baseline)
│
├── slides/
│   └── presentation.tex        # Slide thuyết trình LaTeX Beamer
│
├── data/                       # Dữ liệu MovieLens (đã .gitignore)
│   ├── ratings.csv
│   ├── movies.csv
│   └── tags.csv
│
├── baseline_results.csv        # Kết quả baseline model
├── requirements.txt            # Thư viện cần cài đặt
├── .gitignore                  # Bỏ qua file lớn và data
└── README.md                   # Mô tả dự án

## Công nghệ sử dụng

| Công nghệ | Phiên bản | Mục đích |
|-----------|-----------|----------|
| Python | 3.9+ | Ngôn ngữ lập trình |
| Pandas | - | Xử lý và phân tích dữ liệu |
| NumPy | - | Tính toán số học |
| Matplotlib/Seaborn | - | Vẽ biểu đồ, EDA |
| Scikit-learn | - | Linear Regression, Random Forest, metrics |
| Jupyter | - | Môi trường chạy code |
| LaTeX (Beamer) | - | Tạo slide thuyết trình |

## Cách chạy code

### 1. Clone repository

git clone https://github.com/chuduy1827/movie-rating-prediction.git
cd movie-rating-prediction

### 2. Tạo môi trường ảo (khuyến nghị)

# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate

### 3. Cài đặt thư viện

pip install -r requirements.txt

### 4. Tải dữ liệu MovieLens 20M

- Truy cập: https://grouplens.org/datasets/movielens/20m/
- Tải file `ml-20m.zip`
- Giải nén và copy 3 file (`ratings.csv`, `movies.csv`, `tags.csv`) vào thư mục `data/`

### 5. Chạy Jupyter Notebook

jupyter notebook notebooks/baseline.ipynb
Để chạy phần Linear Regression của Tuân:
```bash
jupyter notebook linear_regression_tuan.ipynb
linear_regression_results_tuan.csv
Chạy lần lượt các cell từ trên xuống dưới.

## Chi tiết Baseline Model (Duy)

### Các bước thực hiện

| Bước | Mô tả |
|------|-------|
| 1 | Đọc 3 file CSV (ratings, movies, tags) |
| 2 | Merge theo `movieId` |
| 3 | Xử lý missing values (genres → 'Unknown') |
| 4 | Xóa duplicate (nếu có) |
| 5 | Chuẩn hóa kiểu dữ liệu (timestamp → datetime) |
| 6 | Xây dựng baseline: dự đoán = mean rating |
| 7 | Tính MAE, RMSE |

### Công thức Baseline

\[
\hat{y}_i = \bar{y} = \frac{1}{n}\sum_{i=1}^{n} y_i
\]

### Kết quả (trên 1 triệu dòng test)


==================================================
KẾT QUẢ BASELINE MODEL
==================================================
MAE:  0.8405
RMSE: 1.0522
Mean Rating: 3.5268

## Ghi chú

- Dữ liệu gốc MovieLens 20M (~500MB) **không được upload lên GitHub** do dung lượng lớn
- File `cleaned_data.csv` (76MB) vượt quá giới hạn GitHub (50MB) nên được ignore
- Để chạy full dữ liệu, cần tải từ link gốc và đặt vào thư mục `data/`

## Chi tiết Linear Regression Model (Tuân)

### Các bước thực hiện

| Bước | Mô tả |
|---|---|
| 1 | Đọc dữ liệu `ratings.csv` và `movies.csv` |
| 2 | Merge dữ liệu theo `movieId` |
| 3 | Xử lý missing values trong cột `genres` |
| 4 | Xóa duplicate rows |
| 5 | Chuyển đổi `timestamp` sang định dạng datetime |
| 6 | Tạo thêm các đặc trưng thời gian: `year`, `month`, `dayofweek` |
| 7 | One-hot encoding cột `genres` |
| 8 | Chia dữ liệu thành train/test set |
| 9 | Huấn luyện mô hình Linear Regression |
| 10 | Đánh giá mô hình bằng MAE, RMSE và R² |

### Kết quả

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Baseline (Mean) | 0.8405 | 1.0522 | - |
| Linear Regression | 0.8221 | 1.0315 | 0.0374 |

### Nhận xét

Mô hình Linear Regression cho kết quả tốt hơn mô hình Baseline. MAE giảm từ `0.8405` xuống `0.8221`, trong khi RMSE giảm từ `1.0522` xuống `1.0315`. Điều này cho thấy mô hình Linear Regression đã cải thiện độ chính xác dự đoán so với việc chỉ dự đoán bằng giá trị rating trung bình.

Tuy nhiên, chỉ số R² = `0.0374` vẫn còn thấp, cho thấy các đặc trưng hiện tại mới chỉ giải thích được một phần nhỏ sự biến thiên của rating. Điều này là hợp lý vì rating phim phụ thuộc nhiều vào sở thích cá nhân của người dùng và cần thêm các đặc trưng mạnh hơn để cải thiện mô hình.

## Cập nhật

| Ngày | Nội dung |
|---|---|
| 20/04/2026 | Hoàn thành Baseline Model (MAE=0.8405, RMSE=1.0522) |
| 20/04/2026 | Tạo repository GitHub, upload code và slide |
| 21/04/2026 | Hoàn thành Linear Regression Model bởi Tuân (MAE=0.8221, RMSE=1.0315, R²=0.0374) |
| 21/04/2026 | Linear Regression cho kết quả tốt hơn Baseline |
## Liên kết

- **GitHub Repository:** https://github.com/chuduy1827/movie-rating-prediction
- **Dataset MovieLens 20M:** https://grouplens.org/datasets/movielens/20m/


**Liên hệ:** chud53701@gmail.com

*Project hoàn thành trong khuôn khổ môn học Data Analysis with Python.*
