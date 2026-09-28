# Guideline patch

- **Rule mới đề xuất:** Quy định gán nhãn bắt buộc cho đối tượng ở vùng giáp ranh hai camera (Seam Region). Với các đối tượng xuất hiện ở vùng chồng lấp giữa 2 mắt thấu kính, duy trì ID đồng nhất và bắt buộc thêm thuộc tính `seam_overlap=true`.
- **Áp dụng cho:** Tất cả các class động (`Car`, `Bike`, `Pedestrian`, `Bus`, `Truck`) tại vùng viền thấu kính `edge` zone và vùng giao thấu kính.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** Luật v1.0.0 chưa có chính sách rõ ràng cho việc gộp/tách nhãn đối tượng xuất hiện ở vùng giao thấu kính 360, dẫn đến nguy cơ gán trùng lặp (duplicate) hoặc lệch không gian 3D. Bằng chứng: frame `adasind_167700.jpg` / L8+M8 (`LM_noR`, `E3_data_defect`, `action=escalate`) cho thấy cả người (L) và model (M) phát hiện đối tượng nhưng reference (R) không ghi nhận — có thể do thiếu policy xử lý vùng seam.
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** Áp dụng ngay từ Phase P5 (Rework) và kế hoạch thử nghiệm Gold Set 4 camera.
- **Đề xuất thay luật ở file này, không sửa trực tiếp `docs/02-rules-vi.md`.**

