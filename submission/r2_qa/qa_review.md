# QA review · B4-mid

- **Reviewer (B):** Nguyễn Đình Viên
- **Chủ nhãn (A):** Nguyễn Huỳnh
- **Slice chung:** B3-center
- **Mã khóa đã kiểm:** 5CED-14DA (QA slice B4-mid của Lộc)
- **Ngày review:** 2026-09-28

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_271039.jpg | L1 | R01 | Khung bounding box xe ô tô chưa ôm sát cản sau |
| adasind_271039.jpg | L2 | R04 | Đối tượng người đi bộ thiếu thuộc tính occluded khi bị xe che khuất |
| adasind_006840.jpg | L3 | R06 | Thiếu nhãn ignore_region tại khu vực viền kính mắt cá bị bóng râm |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
