# Project Phân tích Hiệu quả Marketing (Marketing Performance Analysis)

## 1. Tóm tắt Dự án & Năng lực Phân tích (Project Summary & Analytical Competencies)

### Giới thiệu
Đây là một dự án phân tích dữ liệu cá nhân được thực hiện nhằm mục đích **học hỏi và áp dụng các kỹ thuật phân tích vào bài toán marketing**. Mục tiêu là xử lý một bộ dữ liệu thô, khám phá các insights tiềm ẩn, và trình bày kết quả một cách có cấu trúc như trong môi trường doanh nghiệp.

### Phương pháp Phân tích
Dự án được tiếp cận một cách có hệ thống, chuyển từ phân tích khám phá ban đầu sang **phân tích theo định hướng mục tiêu kinh doanh**, tập trung vào 3 chủ đề chính:
1.  **Tối ưu hóa Lợi nhuận (Profitability Optimization)**
2.  **Tối ưu hóa Chi phí & Nguồn lực (Cost & Resource Optimization)**
3.  **Tối ưu hóa Tương tác (Engagement Optimization)**

### Các Kỹ năng và Kỹ thuật Chính Đã Thể hiện
- **Làm sạch & Chuẩn bị Dữ liệu (Data Cleaning & Preparation):**
  - Sử dụng **Regex (Regular Expressions)** để trích xuất và tạo các thuộc tính mới (`Sex`, `Age_Group`) từ dữ liệu văn bản thô.
  - Xử lý các giá trị thiếu và tạo các cột tính toán mới.

- **Phân tích Khám phá Dữ liệu (EDA):**
  - Áp dụng đa dạng các loại biểu đồ của **Seaborn & Matplotlib** để khám phá các khía cạnh khác nhau của dữ liệu.

- **Kiến thức về Metrics Marketing (Marketing Metrics Knowledge):**
  - Tính toán và phân tích sâu các chỉ số marketing quan trọng:
    - **ROI** (Return on Investment)
    - **ROAS** (Return on Ad Spend)
    - **CTR** (Click-Through Rate)
    - **CPC** (Cost Per Click)
    - **CPA** (Cost Per Acquisition)
    - **Impressions & Engagement Score**

- **Các Kỹ thuật Phân tích Nâng cao (Advanced Analytical Techniques):**
  - **Phân tích Đa chiều (Multi-dimensional Analysis):** Sử dụng **heatmap** để đánh giá hiệu suất (ROI, CPA) qua sự kết hợp của nhiều yếu tố (ví dụ: Kênh x Loại chiến dịch).
  - **Phân tích Danh mục (Portfolio Analysis):**
    - **Phân tích Pareto (80/20):** Xác định các kênh marketing "quan trọng" đóng góp 80% lợi nhuận.
    - **Phân tích Tứ phân vị (Quadrant Analysis):** Phân loại các kênh/chiến dịch dựa trên hiệu suất (ví dụ: CTR vs. CPC, ROAS vs. CPA) để đưa ra quyết định chiến lược.
  - **Phân tích Xu hướng (Trend Analysis):** Sử dụng **line plot** để theo dõi sự thay đổi của các metrics (ROI, CTR, CPC) theo thời gian.

- **Tư duy Phản biện & Đánh giá Dữ liệu (Critical Thinking & Data Assessment):**
  - **Thành tựu nổi bật:** Thông qua phân tích, đã **phát hiện và chứng minh được bộ dữ liệu là dữ liệu nhân tạo (synthetic data)** do thiếu các mối quan hệ có ý nghĩa thống kê. Điều này thể hiện khả năng không chỉ phân tích mà còn **đánh giá chất lượng và tính thực tế của dữ liệu**—một kỹ năng quan trọng của một Data Analyst.

### Kết quả
- Hoàn thành một báo cáo phân tích toàn diện (file `README.md` này), cấu trúc theo các mục tiêu kinh doanh, trình bày các phát hiện và trực quan hóa dữ liệu.
- Xây dựng được một notebook phân tích (`Data_Analysis.ipynb`) ghi lại toàn bộ quy trình code và các bước thực hiện.

---

## 2. Quy trình Phân tích Chi tiết (Detailed Analysis Process)

### 2.1. Chủ đề: Tối ưu hóa Lợi nhuận (Profitability Optimization)
- ✅ **Phân tích ROI đa chiều:** Theo kênh, loại chiến dịch, phân khúc khách hàng, địa điểm, và sự kết hợp giữa chúng bằng **bar chart, violin plot, heatmap**.
- ✅ **Phân tích Hiệu quả vs. Quy mô/Thời gian:** Đánh giá mối quan hệ giữa `ROI` và `Acquisition_Cost`/`Duration` bằng **scatter plot**.
- ✅ **Phân tích Xu hướng ROI:** Theo dõi ROI theo thời gian bằng **line plot**.

### 2.2. Chủ đề: Tối ưu hóa Chi phí & Nguồn lực (Cost & Resource Optimization)
- ✅ **Phân tích Phân bổ Nguồn lực:** Phân tích số lượng, chi phí, thời gian của chiến dịch theo `Campaign_Type`.
- ✅ **Phân tích Hiệu quả Chi phí (Cost Efficiency):**
  - So sánh **CPA** và **ROAS** giữa các kênh/loại chiến dịch bằng **bar chart, violin plot**.
  - Sử dụng **Quadrant Analysis (ROAS vs. CPA)** để phân loại và đề xuất chiến lược ngân sách.
- ✅ **Phân tích Tối ưu hóa Danh mục (Portfolio Optimization):**
  - Áp dụng **Phân tích Pareto (80/20)** để xác định các kênh đóng góp nhiều lợi nhuận nhất.

### 2.3. Chủ đề: Tối ưu hóa Tương tác (Engagement Optimization)
- ✅ **Phân tích Tỷ lệ Click (CTR):** So sánh CTR theo loại chiến dịch và kênh bằng **bar chart, grouped bar chart**.
- ✅ **Phân tích Chi phí mỗi Click (CPC):** So sánh CPC giữa các kênh quảng cáo.
- ✅ **Phân tích Mối quan hệ Tương tác vs. Kinh doanh:** Kiểm tra tương quan giữa `Engagement_Score` và `ROI`/`Conversion_Rate` bằng **scatter plot**.
- ✅ **Phân tích Chiến lược Tương tác:** Sử dụng **Quadrant Analysis (CTR vs. CPC)** để xác định các kênh "ngôi sao", "mỏ vàng",...
- ✅ **Phân tích Xu hướng Tương tác:** Theo dõi `CTR` & `CPC` theo thời gian bằng **line plot**.

---

## 3. Các Công cụ & Kỹ thuật Trực quan hóa Đã sử dụng
- **Ngôn ngữ & Thư viện:** Python, Pandas, NumPy, Matplotlib, Seaborn.
- **Biểu đồ:** Bar Chart, Grouped Bar Chart, Violin Plot, Heatmap, Scatter Plot (với đường hồi quy và phân loại), Line Plot, Count Plot, Biểu đồ kết hợp.
- **Kỹ thuật làm sạch biểu đồ:** Sử dụng `sns.despine()`, tùy chỉnh tiêu đề, nhãn, định dạng số liệu để tăng tính trực quan và chuyên nghiệp.
