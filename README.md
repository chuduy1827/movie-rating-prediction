# Movie Rating Prediction

Dự án xây dựng mô hình Machine Learning để dự đoán rating (điểm đánh giá) của người dùng cho phim, dựa trên bộ dữ liệu MovieLens.

## Thành viên nhóm

| Thành viên | Nhiệm vụ chính |
|------------|----------------|
| **Duy** | Đọc dữ liệu, làm sạch, xây dựng Baseline |
| **B** | EDA, Feature Selection, vẽ biểu đồ |
| **C** | Tiền xử lý, Linear Regression |
| **D** | Random Forest/XGBoost, đánh giá, viết báo cáo |

## Công nghệ sử dụng

- Python 3.9+
- pandas - xử lý dữ liệu
- numpy - tính toán số học
- matplotlib & seaborn - vẽ biểu đồ
- scikit-learn - xây dựng mô hình

## Cấu trúc thư mục

movie-rating-prediction/
├── data/                  # chứa file CSV (đã được .gitignore)
├── notebooks/             # chứa các Jupyter Notebook
│   ├── duy/
│   ├── b/
│   ├── c/
│   └── d/
├── slides/                # chứa file thuyết trình PPTX
├── report/                # chứa báo cáo PDF cuối cùng
└── README.md              # file hướng dẫn này

##  Cách cài đặt và chạy

### 1. Clone repository

```bash
git clone https://github.com/ten_cua_ban/movie-rating-prediction.git
cd movie-rating-prediction
```

### 2. Tạo môi trường ảo (khuyến nghị)

# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate

### 3. Cài đặt thư viện

pip install pandas numpy matplotlib seaborn scikit-learn

(Nếu sử dụng XGBoost, cài thêm: `pip install xgboost`)

### 4. Tải dữ liệu

Tải các file sau từ [MovieLens](https://grouplens.org/datasets/movielens/) (bộ small hoặc 100k) và đặt vào thư mục `data/`:

- `ratings.csv`
- `movies.csv`
- `tags.csv`

> **Lưu ý:** Thư mục `data/` đã được thêm vào `.gitignore` để không push dữ liệu lên GitHub.

### 5. Chạy các notebook theo thứ tự

| Thứ tự | Notebook | Người thực hiện | Nội dung |
|--------|----------|-----------------|----------|
| 1 | `01_duy_data_cleaning.ipynb` | Duy | Đọc dữ liệu, làm sạch, baseline |
| 2 | `02_b_eda.ipynb` | B | EDA, vẽ biểu đồ, chọn feature |
| 3 | `03_c_preprocessing.ipynb` | C | Tiền xử lý dữ liệu |
| 4 | `04_c_linear_regression.ipynb` | C | Linear Regression |
| 5 | `05_d_random_forest.ipynb` | D | Random Forest, đánh giá |

## Kết quả dự kiến

- So sánh 3 mô hình: Baseline, Linear Regression, Random Forest
- Đánh giá qua các chỉ số: MAE, RMSE, R²
- Biểu đồ sai số (residuals) và scatter plot dự đoán vs thực tế

## Quy tắc làm việc nhóm

### Git workflow

1. Mỗi người làm việc trên **branch riêng** của mình
2. Không commit trực tiếp vào branch `main`
3. Sau khi hoàn thành, tạo **Pull Request** để review code
4. Người được phân công review sẽ kiểm tra và merge

### Branch naming

- `duy`
- `b`
- `c`
- `d`

### Commit message

Viết commit message rõ ràng, ví dụ:
- `git commit -m "done: data cleaning and baseline"`
- `git commit -m "add: EDA histogram and boxplot"`

### Review code chéo

| Người viết | Người review |
|-------------|---------------|
| Duy | D |
| B | C |
| C | B |
| D | tổng thể |

## Tiến độ dự kiến

| Ngày | Nhiệm vụ | Người thực hiện |
|------|----------|------------------|
| 1 | Kick-off, tạo repo, chia task | Cả nhóm |
| 2 | Làm sạch dữ liệu + Baseline | Duy |
| 3 | EDA + Feature Selection | B |
| 4 | Tiền xử lý | C |
| 5 | Linear Regression | C |
| 6 | Random Forest + Họp review | D + cả nhóm |
| 7 | Tổng hợp báo cáo + slide cuối | D + cả nhóm |
