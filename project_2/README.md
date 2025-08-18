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

#### 📊 KPI CARDS (Luôn đặt ở đầu dashboard):
- **Total Revenue by Channel** (với % change vs previous period)
- **Average ROAS by Platform** (với trend indicator ↗️↘️)
- **Best Performing Content Type** (ROAS cao nhất + volume)
- **Channel Efficiency Score** (weighted ROAS × Volume)
- **Content Engagement Rate** (CTR × Conversion Rate combined)

#### 🎯 BIỂU ĐỒ QUAN TRỌNG NHẤT (Ấn tượng với nhà tuyển dụng):

**1. Performance Matrix Heatmap** (⭐⭐⭐⭐⭐)
- **Mục đích:** So sánh ROAS và CPM theo Platform × Content_Type
- **Tại sao quan trọng:** Một cái nhìn duy nhất cho thấy "sweet spot" (kênh + nội dung hiệu quả nhất)
- **Ấn tượng với NTD:** Thể hiện khả năng tổng hợp complex data thành actionable insights
- **Code:** Heatmap với Platform (rows) × Content_Type (cols), color = ROAS, annotation = CPM values

**2. Channel Efficiency Bubble Chart** (⭐⭐⭐⭐⭐)
- **Mục đích:** x = Spend, y = ROAS, size = Revenue, color = Platform
- **Tại sao quan trọng:** Định vị kênh nào "đáng đồng tiền bát gạo" và scale được
- **Ấn tượng với NTD:** Hiểu portfolio management và risk-return trong marketing
- **Code:** Scatter với quadrant lines (ROAS = avg, Spend = median) để phân vùng

**3. Marketing Funnel Sankey** (⭐⭐⭐⭐)
- **Mục đích:** Flow Impressions → Clicks → Conversions theo Platform
- **Tại sao quan trọng:** Thấy "leak" ở đâu trong customer journey
- **Ấn tượng với NTD:** Hiểu full-funnel marketing, không chỉ bottom-line metrics
- **Code:** Sankey với drop-off rates annotated, filter theo Content_Type

**4. ROI Decomposition Tree** (⭐⭐⭐⭐)
- **Mục đích:** ROAS = (Revenue/Conversions) × (Conversions/Clicks) × (Clicks/Spend)
- **Tại sao quan trọng:** Hiểu driver nào kéo ROAS (value per conversion vs conversion rate vs cost efficiency)
- **Ấn tượng với NTD:** Advanced analytics thinking - decompose metrics để optimize từng lever
- **Code:** Waterfall chart hoặc nested bar chart theo Platform

**5. Content Performance Leaderboard** (⭐⭐⭐)
- **Mục đích:** Top 10 campaigns theo ROAS với supporting metrics (Spend, Revenue, Duration)
- **Tại sao quan trọng:** Marketers cần biết creative nào work để replicate
- **Ấn tượng với NTD:** Business-focused presentation
- **Code:** Interactive table với conditional formatting và drill-down

#### 💡 Key Metrics để tính:
- **ROAS, CPA, CTR, CPM** (cơ bản)
- **Revenue per Click = Revenue/Clicks** (advanced)
- **Funnel Drop-off Rate = 1 - Conversion_Rate** (advanced)
- **Platform Share of Voice = Impressions_platform / Total_Impressions** (strategic)

---

### Dashboard 3: Phân tích Chân dung Khách hàng (Customer Persona Analysis)
*   **Mục tiêu:** Hiểu rõ khách hàng mục tiêu là ai và họ ở đâu.
*   **Đối tượng sử dụng:** Trưởng phòng Marketing, Đội ngũ Sáng tạo Nội dung (Content Team), Chuyên viên quảng cáo.
*   **Câu hỏi trả lời:** "Ai là khách hàng giá trị nhất của chúng ta?"

#### 📊 KPI CARDS (Luôn đặt ở đầu dashboard):
- **Highest Value Persona** (Age×Gender với CLV cao nhất)
- **Most Profitable Region** (Revenue - Spend, với growth rate)
- **Customer Acquisition Cost by Segment** (CPA trung bình theo persona)
- **Geographic Revenue Distribution** (Top 3 regions % contribution)
- **Persona Conversion Efficiency** (Best performing Age×Gender combo)

#### 🎯 BIỂU ĐỒ QUAN TRỌNG NHẤT (Ấn tượng với nhà tuyển dụng):

**1. Customer Value Matrix** (⭐⭐⭐⭐⭐)
- **Mục đích:** Heatmap ROAS theo Age_Group × Gender, với bubble size = Revenue
- **Tại sao quan trọng:** Identify "golden personas" - segment có ROI cao nhất
- **Ấn tượng với NTD:** Hiểu customer segmentation và value-based targeting
- **Code:** Heatmap với annotation số liệu Revenue, filter theo Region/Platform

**2. Geographic Revenue Map** (⭐⭐⭐⭐⭐)
- **Mục đích:** Choropleth map Revenue theo Region, với overlay CPA bubbles
- **Tại sao quan trọng:** Geo-targeting strategy - biết đầu tư vào market nào
- **Ấn tượng với NTD:** Spatial analytics và international marketing thinking
- **Code:** Map với color scale = Revenue, bubble size = Total Spend, hover = ROAS

**3. Persona Profitability Radar** (⭐⭐⭐⭐)
- **Mục đích:** So sánh Top 5 personas trên 6 metrics: ROAS, Revenue, CLV, Conversion Rate, Volume, Efficiency
- **Tại sao quan trọng:** Multi-dimensional comparison để chọn target persona
- **Ấn tượng với NTD:** Advanced visualization và holistic thinking
- **Code:** Radar chart với personas khác màu, metrics normalized 0-10

**4. Customer Journey Cohort** (⭐⭐⭐⭐)
- **Mục đích:** Heatmap retention ROAS theo Date × Persona, thấy persona nào "bền"
- **Tại sao quan trọng:** Hiểu lifetime value và churn patterns
- **Ấn tượng với NTD:** Cohort analysis - advanced marketing analytics skill
- **Code:** Cohort table với color gradient, group by Age/Gender

**5. Persona Performance Leaderboard** (⭐⭐⭐)
- **Mục đích:** Top 10 Age×Gender×Region combinations theo CLV
- **Tại sao quan trọng:** Actionable list để focus marketing efforts
- **Ấn tượng với NTD:** Business-ready recommendations
- **Code:** Table với CLV, Revenue, CPA, Volume, và "Opportunity Score"

#### 💡 Key Metrics để tính:
- **Customer Lifetime Value (CLV) = (Revenue/Conversions) × Average Duration**
- **Persona Profitability = Revenue - Spend** (per segment)
- **Market Penetration = Conversions_segment / Total_Conversions** (% share)
- **Efficiency Score = ROAS × Conversion_Rate** (combined effectiveness)

---

### Dashboard 4: Phân tích Ngân sách & Thời gian (Budget & Duration Analysis)
*   **Mục tiêu:** Đánh giá mối quan hệ giữa chi tiêu, thời gian và hiệu quả.
*   **Đối tượng sử dụng:** Trưởng phòng Marketing, Chuyên viên Lập kế hoạch (Media Planners).
*   **Câu hỏi trả lời:** "Chi tiêu bao nhiêu và trong bao lâu là tối ưu?"

#### 📊 KPI CARDS (Luôn đặt ở đầu dashboard):
- **Total Marketing Spend** (vs Budget, với pacing %)
- **Average Campaign Duration** (optimal vs actual, với efficiency score)
- **Break-even Spend Threshold** (ROAS = 1 point)
- **Budget Utilization Rate** (Spend/Budget across all campaigns)
- **ROI Forecast Next Period** (dựa trên current trends)

#### 🎯 BIỂU ĐỒ QUAN TRỌNG NHẤT (Ấn tượng với nhà tuyển dụng):

**1. ROI vs Investment Scatter** (⭐⭐⭐⭐⭐)
- **Mục đích:** x = Spend, y = ROAS, size = Revenue, color = Platform, với regression line
- **Tại sao quan trọng:** Thấy "sweet spot" của investment - không phải càng chi nhiều càng tốt
- **Ấn tượng với NTD:** Hiểu diminishing returns và portfolio optimization
- **Code:** Scatter với quadrants (High Spend/High ROAS, etc.), annotation break-even line

**2. Campaign Duration Efficiency** (⭐⭐⭐⭐⭐)
- **Mục đích:** Line chart ROAS vs Duration với trend line, group by Platform
- **Tại sao quan trọng:** Timing strategy - campaigns dài có hiệu quả hơn không?
- **Ấn tượng với NTD:** Media planning expertise và temporal optimization
- **Code:** Multi-line với confidence intervals, annotation optimal duration ranges

**3. Budget Allocation Treemap** (⭐⭐⭐⭐)
- **Mục đích:** Hierarchy Platform → Content_Type, size = Spend, color = ROAS
- **Tại sao quan trọng:** Portfolio view - thấy ngân sách phân bổ và hiệu quả tương ứng
- **Ấn tượng với NTD:** Strategic thinking và resource allocation
- **Code:** Treemap với hover showing ROI, Profit, và recommendations

**4. Pacing & Performance Dashboard** (⭐⭐⭐⭐)
- **Mục đích:** Gauge charts cho Budget Utilization, với alert zones (under/over-paced)
- **Tại sao quan trọng:** Real-time campaign management - biết khi nào cần adjust
- **Ấn tượng với NTD:** Operational excellence và monitoring skills
- **Code:** Multiple gauges với color zones, table campaigns cần attention

**5. Forecast & Scenario Planner** (⭐⭐⭐⭐⭐)
- **Mục đích:** Interactive sliders để forecast Revenue nếu thay đổi Budget/Duration
- **Tại sao quan trọng:** Predictive analytics cho planning - "What if we spend X more?"
- **Ấn tượng với NTD:** Advanced analytics và business planning capability
- **Code:** Plotly với callbacks, regression model để predict, sensitivity analysis

#### 💡 Key Metrics để tính:
- **Budget Pacing = (Spend/Budget) × 100%** (campaign health)
- **Daily Efficiency = Revenue/Duration** (time-normalized performance)  
- **Break-even Spend = Budget where ROAS = 1** (risk threshold)
- **ROI Elasticity = % change ROAS / % change Spend** (sensitivity)

---

## 🚀 Tổng kết: Tại sao các Dashboard này sẽ gây ấn tượng

### Với Marketing Managers:
- **Dashboard 2:** Hiểu channel mix optimization và content strategy
- **Dashboard 3:** Customer-centric thinking và persona-based targeting  
- **Dashboard 4:** Budget management và ROI forecasting

### Với Nhà tuyển dụng (Technical):
- **Advanced Visualizations:** Sankey, Heatmaps, Radar, Treemaps - không phải basic bar charts
- **Statistical Thinking:** Regression, correlation, cohort analysis, forecasting
- **Interactive Elements:** Filters, sliders, drill-downs - modern BI approach

### Với Nhà tuyển dụng (Business):
- **Actionable Insights:** Mỗi chart đều có business recommendation cụ thể
- **Strategic Thinking:** Portfolio optimization, customer segmentation, media planning
- **ROI Focus:** Tất cả đều hướng về tăng profits và optimize spending

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
