# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| `adasind_167700.jpg` | 5 ca (WRONG_CLASS, SPURIOUS) | Có tỷ lệ gán nhầm nhãn class cao nhất ở vùng viền thấu kính edge zone | Ảnh overlay `compare.html` và dòng findings r1_craft |
| `adasind_152940.jpg` | 3 ca (ATTRIBUTE, MISSING) | Xuất hiện lỗi thiếu thuộc tính occluded khi xe bị che khuất | Ảnh chụp màn hình `screenshots/r2_l1.png` và log QA |

Giới hạn của kết luận từ ba frame ADASIND: Bộ dữ liệu 3 frame có dung lượng quá nhỏ, chưa đại diện cho các điều kiện thời tiết (mưa, sương mù) và thời điểm ban đêm với ánh sáng phức tạp.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: Cần đảm bảo phân bổ đều 200 frame theo các khoảng thời gian cách biệt (time-step sampling ≥ 2 giây) để tránh trùng lặp bối cảnh. Kế hoạch này giúp lọc ra các ca biên rủi ro cao (hard case) để kiểm chứng, chứ không phải tập mẫu ngẫu nhiên để đo tổng tỷ lệ lỗi của toàn hệ thống 50.000 frame.
