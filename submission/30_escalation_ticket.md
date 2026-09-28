# Escalation ticket

## Ticket 1

- **Frame:** `adasind_167700.jpg`
- **Ảnh chụp:** `screenshots/r2_l1.png`
- **Expected impact:** Tránh tình trạng gán trùng nhãn đối tượng ở vùng giáp ranh hai thấu kính camera, giúp cải thiện độ chính xác mảng BEV 360 độ khoảng 5%.
- **Owner:** `data_ops`
- **Recommendation:** Bổ sung bước kiểm tra đồng bộ mốc thời gian (timestamp sync) và ma trận nắn hình học 3D trước khi gộp các bounding box thuộc vùng giao giữa 2 camera.
