# Báo cáo: Hiệu suất Chiến dịch Marketing

## Mô tả Dataset:
Dataset về Hiệu suất Chiến dịch Marketing cung cấp những thông tin quan trọng về hiệu quả của các chiến dịch marketing khác nhau. Dataset này ghi lại các chỉ số hiệu suất, đối tượng mục tiêu, thời gian, kênh sử dụng, và các yếu tố thiết yếu khác góp phần vào thành công của các chiến dịch. Với 200.000 dòng dữ liệu độc nhất trải dài trong hai năm, dataset này mang lại cái nhìn toàn diện về hiệu suất chiến dịch trên nhiều công ty và phân khúc khách hàng.

## Các cột trong Dataset:
1. **Company**: Công ty chịu trách nhiệm thực hiện chiến dịch, bao gồm các thương hiệu giả định.
2. **Campaign_Type**: Loại chiến dịch được sử dụng, bao gồm email, mạng xã hội, influencer, quảng cáo hiển thị, hoặc tìm kiếm.
4. **Duration**: Thời gian diễn ra chiến dịch, tính bằng ngày.
5. **Channels_Used**: Các kênh được sử dụng để quảng bá chiến dịch, bao gồm email, nền tảng mạng xã hội, YouTube, website, hoặc Google Ads.
6. **Conversion_Rate**: Tỷ lệ chuyển đổi từ lượt xem hoặc lượt tiếp cận thành hành động mong muốn, thể hiện hiệu quả của chiến dịch.
7. **Acquisition_Cost**: Chi phí mà công ty phải bỏ ra để thu hút khách hàng, được trình bày dưới dạng giá trị tiền tệ.
8. **ROI**: Lợi tức đầu tư, thể hiện mức độ lợi nhuận và thành công của chiến dịch.
9. **Location**: Địa điểm địa lý nơi chiến dịch được thực hiện, bao gồm các thành phố lớn như New York, Los Angeles, Chicago, Houston, hoặc Miami.
10. **Language**: Ngôn ngữ được sử dụng trong nội dung chiến dịch, bao gồm tiếng Anh, Tây Ban Nha, Pháp, Đức, hoặc Trung Quốc.
11. **Clicks**: Số lượt nhấp chuột mà chiến dịch tạo ra, thể hiện mức độ tương tác của người dùng.
12. **Impressions**: Tổng số lần chiến dịch được hiển thị hoặc xem bởi đối tượng mục tiêu (Số lần nội dung quảng cáo được hiển thị trên màn hình của người dùng, mặc kệ người dùng có click hay không)
13. **Engagement_Score**: Điểm số từ 1 đến 10 đo lường mức độ tương tác mà chiến dịch tạo ra.
14. **Customer_Segment**: Phân khúc khách hàng hoặc nhóm đối tượng mà chiến dịch hướng đến, ví dụ: người yêu công nghệ, tín đồ thời trang, người quan tâm đến sức khỏe, người yêu ẩm thực, hoặc người thích hoạt động ngoài trời.
15. **Date**: Ngày diễn ra chiến dịch, cung cấp góc nhìn theo thời gian để phân tích xu hướng và mô hình.
16. **Sex**: Giới tính của đối tượng ta tiếp cận chiến dịch
17. **Age_Group**: Nhóm tuổi đối tượng ta tiếp cận

## Phạm vi ứng dụng:
Bằng cách sử dụng dataset này, các nhà tiếp thị và nhà phân tích dữ liệu có thể khám phá những thông tin giá trị về hiệu suất chiến dịch, sở thích của đối tượng mục tiêu, hiệu quả của kênh, và ROI. Dataset này là một nguồn tài nguyên quý giá cho nghiên cứu thị trường, tối ưu hóa chiến dịch, và ra quyết định dựa trên dữ liệu, giúp doanh nghiệp cải thiện chiến lược marketing và thúc đẩy tăng trưởng có mục


## Tổng hợp công việc đã thực hiện - Marketing Campaign Analysis

### 1. Giai đoạn Chuẩn bị và Làm sạch dữ liệu (Data Preparation)
- ✅ Import các thư viện cần thiết (pandas, numpy, seaborn, matplotlib)
- ✅ Đọc và kiểm tra dữ liệu từ file `marketing_campaign_sample.csv`
- ✅ Sử dụng regex để tách thông tin từ cột `Target_Audience` thành `Sex` và `Age_Group`
- ✅ Tạo DataFrame mới (`new_df`) với các cột đã được làm sạch

### 2. Phân tích Theo Chủ đề Kinh doanh (Business-Driven Analysis)

#### 2.1 Chủ đề: Tối ưu hóa Lợi nhuận (Profitability Optimization)
- ✅ **Phân tích ROI đa chiều:**
  - **Theo kênh:** Dùng **biểu đồ cột (bar chart)** để so sánh ROI trung bình của các `Channel_Used`.
  - **Theo loại chiến dịch:** Phân tích phân phối ROI bằng **violin plot**.
  - **Theo sự kết hợp Kênh & Loại chiến dịch:** Dùng **heatmap** để tìm sự kết hợp hiệu quả.
  - **Theo sự kết hợp Phân khúc khách hàng & Kênh:** Dùng **heatmap** để phân tích hiệu quả theo `Customer_Segment` và `Channel_Used`.
  - **Theo phân khúc khách hàng:** Dùng **heatmap** để phân tích hiệu quả theo `Customer_Segment`.
  - **Theo địa điểm:** Dùng **heatmap** để phân tích hiệu quả theo `Location`.
  - **Theo độ tuổi:** Dùng **heatmap** để phân tích hiệu quả theo `Age_Group`.
- ✅ **Phân tích Hiệu quả vs. Quy mô:** Dùng **scatter plot** để đánh giá mối quan hệ giữa `ROI` và `Acquisition_Cost`.
- ✅ **Phân tích Xu hướng ROI:** Dùng **line plot** để theo dõi ROI theo thời gian.
- ➡️ **Kết luận chung chủ đề:** Các phân tích trên đều chỉ ra dữ liệu có khả năng cao là nhân tạo do ROI không có sự khác biệt ý nghĩa giữa các chiều phân tích.

#### 2.2 Chủ đề: Tối ưu hóa Chi phí & Nguồn lực (Cost & Resource Optimization)
- ✅ **Phân tích Phân bổ Nguồn lực:**
  - **Theo số lượng:** Phân tích số lượng chiến dịch theo `Campaign_Type` bằng **countplot**.
  - **Theo chi phí:** Phân tích tổng và trung bình chi phí theo `Campaign_Type`.
  - **Theo thời gian:** Phân tích thời gian chạy chiến dịch trung bình theo `Campaign_Type`.
- ➡️ **Kết luận chung chủ đề:** Công ty đang áp dụng chiến lược "an toàn", phân bổ nguồn lực (chi phí, thời gian, số lượng) rất đồng đều giữa các loại chiến dịch.

#### 2.3 Chủ đề: Tối ưu hóa Tương tác (Engagement Optimization)
- ✅ **Phân tích Tỷ lệ chuyển đổi (Conversion Rate):**
  - **Theo Loại chiến dịch:** So sánh `Conversion_Rate` trung bình theo `Campaign_Type`. Kết quả cho thấy tỷ lệ gần như không đổi, củng cố giả thuyết về dữ liệu nhân tạo.
  - **Theo Loại chiến dịch & Kênh:** Dùng **biểu đồ cột nhóm (grouped bar chart)** để tìm ra `Channel_Used` hiệu quả nhất cho từng `Campaign_Type`.
- ⏳ **Phân tích Tỷ lệ Click (CTR):**
  - _Mục tiêu:_ Tính và so sánh `CTR = Clicks / Impressions` theo các chiều (Kênh, Loại chiến dịch) để xem quảng cáo nào hấp dẫn người dùng nhất.
- ⏳ **Phân tích Chi phí mỗi Click (CPC):**
  - _Mục tiêu:_ Tính và so sánh `CPC = Acquisition_Cost / Clicks` để tìm ra kênh mang lại traffic với chi phí hiệu quả nhất.
- ⏳ **Phân tích Mối quan hệ giữa Tương tác và Lợi nhuận:**
  - _Mục tiêu:_ Dùng scatter plot để xem xét liệu `Engagement_Score` cao có dẫn đến `ROI` hoặc `Conversion_Rate` cao không.
- ➡️ **Kết luận chung chủ đề:** (Chưa có)

### 3. Kỹ thuật Visualization đã áp dụng
- ✅ Sử dụng `sns.despine()` để làm sạch biểu đồ (loại bỏ đường viền trên và phải)
- ✅ Tùy chỉnh tiêu đề, nhãn và annotations cho các biểu đồ
- ✅ Ẩn trục không cần thiết để tập trung vào dữ liệu
- ✅ Sử dụng màu sắc nhất quán (#4F8EF7) cho thương hiệu
- ✅ Format số liệu (triệu đồng, thập phân) cho dễ đọc
- ✅ Sử dụng **Violin Plot** để so sánh phân phối dữ liệu.
- ✅ Sử dụng **Heatmap** để phân tích mối quan hệ hai chiều.
- ✅ Sử dụng **Scatter Plot** để trực quan hóa mối quan hệ giữa các biến số.
- ✅ Sử dụng **Line Plot** để phân tích xu hướng theo thời gian.
- ✅ Sử dụng **Biểu đồ cột nhóm (Grouped Bar Chart)** để so sánh các danh mục phụ trong một danh mục chính.
- ✅ Sử dụng **Biểu đồ cột (Bar Chart)** để so sánh giá trị giữa các danh mục.

### 4. Insights chính đã phát hiện
1. **Chiến lược Phân bổ An toàn:** Công ty đang phân bổ đều tài nguyên (số lượng, chi phí, thời gian), chưa tập trung vào một mũi nhọn cụ thể.
2. **Dữ liệu được xác nhận là nhân tạo (Synthetic Data):** Tất cả các phân tích sâu về ROI và Tỷ lệ chuyển đổi đều cho thấy sự phân bố ngẫu nhiên và không có mối quan hệ có ý nghĩa giữa các biến. Đây là bằng chứng vững chắc rằng dữ liệu được tạo ra một cách nhân tạo.

### 5. Công việc đang thực hiện
- ✅ **Hoàn thành giai đoạn phân tích khám phá (EDA):** Đã hoàn thành các phân tích trực quan chính và xác nhận được bản chất của bộ dữ liệu.
- 🔄 **Chuyển sang giai đoạn phân tích Tương tác:** Đang trong quá trình thực hiện các phân tích trong Chủ đề 3.

### 6. Kế hoạch tiếp theo
- ✅ **Phân tích Tối ưu hóa Tương tác (Engagement Optimization):** (Đang thực hiện)
- ⏳ Xây dựng dashboard tương tác với Plotly/Dash
- ⏳ Tổng hợp insights và đề xuất hành động

### 7. Files đã tạo
- ✅ `Plan.md` - Kế hoạch chi tiết 5 giai đoạn
- ✅ `Measures.md` - Danh sách các measures/KPIs marketing
- ✅ `Data_Analysis.ipynb` - Notebook chính chứa code và phân tích
