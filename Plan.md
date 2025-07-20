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

**Mục tiêu:** Trả lời các câu hỏi kinh doanh cụ thể và tìm kiếm "insights" để trình bày. Dưới đây là các nhóm câu hỏi trọng tâm cần giải đáp:

**1. Câu hỏi về Hiệu quả và Lợi nhuận (Performance & Profitability)**
*   Loại chiến dịch (`Campaign_Type`) nào mang lại Lợi tức Đầu tư (ROI) cao nhất?
*   Kênh quảng cáo (`Channel_Used`) nào có Tỷ lệ chuyển đổi (`Conversion_Rate`) tốt nhất?
*   Đâu là top 5 chiến dịch có ROI cao nhất và top 5 chiến dịch có ROI thấp nhất? Đặc điểm chung của chúng là gì?

**2. Câu hỏi về Chi phí và Tối ưu Ngân sách (Cost & Budget Optimization)**
*   Kênh (`Channel_Used`) hoặc Phân khúc khách hàng (`Customer_Segment`) nào có chi phí để tạo ra một chuyển đổi (CPA) là thấp nhất?
*   Kênh nào có chi phí cho mỗi lượt nhấp (CPC) rẻ nhất?
*   Liệu việc chi nhiều tiền hơn (`Accquisition_Cost`) có luôn đồng nghĩa với việc thu về ROI cao hơn không?

**3. Câu hỏi về Đối tượng và Phân khúc Khách hàng (Audience & Segmentation)**
*   Phân khúc khách hàng (`Customer_Segment`, `Age_Group`, `Sex`) nào tương tác (`Engagement_Score`) và chuyển đổi tốt nhất?
*   Chiến dịch sử dụng Ngôn ngữ (`Language`) nào, tại Thành phố (`Location`) nào đang hoạt động hiệu quả nhất?

**4. Câu hỏi về Kênh và Chiến lược Nội dung (Channel & Content Strategy)**
*   Kênh nào (Google Ads, YouTube,...) phù hợp nhất cho từng loại chiến dịch (Email, Influencer,...)?
*   Điểm tương tác (`Engagement_Score`) cao có dẫn đến Tỷ lệ chuyển đổi cao không?
*   Thời lượng (`Duration`) của một chiến dịch ảnh hưởng đến hiệu suất của nó như thế nào?

**5. Câu hỏi về Xu hướng theo Thời gian (Trends Over Time)**
*   Xu hướng của tổng chi phí, tổng số lượt nhấp và ROI trung bình thay đổi như thế nào qua các tháng?

**Công cụ trực quan hóa gợi ý:**
*   **Biểu đồ cột nhóm:** Để so sánh các chỉ số (ROI, Conversion Rate) theo các danh mục (`Campaign_Type`, `Channel_Used`).
*   **Heatmap:** Để phân tích hiệu suất theo `Customer_Segment` hoặc xem ma trận tương quan.
*   **Biểu đồ đường:** Để thể hiện xu hướng theo thời gian (`Month`).
*   **Biểu đồ phân tán:** Để khám phá mối quan hệ giữa hai biến số (ví dụ: `Acquisition_Cost` vs `ROI`).

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