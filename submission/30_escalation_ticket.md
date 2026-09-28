# Escalation ticket

## Ticket 1

- **Frame:** `adasind_167700.jpg`
- **Object ref:** L8+M8
- **Cell:** `LM_noR` — cả người gán nhãn (L) và model (M) phát hiện đối tượng, nhưng reference (R) không ghi nhận
- **Ảnh chụp:** `screenshots/r2_l1.png`
- **What:** SPURIOUS
- **Why:** `E3_data_defect` — nghi ngờ reference thiếu sót hoặc vùng seam chưa có policy rõ ràng
- **Expected impact:** Nếu không xử lý, các annotator khác nhau sẽ gán nhãn không nhất quán ở vùng giáp ranh hai thấu kính camera. Ảnh hưởng đến độ chính xác của hệ thống BEV 360 khi ghép nhãn từ nhiều camera.
- **Owner:** `data_ops`
- **Recommendation:** Bổ sung bước kiểm tra đồng bộ mốc thời gian (timestamp sync) và ma trận nắn hình học 3D trước khi gộp các bounding box thuộc vùng giao giữa 2 camera. Cần xây dựng policy rõ ràng cho seam region trước khi mở rộng gán nhãn sang 4 camera (xem `20_guideline_patch.md` v1.1.0).
- **Finding liên quan:** Dòng `r3_diag,B3-center,adasind_167700.jpg,L8+M8,LM_noR,SPURIOUS,E3_data_defect,P2,data_ops,,screenshots/diag_11.png,escalate,v1.0.0,` trong `findings.csv`
