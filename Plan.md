# Kế hoạch Phân tích Dữ liệu Chiến dịch Marketing

Dưới đây là kế hoạch chi tiết để phân tích file dữ liệu `marketing_campaign_sample.csv`, nhằm mục tiêu hiểu rõ hiệu suất các chiến dịch đã qua và trình bày kết quả cho Trưởng phòng Marketing thông qua một dashboard tương tác.

### **Giai đoạn 1: Thiết lập & Khám phá Dữ liệu (Setup & EDA)**

**Mục tiêu:** Chuẩn bị môi trường, làm sạch và hiểu cấu trúc cơ bản của dữ liệu. Đây là nền tảng cho mọi phân tích sâu hơn.

1.  **Thiết lập môi trường:** Import các thư viện cần thiết (`pandas`, `numpy`, `plotly.express`, `matplotlib.pyplot`/`seaborn`).
2.  **Tải và Kiểm tra Dữ liệu:**
    *   Đọc file `marketing_campaign_sample.csv` vào DataFrame.
    *   Sử dụng `.info()` để kiểm tra kiểu dữ liệu (đặc biệt là cột `Date`).
    *   Sử dụng `.describe()` để xem thống kê tóm tắt và phát hiện giá trị bất thường.
3.  **Làm sạch Dữ liệu:**
    *   Chuẩn hóa tên cột (ví dụ: `Accquisition_Cost ($)` -> `Acquisition_Cost`).
    *   Kiểm tra và xử lý các giá trị thiếu hoặc không nhất quán.

### **Giai đoạn 2: Kỹ thuật tạo đặc trưng (Feature Engineering)**

**Mục tiêu:** Tạo các cột dữ liệu mới để làm giàu thông tin, phục vụ cho phân tích theo thời gian và các chỉ số hiệu suất quan trọng.

1.  **Tách thông tin thời gian:** Từ cột `Date`, tạo ra các cột `Year`, `Month`, `DayOfWeek`.
2.  **Tính toán chỉ số Marketing phái sinh:**
    *   `Cost_Per_Click (CPC)` = `Acquisition_Cost / Clicks`
    *   `Cost_Per_Impression (CPM)` = `(Acquisition_Cost / Impressions) * 1000`
    *   `Engagement_Rate` = `(Engagement_Score / 10) * 100`

### **Giai đoạn 3: Phân tích Khám phá Chuyên sâu (In-depth Analysis & Insights)**

**Mục tiêu:** Trả lời các câu hỏi kinh doanh cụ thể và tìm kiếm "insights" để trình bày.

1.  **Tổng quan hiệu suất:** Tính các chỉ số trung bình (ROI, Conversion Rate, CPC) trên toàn bộ dữ liệu.
2.  **Hiệu suất theo Loại chiến dịch & Kênh:** So sánh ROI, Conversion Rate giữa các `Campaign_Type` và `Channel_Used` (Gợi ý biểu đồ: Biểu đồ cột nhóm).
3.  **Hiệu suất theo Phân khúc Khách hàng:** Phân tích hiệu suất theo `Customer_Segment`, `Age_Group`, `Sex` (Gợi ý biểu đồ: Heatmap).
4.  **Phân tích theo Địa lý và Thời gian:**
    *   So sánh hiệu suất giữa các `Location`.
    *   **Quan trọng:** Vẽ biểu đồ đường để xem xu hướng của chi phí, clicks, và ROI qua các `Month`.
5.  **Phân tích Tương quan:** Tạo một heatmap tương quan để xem các yếu tố nào ảnh hưởng mạnh nhất đến `ROI`.

### **Giai đoạn 4: Xây dựng Dashboard Tương tác (Dashboard Creation)**

**Mục tiêu:** Tổng hợp tất cả các insights vào một dashboard trực quan, dễ sử dụng.

1.  **Lựa chọn công cụ:** Sử dụng `Plotly` và `Dash` (hoặc `Streamlit`).
2.  **Thiết kế bố cục:**
    *   **Bộ lọc (Filters):** Cho phép người dùng lọc theo `Campaign_Type`, `Location`, `Month`.
    *   **Thẻ KPI:** Hiển thị các chỉ số chính.
    *   **Phần thân:** Bao gồm các biểu đồ chi tiết từ Giai đoạn 3.

### **Giai đoạn 5: Tổng hợp & Đề xuất (Synthesis & Recommendations)**

**Mục tiêu:** Chuyển từ "phân tích" sang "tư vấn", đưa ra những kết luận và đề xuất hành động cụ thể.

1.  **Tóm tắt những phát hiện chính:** Trình bày 3-5 insight quan trọng nhất một cách ngắn gọn.
    *   *Ví dụ: "Phân tích cho thấy các chiến dịch Email Marketing nhắm vào phân khúc 'Health & Wellness' mang lại ROI cao hơn 30% so với mức trung bình."*
2.  **Đề xuất Hành động:** Dựa trên các phát hiện, đề xuất các bước tiếp theo.
    *   *Ví dụ: "Đề xuất tăng ngân sách cho các chiến dịch Google Ads cho phân khúc 'Tech Enthusiasts'."*
3.  **Hạn chế và Hướng phát triển:** Nêu rõ các hạn chế của phân tích và gợi ý các bước phân tích sâu hơn trong tương lai. 