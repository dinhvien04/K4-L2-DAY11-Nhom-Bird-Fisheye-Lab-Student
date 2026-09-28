# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide, **không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference ADASIND hoặc nhãn bạn vừa vẽ.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Xe cắt ngang sát cản trước, ánh sáng ngược | Méo fisheye góc rộng làm biến dạng tỷ lệ khung xe, lóa thấu kính | Giữ khung hình hình học fisheye gốc, không crop bỏ vùng viền kính | 2 người dán nhãn độc lập + 1 chuyên gia QA duyệt lại |
| rear | Đèn pha xe sau chiếu rọi đêm, vật sát cản sau | Đèn pha làm mù thấu kính, lóa sáng tạo bounding box giả | Giữ lại khu vực cản sau xe (ego body) để làm mốc phân định | Kiểm tra chéo với cảm biến siêu âm hoặc dữ liệu radar |
| left | Xe máy chen ngang vùng góc méo thấu kính | Vật thể bị kéo dãn hình học ở rìa kính, dễ sót nhãn | Giữ nguyên ma trận calibration góc méo thấu kính trái | Review mù bởi reviewer độc lập thứ 3 |
| right | Vùng giao nắp thấu kính (seam region) phải-trước | Vật thể xuất hiện đồng thời trên 2 camera tạo nhãn trùng | Đồng bộ mốc thời gian (timestamp) và không gian 3D | Đánh dấu liên kết ID đồng nhất trên cả 2 góc nhìn |

- **Khi nào cần refresh gold set (đổi camera, calibration hoặc rule)**: Cần làm mới Gold Set khi có sự thay đổi về phần cứng camera (thay thấu kính/góc đặt), khi cập nhật lại tham số hiệu chỉnh calibration, hoặc khi có sự thay đổi lớn trong bộ quy chuẩn gán nhãn (guideline patch v2.0).
- **Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box**: Phải kiểm tra trùng lặp thời điểm (timestamp sync), vị trí không gian 3D và góc nhìn tương quan giữa 2 thấu kính trước khi quyết định gộp hoặc tách 2 bounding box ở vùng giáp ranh.
- **Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera**: Việc đồng thuận trên 1 camera đơn lẻ chỉ đánh giá được góc nhìn đơn 2D, chưa phản ánh được hiện tượng chồng lấp hình ảnh ở vùng ranh giới (seam), lỗi sai số hiệu chỉnh phối cảnh BEV 360, và sự mất đồng bộ thời gian giữa các camera khác nhau trên hệ thống SVM.
