# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B4 | MISSING | 1 |
| center | B4 | SPURIOUS | 5 |
| center | C0 | MISSING | 2 |
| edge | B4 | SPURIOUS | 1 |
| edge | C0 | MISSING | 1 |
| mid | B4 | MISSING | 8 |
| mid | B4 | SPURIOUS | 8 |
| mid | C0 | MISSING | 2 |

## Top defects
- SPURIOUS: 14 (ví dụ frame adasind_249480.jpg)
- MISSING: 14 (ví dụ frame adasind_261480.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: TODO
- Cách sửa và ai nhận việc (`owner`): TODO
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): TODO
