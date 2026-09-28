# Guideline patch

- **Rule mới đề xuất (đề xuất của nhóm cho kịch bản giả lập SVM 4 camera, cần thử nghiệm xác nhận):** Quy định gán nhãn cho đối tượng ở vùng giáp ranh hai camera (Seam Region). Với các đối tượng xuất hiện ở vùng chồng lấp quang học giữa 2 mắt thấu kính trong hệ thống đa camera, duy trì ID đồng nhất và gắn thêm thuộc tính `seam_overlap=true`.
- **Áp dụng cho:** Tất cả các class động (`Car`, `Bike`, `Pedestrian`, `Bus`, `Truck`) tại vùng viền thấu kính `edge` zone và vùng giao thấu kính trong kịch bản giả lập 4 camera.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** Dữ liệu ADASIND là ảnh một camera đơn lẻ; ca frame `adasind_167700.jpg` / L8+M8 (`LM_noR`, `E3_data_defect`, `action=escalate`) chứng minh sự bất đồng tham chiếu (reference ambiguity) trên một camera ở vùng viền biến dạng. Khi mở rộng sang hệ thống giả lập SVM 4-camera có vùng seam chồng lấp thật sự, nếu không có quy tắc gộp/tách nhãn thì sẽ phát sinh nguy cơ gán trùng lặp (duplicate) hoặc lệch không gian 3D. Do đó, quy tắc seam region là chính sách đề xuất cần thiết cho kịch bản 4 camera.
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** Đề xuất áp dụng thử nghiệm từ Phase P5 (Rework) và kế hoạch xây dựng Gold Set 4 camera giả lập.
- **Đề xuất thay luật ở file này, không sửa trực tiếp `docs/02-rules-vi.md`.**


