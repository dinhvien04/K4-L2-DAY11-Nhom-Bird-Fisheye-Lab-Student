# QA review · B4-mid

- **Reviewer:** Nguyễn Huỳnh (theo rotation CLI huynh → loc) / kiểm tra độc lập cùng Nguyễn Đình Viên (vai QA nhóm)
- **Chủ nhãn (người được review):** Lộc (loc)
- **Slice QA:** B4-mid
- **Mã khóa đã kiểm:** 5CED-14DA (QA slice B4-mid của Lộc)
- **Ngày review:** 2026-09-28

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_249480.jpg | L1 | R02 | Khung bounding box xe máy trên ảnh fisheye gốc chưa ôm sát ngoại tiếp đối tượng |
| adasind_261480.jpg | L4 | R05 | Đối tượng xe máy nằm sát mép ảnh bên trái bị cắt viền nhưng thiếu thuộc tính truncated |
| adasind_265065.jpg | L1 | R02 | Khung bounding box xe tải chưa ôm sát cản trước và bánh xe bên trái bị méo quang học ở vùng fisheye, cần nới rộng về phía mép trái |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.

