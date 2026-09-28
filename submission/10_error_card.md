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

- **Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy**:
  - **SPURIOUS ở edge (6 ca):** Phần lớn là model YOLO26m dự đoán thừa box ở vùng rìa thấu kính fisheye, nơi biến dạng hình học cao — ví dụ frame `adasind_152940.jpg` có 5 box M_only (M1, M3, M4, M7, M8) đều là `E4_model_domain`. Model chưa được huấn luyện với dữ liệu fisheye biến dạng nên sinh nhiều false positive ở vùng viền kính.
  - **MISSING ở center (3 ca):** Người gán nhãn (L) bỏ sót đối tượng mà reference (R) có — ví dụ frame `adasind_152940.jpg` / R6 là `R_only` + `E1_annotator_error`, và frame `adasind_167700.jpg` / R4+M4 là `RM_noL` → annotator thiếu chú ý ở vùng trung tâm khi có nhiều đối tượng chồng chéo.
  - **WRONG_CLASS ở edge (2 ca):** Frame `adasind_167700.jpg` / L7+R4 và L8+R6 bị gán sai class, nguyên nhân là hình dạng vật thể bị méo ở rìa fisheye khiến khó phân biệt Bike vs Pedestrian.

- **Cách sửa và ai nhận việc (`owner`)**:
  - `annotator` (8 ca rework): Kiểm tra lại từng frame, bổ sung box thiếu (MISSING), xóa box thừa (SPURIOUS do L) và sửa class (WRONG_CLASS). Đặc biệt chú ý vùng edge khi vẽ.
  - `ai_team` (7 ca keep_with_reason): Các box M_only SPURIOUS cho thấy model cần fine-tune với dữ liệu fisheye; hiện tại giữ nguyên nhãn người vì model chưa đáng tin ở vùng biến dạng.
  - `data_ops` (1 ca escalate): Frame `adasind_167700.jpg` / L8+M8 có cả L và M thấy nhưng R không thấy → cần kiểm tra lại chất lượng reference tại đây.

- **Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule)**: Dòng r3_diag trong findings.csv (16 dòng) có đầy đủ frame/object_ref/cell/evidence. Ảnh minh chứng tại `screenshots/`. Báo cáo overlay: `r1_craft/compare.html`, `r3_diag/model_compare.html`.

