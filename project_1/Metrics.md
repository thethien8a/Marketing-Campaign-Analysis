### 1. **Chỉ số Tương tác (Engagement Metrics)**
   - **Click-Through Rate (CTR)**: Tỷ lệ nhấp chuột so với hiển thị.  
     Công thức: `CTR = Clicks / Impressions` (thường nhân 100 để ra %).  
     Ứng dụng: Phân tích hiệu quả nội dung theo Channels_Used hoặc Target_Audience.
   - **Engagement Rate**: Tỷ lệ tương tác dựa trên điểm số.  
     Công thức: `Engagement Rate = Engagement_Score / 10` (hoặc aggregate trung bình theo nhóm).  
     Ứng dụng: So sánh giữa Campaign_Type (e.g., social media vs. email).
   - **Impressions per Day**: Số hiển thị trung bình mỗi ngày.  
     Công thức: `Impressions per Day = Impressions / Duration` (Duration tính bằng ngày).  
     Ứng dụng: Xu hướng theo Date hoặc Location.

### 2. **Chỉ số Chuyển đổi và Hiệu quả (Conversion Metrics)**
   - **Conversions**: Số lượng chuyển đổi ước tính (dựa trên giả định Conversion_Rate áp dụng cho Clicks).  
     Công thức: `Conversions = Clicks * Conversion_Rate`.  
     Ứng dụng: Tổng hợp theo Company hoặc Customer_Segment (speculation: nếu dataset không có cột Conversions trực tiếp, đây là cách derive).
   - **Conversion Rate Aggregate**: Trung bình tỷ lệ chuyển đổi theo nhóm.  
     Công thức: `Avg Conversion Rate = AVG(Conversion_Rate)` (group by Target_Audience hoặc Language).  
     Ứng dụng: Xác định đối tượng hiệu quả nhất.
   - **Bounce Rate (nếu derive được)**: Tỷ lệ bỏ qua (speculation: nếu có dữ liệu bổ sung, nhưng dựa trên dataset, có thể ước tính từ low Engagement_Score).  
     Công thức: Không trực tiếp, nhưng proxy: `Bounce Rate ≈ 1 - (Clicks / Impressions)`.

### 3. **Chỉ số Chi phí và Lợi nhuận (Cost & Profit Metrics)**
   - **Cost per Click (CPC)**: Chi phí mỗi nhấp chuột.  
     Công thức: `CPC = Acquisition_Cost / Clicks`.  
     Ứng dụng: So sánh chi phí theo Channels_Used (e.g., Google Ads vs. YouTube).
   - **Cost per Acquisition (CPA)**: Chi phí mỗi chuyển đổi.  
     Công thức: `CPA = Acquisition_Cost / Conversions` (sử dụng Conversions từ trên).  
     Ứng dụng: Đánh giá hiệu quả ngân sách theo Location hoặc Campaign_Type.
   - **Cost per Impression (CPM)**: Chi phí mỗi 1000 hiển thị.  
     Công thức: `CPM = (Acquisition_Cost / Impressions) * 1000`.  
     Ứng dụng: Phân tích chi phí quảng cáo theo thời gian (Date).
   - **ROI Aggregate**: Trung bình lợi tức đầu tư.  
     Công thức: `Avg ROI = AVG(ROI)` (group by Company hoặc Duration).  
     Ứng dụng: Xếp hạng chiến dịch thành công nhất.
   - **Break-even Point**: Điểm hòa vốn (speculation: dựa trên ROI).  
     Công thức: `Break-even Acquisitions = Acquisition_Cost / (Revenue per Acquisition)` (nếu derive Revenue từ ROI).

### 4. **Chỉ số Tổng hợp và Phân khúc (Aggregate & Segmentation Metrics)**
   - **Total Spend**: Tổng chi phí.  
     Công thức: `Total Spend = SUM(Acquisition_Cost)` (group by Company hoặc Date).  
     Ứng dụng: Theo dõi ngân sách theo năm (dựa trên 2 năm dữ liệu).
   - **Campaign Efficiency Score**: Điểm hiệu quả tổng hợp (custom measure).  
     Công thức: `Efficiency Score = (ROI * Conversion_Rate) / (Acquisition_Cost / Impressions)` (normalize nếu cần).  
     Ứng dụng: Xếp hạng chiến dịch theo Customer_Segment (e.g., tech enthusiasts vs. foodies).
   - **Year-over-Year Growth**: Tăng trưởng theo năm cho bất kỳ metric (e.g., Clicks).  
     Công thức: `YoY Growth = (Current Year Metric - Previous Year Metric) / Previous Year Metric * 100` (group by Date).  
     Ứng dụng: Xu hướng theo Location hoặc Language.

### Gợi ý Phân tích Thêm (Anticipating Needs)
- **Correlation Analysis**: Tính correlation giữa ROI và Engagement_Score để tìm yếu tố ảnh hưởng (sử dụng Pandas corr()).
- **Segmentation**: Group by Target_Audience + Campaign_Type để xem metric như CTR thay đổi thế nào.
- **Time-based**: Sử dụng Date để tính rolling averages (e.g., 7-day moving average của Impressions).
- **Visualization Ideas**: Bar chart cho Avg ROI theo Location; Heatmap cho Conversion_Rate theo Channels_Used và Language.
- **Potential Derivations**: Nếu cần Revenue, speculate `Revenue = Acquisition_Cost * (1 + ROI)` (flag: dựa trên định nghĩa ROI tiêu chuẩn). 