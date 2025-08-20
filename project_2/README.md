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
**Objective:** So sánh hiệu quả giữa các kênh (Platform) và loại nội dung (Content_Type) để tối ưu phân bổ ngân sách & sáng tạo.

**Primary Users:** Marketing Team, Ad Specialists.

**Key Business Questions:**
1. Kênh + loại nội dung nào mang lại ROAS cao và CPM thấp nhất (sweet spot)?
2. Nên scale ngân sách ở đâu và giảm ở đâu (hiệu quả thấp / chi phí cao)?
3. Funnel bị rò rỉ ở giai đoạn nào theo từng platform?
4. Yếu tố nào kéo ROAS: giá trị trên mỗi conversion, conversion rate hay cost efficiency?

**Priority Legend:**
- P1 (⭐⭐⭐⭐⭐) = Critical driver / phải xây trước
- P2 (⭐⭐⭐⭐) = High impact / triển khai sau P1
- P3 (⭐⭐⭐) = Support / bổ sung chiều sâu

#### 📊 KPI Layer (Top Cards)
| KPI | Mục đích | Định nghĩa ngắn | So sánh |
| --- | --- | --- | --- |
| Total Revenue by Channel | Quy mô giá trị | Sum(Revenue) group Platform | vs prev period (%) |
| Avg ROAS by Platform | Hiệu quả tổng hợp | Revenue / Spend (weighted) | trend (7d / 30d) |
| Best Performing Content Type | Creative hiệu quả | Max ROAS (Content_Type) + Volume | rank change |
| Channel Efficiency Score | Ưu tiên ngân sách | Weighted_ROAS = Σ(ROAS_i*Spend_i)/Σ(Spend_i) | vs overall |
| Content Engagement Rate | Chất lượng traffic | CTR * Conversion_Rate | vs median |

#### 🎯 Key Visuals (with Data Needs, Insight, Action)

**P1. Performance Matrix Heatmap (Platform × Content_Type)**
- Data Needs: Platform, Content_Type, Spend, Revenue, Impressions
- Metrics: ROAS, CPM = Spend / (Impressions/1000)
- Expected Insight: Nhận diện cluster High ROAS + Low CPM → ưu tiên scale
- Action Rule: Nếu ROAS > (median + 1 SD) & CPM < median ⇒ tăng ngân sách 10–25%
- Visualization: Heatmap color=ROAS (diverging), annotation=CPM (k format), optional tooltip Spend, Revenue

**P1. Channel Efficiency Bubble Chart**
- Data Needs: Platform, Spend, Revenue, Conversions (optional for CPA), ROAS
- Axes: x=Spend, y=ROAS, size=Revenue, color=Platform
- Insight: Phân loại 4 vùng: High Spend/Low ROAS (Optimize), Low Spend/High ROAS (Scale), High/High (Monitor), Low/Low (Deprioritize)
- Action Rule: Low Spend/High ROAS ⇒ Test tăng ngân sách theo bậc 10% → 20% → 30%
- Overlay: Lines: Spend=median, ROAS=avg

**P2. Marketing Funnel Sankey**
- Data Needs: Platform, Impressions, Clicks, Conversions
- Derived: CTR = Clicks/Impressions; Conversion_Rate = Conversions/Clicks; Drop-off stages
- Insight: Stage với drop-off > (median + 15pp) cần tối ưu (creative, landing, offer)
- Action Rule: Nếu CTR thấp (<pct threshold) nhưng Conversion_Rate cao ⇒ cần cải thiện creative/ad copy; ngược lại xem xét UX landing page

**P2. ROI Decomposition Tree**
- Identity: ROAS = (Revenue/Conversions) × (Conversions/Clicks) × (Clicks/Spend)
- Labels: Value_per_Conversion, Conversion_Rate, Click_Through_Efficiency
- Insight: Segment yếu nhất → ưu tiên A/B test tương ứng
- Action Rule: Driver thấp hơn 20% so với median driver toàn bộ ⇒ tạo backlog tối ưu riêng

**P3. Content Performance Leaderboard**
- Data Needs: Campaign_ID, Content_Type, Platform, Spend, Revenue, Duration, Conversions
- Columns: ROAS, Spend, Revenue, CPA, Duration, Opportunity_Score (see metric dictionary)
- Insight: Xếp hạng top creative để replicate hoặc scale
- Action Rule: Campaign có Opportunity_Score top quintile nhưng Spend dưới median ⇒ cân nhắc increase spend

#### Supporting Computations
- Revenue per Click = Revenue/Clicks
- Funnel Drop-off Rate = 1 - Conversion_Rate
- Platform Share of Voice = Impressions_platform / Total_Impressions

#### Data Quality / Feasibility Notes
- Cần đảm bảo không chia cho 0 (Spend=0, Clicks=0, Impressions=0)
- Chuẩn hoá rolling windows: 7d & 30d
- Outlier spend (> Q3 + 1.5*IQR) có thể distort median line scatter → cân nhắc winsorize

#### Action Playbook (Examples)
| Tình huống | Diễn giải | Hành động đề xuất |
|------------|-----------|-------------------|
| High ROAS + Low Spend | Cơ hội scale | Tăng ngân sách từng bước 10–20% và theo dõi ROAS giữ > 90% baseline |
| Low ROAS + High Spend | Lãng phí | Freeze incremental spend, audit creative & targeting |
| High CTR, Low Conversion_Rate | Landing issue | Kiểm tra tốc độ trang, form friction, message mismatch |
| Low CTR, High Conversion_Rate | Ad hook yếu | Tối ưu creative, headline, audience relevance |

---

---

### Dashboard 3: Phân tích Chân dung Khách hàng (Customer Persona Analysis)
**Objective:** Xác định phân khúc khách hàng có giá trị & hiệu quả cao nhất để tối ưu targeting và ngân sách.

**Primary Users:** Marketing Manager, Content Team, Ad Optimization.

**Key Business Questions:**
1. Persona (Age × Gender × Region) nào tạo nhiều giá trị / lợi nhuận nhất?
2. Chênh lệch hiệu suất giữa các vùng địa lý ảnh hưởng ngân sách thế nào?
3. Có persona nào đang under-invested (ROAS cao nhưng share thấp)?
4. Retention / giá trị dài hạn thay đổi thế nào theo cohort thời gian bắt đầu?

#### 📊 KPI Layer
| KPI | Purpose | Definition | Comparison |
|-----|---------|------------|------------|
| Highest Value Persona | Focus segment | Max CLV persona | vs #2 difference |
| Most Profitable Region | Geo allocation | (Revenue - Spend) by Region | QoQ / MoM |
| Avg CPA by Persona | Efficiency | Spend / Conversions | vs overall CPA |
| Geographic Revenue Distribution | Concentration | Top 3 Regions % Revenue | 80/20 ratio |
| Persona Conversion Efficiency | Funnel quality | Conversion_Rate * ROAS (normalized) | vs median |

#### Key Visuals
**P1. Customer Value Matrix (Heatmap)**
- Data Needs: Age_Group (Target_Age), Target_Gender, Revenue, Spend, Conversions
- Metrics: ROAS, Revenue share
- Insight: Identify \"golden personas\"
- Action: Persona ROAS > (overall + 15%) nhưng Spend share < 0.5 * Revenue share ⇒ tăng phân bổ

**P1. Geographic Revenue Map**
- Data Needs: Region, Revenue, Spend, Conversions
- Overlay: Bubble size = Spend, color = Revenue, hover = ROAS & CPA
- Action: Region CPA > (overall + 20%) và ROAS < 0.9 * overall ⇒ audit targeting

**P2. Persona Profitability Radar**
- Data Needs: Top 5 personas (theo CLV)
- Metrics (normalized 0–10): ROAS, Revenue, CLV, Conversion_Rate, Volume (Conversions), Efficiency_Score
- Insight: Persona với trục yếu nhất xác định điểm cải thiện rõ ràng

**P2. Customer Journey Cohort**
- Cohort Definition: Week of first conversion
- Metric: Cumulative ROAS / Retention (% conversions continuing)
- Action: Nếu Cohort tuần gần đây retention giảm >10pp so với median 8 tuần ⇒ xem xét fatigue / creative refresh

**P3. Persona Performance Leaderboard**
- Data Needs: Age × Gender × Region
- Columns: CLV, ROAS, CPA, Revenue, Spend, Opportunity_Score
- Opportunity_Score: (ROAS_index * Revenue_share_index) / Investment_share_index

#### Supporting Metrics
- CLV (simple proxy) = (Revenue / Conversions) * Average Duration (nếu Duration đại diện lifetime) OR mark as proxy
- Persona Profitability = Revenue - Spend
- Market Penetration = Conversions_segment / Total_Conversions
- Efficiency Score = ROAS * Conversion_Rate

#### Action Playbook (Examples)
| Situation | Indicator | Suggested Action |
|----------|-----------|------------------|
| High CLV, Low Spend Share | Spend Share < 0.5 * Revenue Share | Reallocate + incremental budget tests |
| High CPA, Normal CTR | CPA > 120% overall; CTR within 5% range | Optimize mid-funnel (landing, offer) |
| Low CTR, High Conversion_Rate | CTR < p25; Conversion_Rate > p75 | Creative & audience A/B test |
| Declining Retention Cohorts | Retention Week2 drop >10pp | Lifecycle nurture refinement |

---

---

### Dashboard 4: Phân tích Ngân sách & Thời gian (Budget & Duration Analysis)
**Objective:** Xác định mức chi & độ dài chiến dịch tối ưu để đạt ROI cao và tránh diminishing returns.

**Primary Users:** Marketing Manager, Media Planners, Finance Liaison.

**Key Business Questions:**
1. Ngân sách hiện tại được phân bổ có cân đối hiệu suất không?
2. Điểm hòa vốn (ROAS=1) và khu vực diminishing returns xuất hiện ở đâu?
3. Chiến dịch dài hơn có cải thiện hay làm xấu hiệu quả?
4. Dự báo ROI nếu điều chỉnh ngân sách / thời lượng?

#### 📊 KPI Layer
| KPI | Purpose | Definition | Comparison |
|-----|---------|------------|------------|
| Total Marketing Spend | Tổng mức đầu tư | Sum(Spend) | vs Budget target |
| Budget Utilization Rate | Pacing | Spend / Budget | pacing % vs plan |
| Average Campaign Duration | Chiều dài trung bình | Mean(Duration) | vs optimal band |
| Break-even Spend Threshold | Rủi ro lỗ | Spend level where ROAS=1 | track trend |
| ROI Forecast Next Period | Kỳ vọng | Model-based projected ROAS | vs current |

#### Key Visuals
**P1. ROI vs Investment Scatter**
- Data Needs: Campaign_ID, Spend, Revenue, Platform
- Add regression (log or piecewise) để thấy diminishing returns
- Quadrants: Annotate counts & Spend share
- Action: Campaign ở High Spend / Low ROAS ⇒ review or cut 10–30%

**P1. Campaign Duration Efficiency (Line / Spline)**
- Data Needs: Duration, ROAS, Platform
- Add smoothing + confidence interval
- Insight: Optimal duration range (plateau zone)
- Action: Nếu Duration > optimal_high & ROAS giảm >10% từ peak ⇒ sunset candidate

**P2. Budget Allocation Treemap**
- Hierarchy: Platform → Content_Type
- Size=Spend, Color=ROAS (diverging with neutral at ROAS=1)
- Action: Mảng Spend >15% tổng nhưng ROAS < 0.9 overall ⇒ reallocate thử 5–10%

**P2. Pacing & Performance Gauges**
- Metrics: Budget Utilization %, Forecast vs Plan %, Underspend/ Overspend flags
- Action: Pacing < 90% mid-period ⇒ accelerate spend / add campaigns

**P1. Forecast & Scenario Planner**
- Model: Simple ElasticNet or Gradient Boosting using Spend, Duration, Platform, Content_Type dummies
- Interactive: Sliders ± X% Budget; output projected Revenue, ROAS
- Action: Chỉ commit scale nếu projected ROAS giữ > 95% hiện tại

#### Supporting Metrics
- Budget Pacing = Spend / Budget
- Daily Efficiency = Revenue / Duration
- Break-even Spend: Solve Spend where ROAS = 1 (or find nearest actual)
- ROI Elasticity = %ΔROAS / %ΔSpend (rolling window)

#### Action Playbook
| Scenario | Indicator | Action |
|----------|-----------|--------|
| Overspend & Underperform | Pacing >105%, ROAS <0.9 target | Freeze marginal spend, audit cost drivers |
| Underspend & High Efficiency | Pacing <90%, ROAS >1.15 target | Controlled scale sequence (add +10% cycles) |
| Long Tail Inefficient | Campaign age > optimal & ROAS decay | Sunset or refresh creative |
| Sharp Elasticity Decline | Elasticity <0 after scale | Stop scaling; test new segments |

---

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
 
### Trường dẫn xuất (Derived Fields)
- **ROAS** (nếu không có sẵn) = Revenue / Spend
- **CPA** (nếu cần tái tính) = Spend / Conversions
- **CTR** = Clicks / Impressions
- **Conversion_Rate** = Conversions / Clicks
- **CPM** = Spend / (Impressions/1000)
- **Revenue_per_Click** = Revenue / Clicks
- **Drop_Off_Clicks** = 1 - CTR (biểu diễn tỷ lệ bỏ qua sau impression)
- **Drop_Off_Conversion** = 1 - Conversion_Rate
- **Weighted_ROAS (Channel Efficiency)** = Σ(ROAS_i * Spend_i)/Σ(Spend_i)
- **Opportunity_Score** (leaderboard) = (ROAS_index * Revenue_share_index) / Spend_share_index (chuẩn hoá indices quanh 1)
- **Efficiency_Score** = ROAS * Conversion_Rate (scale/normalize để so sánh)
- **CLV (proxy)** = (Revenue / Conversions) * Average Duration (hoặc giả định 1 chu kỳ nếu thiếu)

### Data Gaps & Assumptions
| Yếu tố | Trạng thái | Giả định / Hành động |
|--------|-----------|----------------------|
| Age / Gender / Region | Cần kiểm tra đủ độ phủ | Nếu thiếu nhiều (>30%) ⇒ hạn chế Persona dashboard hoặc tạo bucket "Unknown" |
| Budget (kế hoạch) | Có thể khác Spend | Nếu không có cột Budget ⇒ tạo giả định = historical avg Spend * factor |
| Duration | Nếu chỉ có Start/End | Tính Duration = (End - Start).days + 1 |
| Impressions outliers | Có thể skew CTR | Winsorize p1–p99 hoặc log-scale trong phân tích |
| Revenue attribution lag | Delay ghi nhận | Ghi chú độ trễ nếu forecasting ngắn hạn |
| Missing Spend=0 & Revenue>0 | Có khả năng attribution khác kênh | Flag validation trước khi tính ROAS |

### Metric Dictionary (Consolidated)
| Metric | Formula | Notes |
|--------|---------|-------|
| ROAS | Revenue / Spend | Guard: Spend>0 |
| CPA | Spend / Conversions | Guard: Conversions>0 |
| CTR | Clicks / Impressions | Guard: Impressions>0 |
| Conversion_Rate | Conversions / Clicks | Guard: Clicks>0 |
| CPM | Spend / (Impressions/1000) | Rounded to 2 decimals |
| Revenue_per_Click | Revenue / Clicks | Performance value proxy |
| Funnel Drop-off Rate | 1 - Conversion_Rate | Stage efficiency |
| Share of Voice | Impressions_platform / Total_Impressions | Platform mix |
| Weighted_ROAS | Σ(ROAS_i * Spend_i)/Σ Spend_i | Spend-weighted effectiveness |
| Efficiency_Score | ROAS * Conversion_Rate | Normalize 0–1 or 0–10 |
| Opportunity_Score | (ROAS_idx * Revenue_share_idx)/Spend_share_idx | idx = metric / overall |
| Budget Pacing | Spend / Budget | Track vs plan |
| Daily Efficiency | Revenue / Duration | Time-normalized |
| ROI Elasticity | %ΔROAS / %ΔSpend | Rolling window (e.g. 14d) |
| CLV (proxy) | (Revenue / Conversions) * Avg Duration | Simplified estimate |

---
