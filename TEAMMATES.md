# Thành viên và phân vai — Day11 SVM 360 Fisheye

## 1. Thông tin nhóm

- Khóa/lớp: K4-L2
- Tên nhóm: Nhóm Bird
- Repo Public: K4-L2-DAY11-Nhom-Bird-Fisheye-Lab-Student
- Remote URL: https://github.com/dinhvien04/K4-L2-DAY11-Nhom-Bird-Fisheye-Lab-Student.git
- Máy giữ hồ sơ chính / người quản lý: Máy huynh (macOS)
- Slice chính lưu trong hồ sơ bài nộp: B3-center
- Tên định danh vai A dùng cho --self: huynh
- Kênh trao đổi nội bộ: Zalo nhóm
- Đại diện nộp (vai C): Lộc
- Commit chốt bài: 57edd72 (và các commit hoàn thiện hồ sơ trên main)

## 2. Ba vai chính


| Vai                           | Họ và tên        | MSSV        | Tên định danh trong mode | Trách nhiệm                                         | Bằng chứng đóng góp                                                                                                           |
| ----------------------------- | ---------------- | ----------- | ------------------------ | --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| A · Gán nhãn                  | Nguyễn Huỳnh     | 2A202602206 | huynh                    | Parking/C0/slice B3-center, self-QC, lock, rework, thực hiện QA slice B4-mid theo rotation CLI | `submission/r1_craft/` (lock A91B-0A4B), `submission/rework/` (lock 6A13-12AB), `submission/parking/`, `submission/p1_calib/`, `submission/r2_qa/qa_review.md` |
| B · QA độc lập                | Nguyễn Đình Viên | 2A202602148 | vien                     | Review chéo độc lập trước reference, rà soát finding QA slice B4-mid, kiểm lại ca sửa, soát bằng chứng P6 | `submission/r2_qa/qa_review.md`, findings r2\_qa trong `findings.csv`, `submission/screenshots/`, soát `50_exit_ticket.md` câu 1–2 |
| C · Chẩn đoán &amp; điều phối | Lộc              | 2A202602242 | loc                      | Báo cáo chẩn đoán, phân xử findings, kế hoạch 4 camera, chủ nhãn slice B4-mid (được QA review mã 5CED-14DA), tích hợp hồ sơ, check và nộp | `submission/r3_diag/`, `submission/40_decision_log.csv`, `submission/45_sampling_plan.csv`, `submission/46_gold_set_plan.md`, `submission/10_error_card.md`, `TEAMMATES.md`  |


Phân công slice trong `mode.json`: Huỳnh (B3-center), Lộc (B4-mid), Viên (B1-mid). Vòng QA trong `team.json` gồm: Huỳnh review Lộc (slice B4-mid), Lộc review Viên (slice B1-mid), Viên review Huỳnh (slice B3-center). Trong repo nộp bài chung này (`self=huynh`), dữ liệu gán nhãn tập trung lưu trữ slice B3-center của Huỳnh, và báo cáo `submission/r2_qa/qa_review.md` lưu trữ kết quả review trên slice B4-mid của Lộc (mã khóa 5CED-14DA) do Huỳnh thực hiện theo rotation CLI kết hợp cùng sự kiểm tra chéo độc lập của Viên.

## 3. Bàn giao theo pha


| Mốc                         | Người giao → nhận              | File / commit / mã khóa                                    | Người nhận đã kiểm gì?                                   | Trạng thái / vướng mắc |
| --------------------------- | ------------------------------ | ---------------------------------------------------------- | -------------------------------------------------------- | ---------------------- |
| P0 · Chốt môi trường và vai | C (loc) → A (huynh), B (vien)  | mode.json, slice B3-center, phân vai                       | Kiểm mode.json đúng 3 thành viên, slice B3-center        | Hoàn thành             |
| P1 · Hiệu chuẩn C0          | A (huynh) → C (loc)            | p1\_calib/annotations.xml, lock 9FFB-137A                  | C kiểm lock và chạy reference/compare calib              | Hoàn thành             |
| P2 · Khóa bản đầu           | A (huynh) → B (vien), C (loc)  | r1\_craft/annotations.xml, lock A91B-0A4B, slice B3-center | B xác nhận mã khóa khớp, C kiểm đúng phiên bản           | Hoàn thành             |
| P3 · Chốt QA mù             | B (vien) → C (loc), A (huynh)  | qa\_review.md, findings r2\_qa, ảnh screenshots/           | C kiểm nhận xét có rule/object\_ref, A phản hồi sau chốt | Hoàn thành             |
| P4 · Quyết định sửa         | C (loc) → A (huynh), B (vien)  | findings r3\_diag, decision log                            | A/B đối chiếu quyết định với ảnh                         | Hoàn thành             |
| P5 · Kiểm bản sửa           | A (huynh) → B (vien) → C (loc) | rework/annotations-v2.xml, lock2 6A13-12AB, delta.md       | B kiểm lại ca đã sửa, C đọc delta                        | Hoàn thành             |
| P6 · Chốt nộp               | A (huynh), B (vien) → C (loc)  | manifest.json, commit chốt                                 | Cả ba duyệt cùng một commit                              | Hoàn thành             |


## 4. Bất đồng và phối hợp

- Một ca đã phân xử: Frame `adasind_167700.jpg` / L7 / WRONG\_CLASS; A (huynh) vẽ là Bike, reference coi là class khác → nhóm quyết định `action=rework`, A sửa lại class theo reference và guideline. Bằng chứng: dòng r1\_craft trong findings.csv, compare.html
- Ca còn mở: Frame `adasind_167700.jpg` / L8+M8 / LM\_noR / SPURIOUS → `action=escalate`, E3\_data\_defect. Người theo dõi: C (loc). Phép kiểm tiếp theo: cần thêm dữ liệu và kiểm tra calibration camera
- Đóng góp của A/B/C vào kế hoạch và exit ticket: A (huynh) cung cấp kinh nghiệm gán nhãn fisheye cho câu 3 exit ticket và viết observations parking; B (vien) đóng góp góc nhìn QA cho câu 1–2 exit ticket, soát screenshots và checklist bằng chứng; C (loc) tổng hợp và viết sampling/gold plan, error card, guideline patch, escalation ticket và decision log
- Thay đổi phân công nếu có: Không đổi phân công trong suốt buổi lab

## 5. Xác nhận trước khi nộp

- [x] A xác nhận nhãn và export đúng phiên bản: Nguyễn Huỳnh / r1\_craft lock A91B-0A4B, rework lock 6A13-12AB
- [x] B xác nhận đã QA độc lập trước reference và kiểm lại ca sửa: Nguyễn Đình Viên / qa\_review.md, findings r2\_qa
- [x] C xác nhận báo cáo đúng bản khóa, các file đầy đủ và check exit 0: Lộc / manifest.json failed\_gates rỗng
- [x] manifest.json tại commit chốt có failed\_gates rỗng.
- [x] Repo nhóm Public, ảnh và các bằng chứng mở được.
- [x] C đã push và gửi link repo nhóm + commit qua kênh lớp công bố.

Chỉ đánh dấu việc đã kiểm thật. Nhóm nộp một hồ sơ chung; check không tự chấm đóng góp từng người. Giữ nguyên header/các cột enum của findings.csv; tên người được ghi trong tài liệu này hoặc phần note thích hợp.