# Movie Rating Prediction

Dự án xây dựng mô hình Machine Learning để dự đoán rating phim từ dataset **MovieLens 20M** (20 triệu đánh giá).

## Kết quả chính

| Mô hình | MAE | RMSE | R² | Người thực hiện |
|---------|-----|------|-----|-----------------|
| **Baseline (Mean)** | 0.8405 | 1.0522 | - | Duy |
| Linear Regression | ? | ? | ? | Tuân |
| Random Forest | ? | ? | ? | Thịnh |

> 📌 *Kết quả Linear Regression và Random Forest sẽ được cập nhật sau khi hoàn thành.*

## Phân công nhiệm vụ

| Thành viên | Nhiệm vụ | Kỹ năng sử dụng |
|------------|----------|------------------|
| **Duy** | Đọc dữ liệu, làm sạch, Baseline model | Python, Pandas, LaTeX |
| **Phúc** | EDA, Feature Selection, vẽ biểu đồ | Pandas, Matplotlib, Seaborn |
| **Tuân** | Tiền xử lý, Linear Regression | Scikit-learn, Pandas |
| **Thịnh** | Random Forest/XGBoost, đánh giá, viết báo cáo | Scikit-learn, Matplotlib |

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

## Cập nhật

| Ngày | Nội dung |
|------|----------|
| 20/04/2026 | Hoàn thành Baseline Model (MAE=0.8405, RMSE=1.0522) |
| 20/04/2026 | Tạo repository GitHub, upload code và slide |
| 21/04/2026 | Chờ cập nhật kết quả từ các thành viên khác |

## Liên kết

- **GitHub Repository:** https://github.com/chuduy1827/movie-rating-prediction
- **Dataset MovieLens 20M:** https://grouplens.org/datasets/movielens/20m/

## Thành viên nhóm

| STT | Họ tên | Nhiệm vụ |
|-----|--------|----------|
| 1 | Duy | Đọc dữ liệu + Làm sạch + Baseline + Slide |
| 2 | Phúc | EDA + Feature Selection + Vẽ biểu đồ |
| 3 | Tuân | Tiền xử lý + Linear Regression |
| 4 | Thịnh | Random Forest + Đánh giá + Báo cáo + Slide |


**Liên hệ:** chud53701@gmail.com

*Project hoàn thành trong khuôn khổ môn học Data Analysis with Python.*
