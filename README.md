# **Used Car Price Analysis - eBay Kleinanzeigen (Germany)**
📌 Giới thiệu dự án (Project Overview)
Dự án tập trung vào việc phân tích các yếu tố ảnh hưởng đến giá xe ô tô cũ trên nền tảng eBay Kleinanzeigen tại Đức. Mục tiêu chính là xây dựng mô hình học máy (Machine Learning) để dự đoán giá xe với độ chính xác cao và trực quan hóa các xu hướng thị trường thông qua Dashboard.
•	Bối cảnh: Thị trường xe cũ trực tuyến phát triển mạnh, việc hiểu rõ các yếu tố ảnh hưởng giúp người bán định giá hợp lý và người mua đánh giá đúng giá trị xe.
•	Mục tiêu:
o	Xác định các yếu tố then chốt tác động đến giá xe.
o	Xây dựng mô hình Machine Learning dự đoán giá xe với độ chính xác cao cho thị trường phổ thông.
o	Trực quan hóa dữ liệu để nắm bắt xu hướng thị trường.
o	Đưa ra các đề xuất dựa trên dữ liệu (data-driven insights) hỗ trợ ra quyết định.
📊 Nguồn dữ liệu (Data Source)
•	Nguồn: Kaggle - bộ dữ liệu “Used cars from eBay Kleinanzeigen”.
•	Định dạng: CSV.
•	Quy mô: 371.528 dòng và 20 cột dữ liệu.
•	Đặc điểm lưu ý: Dữ liệu là các tin đăng (listings), không phải giá bán thực tế. Các giá trị danh mục gốc bằng tiếng Đức sẽ được chuẩn hóa và dịch sang tiếng Anh.
🛠 Công cụ và Công nghệ (Tools & Technologies)
•	Ngôn ngữ & Thư viện: Python (Pandas, Seaborn, Scikit-learn).
•	Machine Learning: Linear Regression, Random Forest Regressor.
•	Trực quan hóa: Microsoft Power BI.
•	Môi trường làm việc: Visual Studio Code / Databricks.
•	Lưu trữ: CSV / MySQL.
🚀 Quy trình thực hiện (Workflow)
1.	Làm sạch & Tiền xử lý: Loại bỏ cột không cần thiết, xử lý giá trị thiếu (Missing values), và loại bỏ ngoại lai (outliers) bằng quy tắc IQR.
2.	Phân tích EDA: Thực hiện phân tích đơn biến, đa biến và ma trận tương quan để xác định các yếu tố ảnh hưởng mạnh nhất đến giá như brand, vehicleType, fuelType, gearbox.
3.	Trực quan hóa (Power BI): Thiết kế Dashboard gồm trang Tổng quan thị trường và trang Phân tích yếu tố ảnh hưởng giá.
4.	Xây dựng mô hình ML: Sử dụng Pipeline xử lý dữ liệu (SimpleImputer, StandardScaler, OneHotEncoder) và chia tập dữ liệu Train/Test theo tỉ lệ 80/20.
5.	Đánh giá: Đo lường hiệu quả bằng các chỉ số MAE, RMSE và $R^2$ Score.
📈 Kết quả kỳ vọng (Expected Outcomes)
•	Mô hình dự đoán giá xe cũ chính xác, hỗ trợ định giá nhanh.
•	Dashboard Power BI giúp trực quan hóa thị trường và các yếu tố ảnh hưởng giá.
•	Hiểu rõ hành vi thị trường xe cũ tại Đức.
•	Nền tảng để phát triển hệ thống tư vấn giá tự động (Auto Pricing Recommendation System).
________________________________________
Tác giả: Pham Quang Hop
Chuyên ngành: Data Processing - FPT Polytechnic

