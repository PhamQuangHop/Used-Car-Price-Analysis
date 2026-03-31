# Used Car Price Prediction

Dự án phân tích thị trường xe cũ tại Đức và xây dựng mô hình Machine Learning để dự đoán giá xe dựa trên dữ liệu tin đăng từ eBay Kleinanzeigen.

## 1. Giới thiệu

Thị trường xe cũ đang phát triển mạnh, đặc biệt trên các nền tảng trực tuyến. Việc hiểu được các yếu tố ảnh hưởng đến giá bán xe giúp:

- Người bán định giá hợp lý hơn
- Người mua đánh giá đúng giá trị thực của xe
- Nhà phân tích có thêm góc nhìn về xu hướng thị trường

Dự án này kết hợp **Data Analysis**, **Data Visualization** và **Machine Learning** để phân tích dữ liệu xe cũ và xây dựng mô hình dự đoán giá.

---

## 2. Mục tiêu dự án

- Xác định các yếu tố chính ảnh hưởng đến giá xe cũ
- Xây dựng mô hình Machine Learning dự đoán giá xe với độ chính xác cao
- Trực quan hóa dữ liệu để nhận diện xu hướng thị trường
- Cung cấp các insight hỗ trợ người mua và người bán ra quyết định tốt hơn

---

## 3. Nguồn dữ liệu

- **Nguồn**: Kaggle  
- **Dataset**: *Used cars from eBay Kleinanzeigen*  
- **Link**: https://www.kaggle.com/datasets/sijovm/used-cars-data-from-ebay-kleinanzeigen/data
- **Định dạng**: CSV
- **Quy mô dữ liệu**: 371,528 dòng × 20 cột

### Một số đặc trưng chính trong dữ liệu

| Nhóm dữ liệu | Tên cột | Mô tả |
|---|---|---|
| Thông tin xe | `brand` | Hãng xe |
| Thông tin xe | `model` | Dòng xe |
| Thông tin xe | `vehicleType` | Loại xe |
| Thông tin xe | `fuelType` | Loại nhiên liệu |
| Thông tin xe | `gearbox` | Loại hộp số |
| Thông tin xe | `notRepairedDamage` | Tình trạng sửa chữa hư hỏng |
| Thông tin xe | `kilometer` | Số km đã đi |
| Thông tin xe | `powerPS` | Công suất động cơ |
| Biến mục tiêu | `price` | Giá xe (EUR) |
| Thông tin xe | `yearOfRegistration` | Năm đăng ký lần đầu |
| Thông tin xe | `monthOfRegistration` | Tháng đăng ký lần đầu |
| Feature engineering | `car_age` | Tuổi xe (được tính thêm) |
| Người bán | `seller` | Loại người bán |
| Người bán | `offerType` | Loại tin đăng |
| Metadata | `dateCreated` | Ngày tạo bản ghi |
| Metadata | `adCreated` | Ngày đăng tin |
| Metadata | `nrOfPictures` | Số lượng hình ảnh |
| Metadata | `postalCode` | Mã bưu điện |
| Metadata | `name` | Tên/mã định danh người bán |
| Metadata | `abtest` | Biến hệ thống A/B testing |

---

## 4. Nhận xét ban đầu về dữ liệu

- Dữ liệu phản ánh **giá đăng bán**, không phải giá giao dịch thực tế
- Dataset chứa cả thông tin về xe, người bán và ngữ cảnh tin đăng
- Một số cột có thể ít ảnh hưởng trực tiếp đến giá như:
  - `seller`
  - `offerType`
  - `abtest`
  - `nrOfPictures`
  - `name`
- Có tồn tại:
  - Giá trị thiếu
  - Giá trị ngoại lai
  - Dữ liệu danh mục cần chuẩn hóa
- Một số giá trị gốc bằng tiếng Đức sẽ được làm sạch và chuẩn hóa sang tiếng Anh

---

## 5. Quy trình thực hiện

### Bước 1: Thu thập dữ liệu
- Tải dữ liệu từ Kaggle
- Lưu trữ dưới dạng CSV để phục vụ phân tích bằng Python và Power BI

### Bước 2: Làm sạch và tiền xử lý dữ liệu
- Tạo thêm các biến mới như `car_age`
- Loại bỏ các cột không cần thiết
- Xử lý missing values
- Chuẩn hóa dữ liệu text
- Loại bỏ outlier bằng:
  - Quy tắc IQR
  - Điều kiện nghiệp vụ

### Bước 3: Phân tích khám phá dữ liệu (EDA)
- Phân tích đơn biến:
  - Phân bố `price`
  - Phân bố `car_age`
  - Phân bố `powerPS`
  - Top 10 nhóm phổ biến theo từng category
- Phân tích hai biến:
  - `price` với `brand`
  - `price` với `vehicleType`
  - `price` với `fuelType`
  - `price` với `gearbox`
  - `price` với `notRepairedDamage`
- Phân tích tương quan giữa các biến số
- Thống kê mô tả:
  - Mean
  - Median
  - Standard deviation

### Bước 4: Trực quan hóa dữ liệu
Xây dựng dashboard Power BI gồm 2 trang:

- **Overview**
  - Tổng quan thị trường xe cũ
- **Price Drivers Analysis**
  - Phân tích các yếu tố ảnh hưởng đến giá

### Bước 5: Xây dựng mô hình Machine Learning
Các thuật toán sử dụng:

- Linear Regression
- Random Forest Regressor

Pipeline tiền xử lý:

- `SimpleImputer`
  - `median` cho biến số
  - `most_frequent` cho biến phân loại
- `StandardScaler` cho biến số
- `OneHotEncoder` cho biến phân loại
- `ColumnTransformer` để gộp pipeline

Chia dữ liệu:

- Train/Test = **80/20**

### Bước 6: Đánh giá mô hình
Sử dụng các chỉ số:

- **MAE (Mean Absolute Error)**  
  Đo sai số tuyệt đối trung bình giữa giá dự đoán và giá thực tế

- **RMSE (Root Mean Squared Error)**  
  Đo sai số theo cùng đơn vị với giá, nhấn mạnh lỗi lớn

- **R² Score**  
  Đánh giá mức độ mô hình giải thích được biến động của dữ liệu

### Bước 7: Kết quả và đề xuất
- Tóm tắt các phát hiện chính từ EDA
- So sánh hiệu quả các mô hình
- Lưu mô hình để tái sử dụng
- Đề xuất hướng ứng dụng thực tế cho định giá xe

---

## 6. Công nghệ sử dụng

| Hạng mục | Công cụ |
|---|---|
| Lập trình & xử lý dữ liệu | Python, Pandas, Seaborn, Scikit-learn |
| Machine Learning | Linear Regression, Random Forest |
| Trực quan hóa | Microsoft Power BI |
| Môi trường làm việc | Visual Studio Code / Databricks |
| Lưu trữ dữ liệu | CSV / MySQL |

---

## 7. Kết quả kỳ vọng

- Xây dựng mô hình dự đoán giá xe cũ với độ chính xác tốt
- Tạo dashboard trực quan giúp phân tích thị trường xe cũ
- Hiểu rõ hơn các yếu tố ảnh hưởng đến giá xe
- Đặt nền tảng cho hệ thống **Auto Pricing Recommendation System** trong tương lai


