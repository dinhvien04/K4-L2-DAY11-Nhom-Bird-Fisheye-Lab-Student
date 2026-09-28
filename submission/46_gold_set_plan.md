# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide, **không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có normal và hard slice. "Gold set" ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference ADASIND hoặc nhãn bạn vừa vẽ.

## Kế hoạch gold set theo từng camera

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Xe cắt ngang sát cản trước khi đang rẽ; ánh sáng ngược nắng trực diện | Méo fisheye góc rộng ở rìa làm biến dạng tỷ lệ khung xe, lóa thấu kính tạo bóng trắng che vật thể — tương tự lỗi MISSING quan sát ở frame `adasind_152940.jpg` R6 | Giữ ảnh fisheye gốc (không undistort), ghi rõ thông số góc mở thấu kính và vị trí lắp đặt camera | 2 annotator độc lập gán nhãn + 1 reviewer QA mù duyệt lại; bất đồng ≥ P1 cần bằng chứng ảnh |
| rear | Đèn pha xe sau chiếu rọi ban đêm; vật thể sát cản sau trong vùng mù | Đèn pha tạo flare trên thấu kính, model dễ sinh false positive ở vùng lóa sáng — tương tự pattern M_only SPURIOUS quan sát ở `adasind_152940.jpg` | Giữ metadata thời gian chụp (ngày/đêm), vùng ego_body cản sau làm mốc phân định | Kiểm tra chéo với cảm biến siêu âm/radar nếu có; nếu không, dùng 2 reviewer độc lập |
| left | Xe máy chen ngang vùng viền méo thấu kính; vật thể nhỏ ở rìa kính | Vật thể bị kéo dãn hình học ở edge zone, dễ sót nhãn hoặc sai class — tương tự lỗi WRONG_CLASS ở edge zone trong `zone_table.md` | Giữ nguyên ma trận calibration góc méo thấu kính trái, không crop bỏ vùng viền | Reviewer độc lập thứ 3 kiểm mù; đối chiếu với annotations từ camera right ở vùng seam chồng lấp |
| right | Vùng giao nắp thấu kính (seam region) phải-trước; vật thể đồng thời trên 2 camera | Vật thể xuất hiện trên 2 góc nhìn tạo nguy cơ gán trùng hoặc lệch ID — bài học từ ca escalate `adasind_167700.jpg` L8+M8 `LM_noR` | Đồng bộ mốc thời gian (timestamp) giữa camera right và front; giữ không gian 3D gốc | Đánh dấu liên kết ID đồng nhất trên cả 2 góc nhìn; cần policy seam trước khi gọi là gold |

## Khi nào cần refresh gold set

Cần làm mới Gold Set khi:
1. **Thay đổi phần cứng camera:** thay thấu kính, đổi góc đặt, hoặc di chuyển vị trí lắp đặt trên xe
2. **Cập nhật calibration:** thay đổi ma trận hiệu chỉnh méo thấu kính (distortion matrix)
3. **Thay đổi lớn trong guideline:** ví dụ thêm rule v1.1.0 về seam region (xem `20_guideline_patch.md`)
4. **Phát hiện drift:** khi quality report trên frame mới cho thấy recall/precision giảm > 10% so với gold set hiện tại

## Ca seam cần policy trước khi ghép box

Phải kiểm tra trước khi quyết định gộp hoặc tách 2 bounding box ở vùng giáp ranh:
1. **Timestamp sync:** Hai frame từ 2 camera phải cùng thời điểm chụp (sai số ≤ 50ms)
2. **Projection 3D:** Chuyển đổi tọa độ box từ ảnh 2D sang không gian 3D bằng calibration matrix, kiểm tra khoảng cách 3D giữa 2 box < ngưỡng cho phép
3. **Evidence:** Lưu cặp ảnh crop vùng seam từ cả 2 camera, ghi rõ quyết định gộp/tách và lý do

## Vì sao peer agreement trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera

Việc đồng thuận trên 1 camera đơn lẻ chỉ đánh giá được góc nhìn 2D riêng lẻ, chưa phản ánh được:
- Hiện tượng chồng lấp hình ảnh ở vùng ranh giới seam giữa các camera
- Lỗi sai số hiệu chỉnh phối cảnh BEV 360 khi ghép 4 góc nhìn
- Sự mất đồng bộ thời gian giữa các camera khác nhau trên hệ thống SVM
- Sự khác biệt về điều kiện chiếu sáng/biến dạng giữa front/rear/left/right
