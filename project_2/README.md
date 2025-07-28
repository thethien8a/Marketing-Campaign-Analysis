# Phân tích Hiệu suất Chiến dịch Marketing & Xây dựng Dashboard

Dự án này tập trung vào việc phân tích dữ liệu từ các chiến dịch marketing để rút ra những hiểu biết sâu sắc và xây dựng các dashboard tương tác nhằm hỗ trợ việc ra quyết định.

---

## 1. Bối cảnh & Mục tiêu

### Bối cảnh
- **Nguồn dữ liệu:** Dữ liệu về các chiến dịch marketing được thu thập từ trang facebook Mastering Data Analytics.
- **Tình huống:** Một công ty cần đánh giá hiệu quả của các hoạt động marketing đã triển khai trên nhiều nền tảng, với nhiều loại nội dung và nhắm đến các đối tượng khách hàng khác nhau.

### Mục tiêu chính
- Xây dựng **4 dashboards chuyên sâu** để trực quan hóa dữ liệu, giúp các bên liên quan (từ marketing team đến ban lãnh đạo) dễ dàng theo dõi, phân tích và tối ưu hóa hiệu suất.

---

## 2. Kế hoạch Xây dựng Dashboards

Dưới đây là kế hoạch chi tiết cho từng dashboard sẽ được xây dựng.

### Dashboard 1: Tổng quan Hiệu suất (Performance Overview)
*   **Mục tiêu:** Cung cấp cái nhìn 360 độ về sức khỏe của tất cả các chiến dịch.
*   **Đối tượng sử dụng:** Ban lãnh đạo (C-Level), Trưởng phòng Marketing.
*   **Câu hỏi trả lời:** "Tình hình marketing tổng thể đang như thế nào?"
*   **Những thứ đối tượng sử dụng có thể quan tâm:**
    -   **Hiệu quả tài chính:** Lợi nhuận ròng (Doanh thu - Chi phí) và ROAS (Return on Ad Spend) là bao nhiêu? Mỗi đồng chi ra mang về bao nhiêu đồng doanh thu?
    -   **Xu hướng tăng trưởng:** Tình hình doanh thu, chi phí và hiệu quả (ROAS) đang tốt lên hay xấu đi theo thời gian?
    -   **Cơ hội & Rủi ro:** Có kênh nào đang chiếm tỷ trọng quá lớn không? Đâu là cơ hội để tăng trưởng?
*   **Các chỉ số chính (KPIs):**
    -   Tổng Doanh thu, Tổng Chi phí, ROAS trung bình
    -   Tổng Chuyển đổi, CPA trung bình

### Dashboard 2: Phân tích Kênh & Nội dung (Channel & Content Deep Dive)
*   **Mục tiêu:** So sánh hiệu quả giữa các kênh và loại nội dung để tối ưu hóa ngân sách.
*   **Đối tượng sử dụng:** Đội ngũ Marketing (Marketing Team), Chuyên viên quảng cáo (Ad Specialists).
*   **Câu hỏi trả lời:** "Nên đầu tư tiền vào đâu và dạng nội dung nào?"
*   **Các chỉ số chính (KPIs):**
    -   ROAS, CPA, CTR theo Nền tảng
    -   ROAS, CPA, CTR theo Loại nội dung

### Dashboard 3: Phân tích Chân dung Khách hàng (Customer Persona Analysis)
*   **Mục tiêu:** Hiểu rõ khách hàng mục tiêu là ai và họ ở đâu.
*   **Đối tượng sử dụng:** Trưởng phòng Marketing, Đội ngũ Sáng tạo Nội dung (Content Team), Chuyên viên quảng cáo.
*   **Câu hỏi trả lời:** "Ai là khách hàng giá trị nhất của chúng ta?"
*   **Các chỉ số chính (KPIs):**
    -   Doanh thu, CPA theo Nhóm tuổi
    -   Doanh thu, CPA theo Giới tính
    -   Doanh thu, CPA theo Khu vực

### Dashboard 4: Phân tích Ngân sách & Thời gian (Budget & Duration Analysis)
*   **Mục tiêu:** Đánh giá mối quan hệ giữa chi tiêu, thời gian và hiệu quả.
*   **Đối tượng sử dụng:** Trưởng phòng Marketing, Chuyên viên Lập kế hoạch (Media Planners).
*   **Câu hỏi trả lời:** "Chi tiêu bao nhiêu và trong bao lâu là tối ưu?"
*   **Các chỉ số chính (KPIs):**
    -   Tương quan giữa Ngân sách và Doanh thu
    -   Tương quan giữa Thời gian chạy và ROAS

## 3. Công cụ sử dụng (dự kiến)
- **Ngôn ngữ:** Python (Pandas, Matplotlib, Seaborn, ...)
- **Công cụ Dashboard:** Streamlit
- **Deployment:** Streamlit Sharing
- **Công cụ phân tích:** Jupyter Notebook
