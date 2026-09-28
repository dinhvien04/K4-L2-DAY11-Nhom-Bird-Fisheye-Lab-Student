# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B3 | ATTRIBUTE | 1 |
| center | B3 | MISSING | 3 |
| center | B3 | SPURIOUS | 4 |
| center | B3 | WRONG_CLASS | 1 |
| center | C0 | SPURIOUS | 1 |
| edge | B3 | IGNORE_SCOPE | 2 |
| edge | B3 | MISSING | 2 |
| edge | B3 | SPURIOUS | 6 |
| edge | B3 | WRONG_CLASS | 2 |
| edge | C0 | SPURIOUS | 1 |
| mid | B3 | ATTRIBUTE | 1 |
| mid | B3 | IGNORE_SCOPE | 1 |
| mid | B3 | MISSING | 3 |
| mid | B3 | SPURIOUS | 2 |
| unknown | B4 | LOOSE_BOX | 1 |
| unknown | B4 | MISSING_IGNORE | 1 |
| unknown | B4 | MISSING_OCCLUDED | 1 |

## Top defects
- SPURIOUS: 14 (ví dụ frame adasind_019560.jpg)
- MISSING: 8 (ví dụ frame adasind_152940.jpg)
- IGNORE_SCOPE: 3 (ví dụ frame adasind_152940.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- **Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy**: Lỗi SPURIOUS và MISSING xảy ra chủ yếu ở vùng thấu kính fisheye biến dạng `edge` zone do hiện tượng lóa sáng và nhiễu viền bóng râm làm mô hình AI dự đoán thừa/sót box. Đồng thời người gán nhãn bỏ sót các thuộc tính `occluded` khi đối tượng bị xe khác che một phần.
- **Cách sửa và ai nhận việc (`owner`)**:
  - `annotator`: Thực hiện gán nhãn bổ sung thuộc tính `occluded` và chỉnh sửa các ô box ôm sát vật thể ở bước Rework.
  - `ai_team`: Điều chỉnh ngưỡng tự tin (confidence threshold) và tập huấn luyện mô hình với ma trận nắn méo thấu kính fisheye.
- **Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule)**: Minh chứng tại dòng `r2_qa` frame `adasind_271039.jpg` (L1, L2), ảnh bằng chứng `screenshots/r2_l1.png` tuân theo quy tắc R01 và R04.
