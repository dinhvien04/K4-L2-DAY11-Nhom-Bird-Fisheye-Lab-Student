# Escalation ticket

## Ticket 1

- **Frame:** `adasind_167700.jpg`
- **Object ref:** L8+M8
- **Cell:** `LM_noR` — cả người gán nhãn (L) và model (M) phát hiện đối tượng, nhưng reference (R) không ghi nhận
- **Ảnh chụp:** Báo cáo overlay trực quan `r1_craft/compare.html` (frame `adasind_167700.jpg`, hiển thị chi tiết đối tượng L8+M8 trong so sánh với reference)
- **What:** SPURIOUS
- **Why:** `E3_data_defect` — trên ảnh camera đơn lẻ ADASIND, đối tượng L8+M8 có sự bất đồng giữa annotator/model với reference (reference ambiguity ở vùng biến dạng thấu kính). Đây là minh chứng điển hình để nhóm escalate lên Data Ops nhằm chuẩn bị policy cho tình huống giả lập SVM 4 camera.
- **Expected impact:** Khi mở rộng sang hệ thống giả lập SVM 4 camera, các đối tượng ở vùng giáp ranh hai thấu kính camera (seam region) nếu không có quy chuẩn sẽ dẫn đến việc các annotator gán nhãn không nhất quán, ảnh hưởng đến độ chính xác của hệ thống BEV 360 khi ghép nhãn từ nhiều camera.
- **Owner:** `data_ops`
- **Recommendation:** Với dữ liệu 1 camera hiện tại, Data Ops cần xác nhận lại tiêu chí chấp nhận đối tượng ở vùng méo thấu kính. Với kế hoạch mở rộng sang 4 camera giả lập, bổ sung bước kiểm tra đồng bộ mốc thời gian và ma trận nắn hình học 3D trước khi gộp các bounding box thuộc vùng giao giữa 2 camera, đồng thời ban hành guideline patch cho seam region (xem `20_guideline_patch.md` v1.1.0).
- **Finding liên quan:** Dòng `r3_diag,B3-center,adasind_167700.jpg,L8+M8,LM_noR,SPURIOUS,E3_data_defect,P2,data_ops,,,escalate,v1.0.0,` trong `findings.csv`

