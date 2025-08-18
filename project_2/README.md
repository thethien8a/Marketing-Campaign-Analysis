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

**Biểu đồ đề xuất (impact cao):**
- KPI Cards: Total Revenue, Total Spend, Avg ROAS, Total Conversions, Avg CPA (+ % thay đổi MoM/7 ngày).
- Line: Revenue vs Spend theo thời gian; tùy chọn thêm ROAS trên trục phụ; có rolling mean 7/30 ngày.
- Bar horizontal (sorted): ROAS theo Platform kèm overlay/annotation Total Spend để tránh bẫy ROAS thấp mẫu.
- Pareto/stacked bar: Đóng góp %Revenue và %Spend theo Platform (nhận diện 80/20 và rủi ro tập trung).
- Watchlist (bảng nhỏ): Top Platform có ROAS giảm > X% trong 14/30 ngày hoặc CPA > ngưỡng.

---

### Dashboard 2: Phân tích Kênh & Nội dung (Channel & Content Deep Dive)
*   **Mục tiêu:** So sánh hiệu quả giữa các kênh và loại nội dung để tối ưu hóa ngân sách.
*   **Đối tượng sử dụng:** Đội ngũ Marketing (Marketing Team), Chuyên viên quảng cáo (Ad Specialists).
*   **Câu hỏi trả lời:** "Nên đầu tư tiền vào đâu và dạng nội dung nào?"
*   **Các chỉ số chính (KPIs) & chỉ số phụ:**
    -   **Chỉ số hiệu quả chính:** ROAS, CPA
    -   **Chỉ số tương tác & chi phí:** CTR, CPC (Chi phí mỗi lượt nhấp)
    -   **Chỉ số chất lượng traffic:** Conversion Rate (Tỷ lệ chuyển đổi)
    -   *Tất cả các chỉ số được phân tích theo Nền tảng và Loại nội dung.*

**Biểu đồ đề xuất:**
- Bar/boxplot: ROAS, CPA, CTR theo Platform (so sánh phân phối và median).
- Bar/boxplot: ROAS, CPA, CTR theo Content_Type.
- Scatter (bubble): x = Spend, y = ROAS, size = Revenue, color = Platform (định vị kênh hiệu quả).
- Pareto theo Platform/Content_Type: %Revenue đóng góp top-N.
- Table: Top-N creatives/campaign theo ROAS/Revenue với số liệu hỗ trợ (Spend, Conversions).

#### Bổ sung để toàn diện hóa:
- **Metrics dẫn xuất mới:**
  - **CPM (Cost per Mille):** \( \frac{Spend \times 1000}{Impressions} \) – Đo lường chi phí tiếp cận (awareness stage).
  - **Funnel Drop-off Rate:** \( 1 - Conversion_Rate \) – Tỷ lệ mất mát từ Click → Conversion.
  - **Content Engagement Score:** Weighted average of CTR + Conversion_Rate.
  - **Attribution Share:** % Revenue attributed to each Platform/Content_Type.

- **Visualizations mới:**
  - **Sankey Diagram:** Flow từ Impressions → Clicks → Conversions theo Platform/Content_Type, với drop-off rates.
  - **Heatmap Content × Platform:** ROAS/CPM/CTR với color gradient, filter bằng Duration.
  - **A/B Testing Simulator:** Bảng so sánh Content_Type trên cùng Platform với statistical significance (t-test trên ROAS/CPA).

- **Insights & Recommendations:** 
  - Phân tích funnel để xác định "leak" (e.g., high drop-off ở CTR cho Text content).
  - Gợi ý reallocation: "Chuyển ngân sách từ Platform X (CPM cao, drop-off 40%) sang Y (ROAS >3x với Carousel)" – Tăng ROI 20-30% qua optimization dựa trên attribution.

---

### Dashboard 3: Phân tích Chân dung Khách hàng (Customer Persona Analysis)
*   **Mục tiêu:** Hiểu rõ khách hàng mục tiêu là ai và họ ở đâu.
*   **Đối tượng sử dụng:** Trưởng phòng Marketing, Đội ngũ Sáng tạo Nội dung (Content Team), Chuyên viên quảng cáo.
*   **Câu hỏi trả lời:** "Ai là khách hàng giá trị nhất của chúng ta?"
*   **Các chỉ số chính (KPIs) & chỉ số phụ:**
    -   **Chỉ số giá trị:** Revenue, ROAS
    -   **Chỉ số chi phí & hiệu quả:** CPA, Conversion Rate
    -   **Chỉ số quy mô:** Conversions (Tổng số chuyển đổi)
    -   *Tất cả các chỉ số được phân tích theo Nhóm tuổi, Giới tính, và Khu vực.*

**Biểu đồ đề xuất:**
- Heatmap: ROAS/CPA theo Age_Group x Gender (nhận diện persona hiệu quả).
- Bar: Revenue và CPA theo Region (2 trục hoặc 2 chart song song).
- Stacked bar: Revenue theo Age_Group trong từng Platform (interaction effect nếu cần).
- Map/choropleth: Revenue/ROAS theo Region (nếu có mapping địa lý).

#### Bổ sung để toàn diện hóa:
- **Metrics dẫn xuất mới:**
  - **Customer Lifetime Value (CLV) Proxy:** \( \frac{Revenue}{Conversions} \times Average Duration \).
  - **RFM Segmentation:** Recency (từ Date), Frequency (Conversions per Campaign_ID), Monetary (Revenue per persona) – Phân loại "High-Value", "At-Risk", "New".
  - **Persona Profitability:** Profit = Revenue - Spend, weighted by Conversion_Rate.
  - **Cross-Segment Interaction:** ROAS theo Age × Gender × Region.

- **Visualizations mới:**
  - **Cohort Matrix:** Heatmap Retention/ROAS theo Date, group by Persona (Age/Gender/Region).
  - **Persona Radar Chart:** So sánh multiple personas trên metrics (ROAS, CPA, CLV, Conversion_Rate).
  - **Treemap:** Hierarchy Region → Age_Group → Gender với size = Revenue, color = ROAS, filter bằng Platform.

- **Insights & Recommendations:** 
  - Sử dụng RFM để segment và predict churn.
  - Gợi ý targeting: "Target Male 45-54 ở Asia với Video để tăng CLV 15%, dựa trên low churn rate" – Kèm personalization ideas (e.g., ad copy tailored by gender/age).

---

### Dashboard 4: Phân tích Ngân sách & Thời gian (Budget & Duration Analysis)
*   **Mục tiêu:** Đánh giá mối quan hệ giữa chi tiêu, thời gian và hiệu quả.
*   **Đối tượng sử dụng:** Trưởng phòng Marketing, Chuyên viên Lập kế hoạch (Media Planners).
*   **Câu hỏi trả lời:** "Chi tiêu bao nhiêu và trong bao lâu là tối ưu?"
*   **Các chỉ số chính (KPIs):**
    -   Tương quan giữa Chi tiêu thực tế (`Spend`) và Doanh thu (`Revenue`), ROAS.
    -   Tương quan giữa Thời gian chạy (`Duration`) và Hiệu quả (`ROAS`, `CPA`).
    -   Phân tích `Impressions` trong mối quan hệ với `Spend` để đánh giá chi phí hiển thị.

**Biểu đồ đề xuất:**
- Scatter: Budget/Spend vs Revenue (size = Conversions, color = ROAS) + đường fit (regression) để thấy trend.
- Line/scatter: Duration (ngày chạy) vs ROAS; thêm LOESS/regression để quan sát hiệu ứng thời lượng.
- Marginal/joint plot: phân phối Budget và Revenue kèm tương quan Pearson/Spearman.
- Bubble timeline (optional): theo Campaign_ID, kích thước theo Spend, màu theo ROAS.

#### Bổ sung để toàn diện hóa:
- **Metrics dẫn xuất mới:**
  - **Budget Pacing:** \( \frac{Spend}{Budget} \times 100\% \), Daily Spend = \( \frac{Spend}{Duration} \).
  - **Forecasted ROAS:** Linear regression từ Spend/Duration/Date để dự báo Revenue/ROAS.
  - **Break-even Point:** Spend level nơi ROAS =1 (Profit=0).
  - **Time Decay Attribution:** Weighted ROAS theo Date (recent days trọng số cao hơn).

- **Visualizations mới:**
  - **Scenario Simulator:** Interactive scatter với sliders cho "What-if" (e.g., tăng Budget 20% → forecasted Revenue).
  - **Time-Series Forecast:** Line chart ROAS/Revenue theo Date, với ARIMA forecast line và anomaly detection.
  - **Budget Allocation Pie:** % Budget vs % Revenue theo Platform/Duration buckets, với break-even lines.

- **Insights & Recommendations:** 
  - Forecasting để hỗ trợ media planning.
  - Gợi ý allocation: "Reallocate 15% từ campaigns Duration >20 days (ROAS decay 25%) sang short bursts để tăng ROI 10%" – Kèm risk assessment (e.g., volatility từ low sample size).

---

### Gợi ý triển khai tương tác (áp dụng cho tất cả dashboards)
- Filters: Date range, Platform, Region, Content_Type, Budget/Spend range.
- Toàn bộ biểu đồ phản ứng theo filter; hỗ trợ tải CSV/Excel dữ liệu đã lọc.
- Chú ý chuẩn hóa công thức: ROAS = Revenue / Spend; CPA = Spend / Conversions.

---

## 3. Lược đồ dữ liệu (Data Schema)

- Nguồn: `Sample_data.csv`
- Lưu ý: Cột đầu tiên trong file là chỉ số dòng (không có tên). Khi đọc bằng pandas có thể bỏ bằng `index_col=0`.

### Danh sách trường dữ liệu
- **Index (không tên)** — integer: Chỉ số dòng; có thể bỏ qua khi phân tích.
- **Campaign_ID** — string: Mã chiến dịch.
- **Budget** — float: Ngân sách dự kiến cho chiến dịch.
- **Clicks** — integer: Số lượt nhấp.
- **CTR** — float: Tỷ lệ nhấp = Clicks / Impressions.
- **CPC** — float: Chi phí cho mỗi nhấp = Spend / Clicks.
- **Conversions** — integer: Số chuyển đổi (hành động mục tiêu đạt được).
- **CPA** — float: Chi phí cho mỗi chuyển đổi = Spend / Conversions.
- **Conversion_Rate** — float: Tỷ lệ chuyển đổi = Conversions / Clicks.
- **Duration** — integer: Số ngày chạy chiến dịch.
- **Platform** — category/string: Nền tảng quảng cáo (Facebook, Google, YouTube, Instagram, LinkedIn,...).
- **Content_Type** — category/string: Loại nội dung (Text, Image, Video, Carousel,...).
- **Target_Age** — category/string: Nhóm tuổi mục tiêu (ví dụ: 18-24, 25-34, 35-44, 55+,...).
- **Target_Gender** — category/string: Giới tính mục tiêu (Male, Female, Other).
- **Region** — category/string: Khu vực địa lý (North America, Europe, Asia, Africa, South America,...).
- **Revenue** — float: Doanh thu tạo ra từ chiến dịch.
- **Spend** — float: Chi phí thực tế đã chi.
- **ROAS** — float: Hiệu quả chi tiêu quảng cáo = Revenue / Spend.
- **Date** — date (YYYY-MM-DD): Ngày ghi nhận dữ liệu/chạy chiến dịch.
- **Impressions** — integer: Số lần hiển thị.
