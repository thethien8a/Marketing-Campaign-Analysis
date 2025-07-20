# Báo cáo: Hiệu suất Chiến dịch Marketing

## Mô tả Dataset:
Dataset về Hiệu suất Chiến dịch Marketing cung cấp những thông tin quan trọng về hiệu quả của các chiến dịch marketing khác nhau. Dataset này ghi lại các chỉ số hiệu suất, đối tượng mục tiêu, thời gian, kênh sử dụng, và các yếu tố thiết yếu khác góp phần vào thành công của các chiến dịch. Với 200.000 dòng dữ liệu độc nhất trải dài trong hai năm, dataset này mang lại cái nhìn toàn diện về hiệu suất chiến dịch trên nhiều công ty và phân khúc khách hàng.

## Các cột trong Dataset:
1. **Company**: Công ty chịu trách nhiệm thực hiện chiến dịch, bao gồm các thương hiệu giả định.
2. **Campaign_Type**: Loại chiến dịch được sử dụng, bao gồm email, mạng xã hội, influencer, quảng cáo hiển thị, hoặc tìm kiếm.
3. **Target_Audience**: Phân khúc đối tượng mục tiêu của chiến dịch, ví dụ: phụ nữ từ 25-34 tuổi, nam giới từ 18-24 tuổi, hoặc tất cả nhóm tuổi.
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

## Phạm vi ứng dụng:
Bằng cách sử dụng dataset này, các nhà tiếp thị và nhà phân tích dữ liệu có thể khám phá những thông tin giá trị về hiệu suất chiến dịch, sở thích của đối tượng mục tiêu, hiệu quả của kênh, và ROI. Dataset này là một nguồn tài nguyên quý giá cho nghiên cứu thị trường, tối ưu hóa chiến dịch, và ra quyết định dựa trên dữ liệu, giúp doanh nghiệp cải thiện chiến lược marketing và thúc đẩy tăng trưởng có mục


## Tổng hợp công việc đã thực hiện - Marketing Campaign Analysis

### 1. Giai đoạn Chuẩn bị và Làm sạch dữ liệu (Data Preparation)
- ✅ Import các thư viện cần thiết (pandas, numpy, seaborn, matplotlib)
- ✅ Đọc và kiểm tra dữ liệu từ file `marketing_campaign_sample.csv`
- ✅ Sử dụng regex để tách thông tin từ cột `Target_Audience` thành `Sex` và `Age_Group`
- ✅ Tạo DataFrame mới (`new_df`) với các cột đã được làm sạch

### 2. EDA (Exploratory Data Analysis) - Đã hoàn thành

#### 2.1 Phân tích Phân bổ Chiến dịch (Campaign Distribution)
- ✅ **Phân bổ số lượng chiến dịch theo loại (`Campaign_Type`):**
  - Tạo biểu đồ countplot để xem phân bổ các loại chiến dịch
  - Kết luận: Nguồn lực phân bổ ở các kênh khá đều nhau, công ty đang chơi "an toàn"

#### 2.2 Phân tích Chi phí (Cost Analysis)
- ✅ **Tổng chi phí theo loại chiến dịch:**
  - Vẽ biểu đồ cột hiển thị tổng chi phí theo `Campaign_Type`
  - Kết luận: Tổng chi phí tỷ lệ thuận với số lượng chiến dịch

- ✅ **Chi phí trung bình cho mỗi chiến dịch:**
  - Tính và hiển thị chi phí trung bình theo từng loại chiến dịch
  - Kết luận: Chi phí trung bình cho mỗi chiến dịch gần như bằng nhau, công ty chưa dám đầu tư mạnh vào kênh cụ thể

#### 2.3 Phân tích Thời gian Chiến dịch (Duration Analysis)
- ✅ **Thời gian diễn ra trung bình cho mỗi chiến dịch:**
  - Tính và visualize thời gian trung bình (`Duration (days)`) theo `Campaign_Type`
  - Kết luận: Hầu như không có sự khác biệt về thời gian giữa các loại chiến dịch

#### 2.4 Phân tích Hiệu suất (Performance Analysis)
- ✅ **ROI trung bình theo kênh quảng cáo:**
  - Tính ROI trung bình theo `Channel_Used` và tạo biểu đồ cột.
- ✅ **Phân phối ROI theo loại chiến dịch:**
  - Sử dụng **violin plot** để xem xét sự phân tán của ROI theo `Campaign_Type`.
  - Kết luận: Phân phối ROI của tất cả các loại chiến dịch gần như giống hệt nhau, cho thấy dữ liệu có thể là nhân tạo (synthetic data).
- ✅ **Phân tích ROI hai chiều (Loại chiến dịch vs. Kênh):**
  - Sử dụng **heatmap** để tìm ra sự kết hợp hiệu quả nhất.
  - Kết luận: ROI chỉ có sự khác biệt rất nhỏ (từ 4.9 đến 5.1), củng cố thêm nghi ngờ về tính xác thực của dữ liệu.
- ✅ **Phân tích ROI vs. Chi phí (Cost vs. ROI):**
  - Sử dụng **scatter plot** để đánh giá mối quan hệ giữa chi phí, ROI, loại chiến dịch và lượt hiển thị.
  - Kết luận: Biểu đồ hỗn loạn như một "đám mây" dữ liệu ngẫu nhiên, không có xu hướng hay cụm nào rõ ràng. Đây là bằng chứng mạnh mẽ nhất xác nhận dữ liệu được tạo ra một cách nhân tạo.
- ✅ **Phân tích Hiệu quả Chiến dịch theo Phân khúc Khách hàng:**
  - Sử dụng **heatmap** để so sánh hiệu quả ROI của các `Campaign_Type` trên từng `Customer_Segment`.
  - Kết luận: Biểu đồ tiếp tục cho thấy sự thiếu khác biệt đáng kể về ROI (chỉ dao động nhỏ từ 4.9 đến 5.1), củng cố thêm bằng chứng về dữ liệu nhân tạo. Các "điểm nóng" và "điểm lạnh" không thực sự nổi bật.
- ✅ **Phân tích Hiệu quả Chiến dịch theo Địa điểm:**
  - Sử dụng **heatmap** thứ hai để so sánh hiệu quả ROI của các `Campaign_Type` tại từng `Location`.
  - Kết luận: Tương tự các phân tích trước, kết quả gần như đồng nhất và không cho thấy sự khác biệt có ý nghĩa về mặt chiến lược giữa các địa điểm, tiếp tục xác nhận bản chất của dữ liệu.
- ✅ **Phân tích Hiệu quả Chiến dịch theo Độ tuổi:**
  - Sử dụng **heatmap** thứ hai để so sánh hiệu quả ROI của các `Campaign_Type` tại từng `Age_Group`.
  - Kết luận: Tương tự các phân tích trước, kết quả gần như đồng nhất và không cho thấy sự khác biệt có ý nghĩa về mặt chiến lược giữa độ tuổi, tiếp tục xác nhận bản chất của dữ liệu.
- ✅ **Phân tích Xu hướng ROI theo Thời gian:**
  - Sử dụng **biểu đồ đường (line plot)** để theo dõi ROI trung bình hàng tháng, ngày của các `Campaign_Type`.
  - Kết luận: Các đường biểu diễn biến động một cách ngẫu nhiên như "spaghetti", không cho thấy bất kỳ tính mùa vụ hay xu hướng dài hạn nào, củng cố thêm bằng chứng về dữ liệu nhân tạo.

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

### 4. Insights chính đã phát hiện
1. **Chiến lược Conservative:** Công ty đang phân bổ đều tài nguyên, chưa tập trung vào kênh cụ thể.
2. **Chi phí Standardized:** Chi phí trung bình cho mỗi chiến dịch tương đương nhau.
3. **Thời gian Consistent:** Không có sự khác biệt đáng kể về thời gian chạy chiến dịch.
4. **Dữ liệu được xác nhận là nhân tạo (Synthetic Data):** Tất cả các phân tích sâu về ROI (violin plot, heatmap, và đặc biệt là scatter plot) đều cho thấy sự phân bố ngẫu nhiên và không có mối quan hệ có ý nghĩa giữa các biến. Đây là bằng chứng vững chắc rằng dữ liệu được tạo ra một cách nhân tạo.

### 5. Công việc đang thực hiện
- ✅ **Hoàn thành giai đoạn EDA:** Đã hoàn thành các phân tích trực quan chính và xác nhận được bản chất của bộ dữ liệu.
- 🔄 **Chuẩn bị tổng kết:** Đang trong quá trình tổng hợp các phát hiện về chất lượng dữ liệu và chuẩn bị các bước tiếp theo.

### 6. Kế hoạch tiếp theo (theo Plan.md)
- ⏳ Hoàn thành phân tích tương quan
- ⏳ Phân tích theo các chiều khác (ví dụ: `Language`)
- ⏳ Xây dựng dashboard tương tác với Plotly/Dash
- ⏳ Tổng hợp insights và đề xuất hành động

### 7. Files đã tạo
- ✅ `Plan.md` - Kế hoạch chi tiết 5 giai đoạn
- ✅ `Measures.md` - Danh sách các measures/KPIs marketing
- ✅ `Data_Analysis.ipynb` - Notebook chính chứa code và phân tích
