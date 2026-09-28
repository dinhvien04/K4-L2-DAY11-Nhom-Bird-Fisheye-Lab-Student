# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| `adasind_167700.jpg` (mid/edge zone) | 7 ca: 2 WRONG_CLASS, 2 SPURIOUS, 2 MISSING, 1 ATTRIBUTE | Tập trung nhiều loại lỗi nhất trong 3 frame, đặc biệt WRONG_CLASS ở edge zone (L7+R4, L8+R6) — chỉ ra khó khăn phân biệt class ở vùng biến dạng fisheye | Overlay `compare.html` frame 2, dòng r1_craft + r3_diag trong `findings.csv`, `zone_table.md` edge zone |
| `adasind_152940.jpg` (center/edge zone) | 8 ca: 5 M_only SPURIOUS, 1 R_only MISSING, 2 LR_noM MISSING | Model YOLO26m dự đoán thừa nhiều nhất ở frame này (5 box M_only) → chỉ ra model domain gap với fisheye. Đồng thời annotator bỏ sót R6 (`E1_annotator_error`) | Overlay `model_compare.html` frame 1, dòng r3_diag `M1/M3/M4/M7/M8` và `R6` |

**Giới hạn của kết luận từ ba frame ADASIND:** Bộ dữ liệu 3 frame chưa đại diện cho các điều kiện thời tiết (mưa, sương mù), thời điểm ban đêm, hoặc mật độ giao thông cao. Các kết luận về class yếu và vùng lỗi chỉ áp dụng cho mẫu quan sát được, chưa suy rộng cho cả hệ SVM 4 camera.

## Chuyển sang kế hoạch bốn camera giả lập

**Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv`:** Phân bổ 200 frame theo 4 camera × 2 loại (normal/hard) với khoảng cách lấy mẫu ≥ 2 giây giữa các frame liền kề để tránh đếm nhiều frame cùng cảnh như nhiều ca độc lập. Kiểm tra mỗi camera có cả hard case (lóa sáng, seam, vật thể nhỏ ở rìa) và normal case.

**Vì sao kế hoạch lấy mẫu chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi:** 200 frame trên 50.000 là tỷ lệ 0,4% — chưa đủ cho ước lượng thống kê đáng tin cậy về tỷ lệ lỗi tổng thể. Kế hoạch này hướng tới phát hiện các loại lỗi phổ biến và ca biên rủi ro cao (hard case) để ưu tiên review, không phải tập mẫu ngẫu nhiên để đo tổng tỷ lệ lỗi của toàn hệ thống.
