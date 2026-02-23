Dự Đoán Giá Xăng RON-95 Tại Việt Nam
Giới Thiệu
Dự án này áp dụng các mô hình học máy và học sâu để dự đoán giá xăng RON-95 tại Việt Nam dựa trên dữ liệu chuỗi thời gian hàng tuần. Chúng tôi tích hợp các biến ngoại sinh như giá dầu thô thế giới (Brent, WTI), chỉ số giá tiêu dùng (CPI) và tỷ giá hối đoái USD/VND. Các mô hình được thử nghiệm bao gồm Linear Regression, SVR, ARIMAX, XGBoost, RNN, LSTM và GRU. Kết quả cho thấy Linear Regression là mô hình hiệu quả nhất với MAPE 1.70% và RMSE 465, phù hợp với đặc trưng dữ liệu ngắn, gián đoạn và chịu ảnh hưởng lớn từ cơ chế điều hành giá. Các mô hình phức tạp hơn không mang lại cải thiện đáng kể do hạn chế của dữ liệu.
Dự án được thực hiện trong khuôn khổ đồ án Phân Tích Dữ Liệu Kinh Doanh, Trường Đại Học Công Nghệ Thông Tin, Đại Học Quốc Gia TP. HCM, học kỳ HK1 năm học 2025-2026.
Thành Viên Nhóm

Trương Thanh Quang (MSSV: 23521295)
Đào Bảo Phúc (MSSV: 23521192)
Ngô Nhật Quân (MSSV: 23521258)
Huỳnh Trần Anh Thú (MSSV: 23521535)

Giảng viên hướng dẫn: ThS. Dương Phi Long.
Yêu Cầu Cài Đặt
Dự án sử dụng Python 3.12 với các thư viện sau. Cài đặt qua pip install -r requirements.txt:

numpy
pandas
scikit-learn
xgboost
statsmodels (cho ARIMAX)
tensorflow (cho RNN, LSTM, GRU)
matplotlib (cho visualize)

Môi trường khuyến nghị: Jupyter Notebook hoặc Google Colab.
Dữ Liệu
Dữ liệu được thu thập từ:

Giá xăng RON-95: PVOIL/Petrolimex (tần suất tuần, từ 2018 đến 11/2025, tổng 378 điểm dữ liệu).
Biến ngoại sinh: Brent/WTI (USD/thùng), USD/VND, CPI (chuẩn hóa theo tuần).

Tiền xử lý: Nội suy CPI hàng tháng, lag features, phần trăm thay đổi, moving average, spread và interaction terms. Dữ liệu chia 70% train, 15% validation, 15% test.
File dữ liệu: data/ron95_data.csv (giả định trong repo).
Các Mô Hình Và Kết Quả
Chúng tôi đánh giá các mô hình dựa trên MAE, RMSE, R², MAPE và Directional Accuracy (DA). Linear Regression vượt trội nhất, chứng tỏ dữ liệu có quan hệ tuyến tính yếu và không cần mô hình phức tạp.





































































Mô HìnhMAERMSER²MAPE (%)DA (%)Linear Regression340.00465.000.42101.7037.00SVR345.60484.900.36941.7137.04XGBoost439.00572.000.12242.1744.40RNN389.80580.160.11741.9441.20LSTM494.55628.72-0.02152.4740.29GRU486.69651.55-0.09712.4342.00ARIMAX1326.301692.50-6.61606.4710.71
Dự đoán 2 tuần tiếp theo bằng Linear Regression: Tuần +1: 20,182 VND/lít; Tuần +2: 20,112 VND/lít.
Code các mô hình nằm trong thư mục models/, ví dụ linear_regression.py.
Hướng Dẫn Sử Dụng

Clone repo: git clone https://github.com/yourusername/ron95-price-prediction.git
Cài đặt dependencies: pip install -r requirements.txt
Chạy notebook chính: jupyter notebook main.ipynb (load data, train models, evaluate).
Dự đoán: Chạy python predict.py --model linear --weeks 2 để dự báo.

Kết Luận
Linear Regression là lựa chọn tối ưu do dữ liệu ngắn, nhiễu chính sách và tín hiệu yếu. Các mô hình học sâu thất bại vì thiếu chuỗi dài hạn. Hướng phát triển: Sử dụng dữ liệu tần suất cao hơn, thêm biến chính sách, mở rộng chuỗi quan sát để cải thiện dự báo.
Tài Liệu Tham Khảo
Xem phần References trong báo cáo PDF (docs/Nhom16-BaoCao.pdf).
License
MIT License.
