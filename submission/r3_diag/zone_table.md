# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 10 | 1 | 1 | 2 | 3 | ATTRIBUTE (1) |
| mid | 6 | 1 | 0 | 2 | 2 | ATTRIBUTE (1) |
| edge | 2 | 2 | 3 | 2 | 4 | WRONG_CLASS (2) |

## Nhận xét

- **Zone người (L) và model (M) gãy nhiều nhất**: Vùng rìa thấu kính `edge` là nơi cả người gán nhãn L và mô hình AI M gặp tỷ lệ sai sót cao nhất (L missing 2/2 frame, L spurious 3; M missing 2, M thừa 4).
- **Giả thuyết nguyên nhân & Giới hạn**: Độ méo hình học cao ở vùng biên thấu kính fisheye làm tỷ lệ đè IoU bị suy giảm mạnh, các bounding box bị biến dạng tỷ lệ và hiện tượng ánh sáng lóa/bóng râm rìa kính làm nhầm lẫn class. Giới hạn của slice 3 frame chưa phản ánh hết được sự biến đổi đa dạng về góc chiếu sáng trong các thời điểm khác nhau.
