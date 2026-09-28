# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 4 | 0 | 1 | 1 | 4 | SPURIOUS (1) |
| mid | 13 | 8 | 1 | 3 | 7 | MISSING (8) |
| edge | 0 | 0 | 0 | 0 | 1 | — |

## Nhận xét

- Zone nào người (L) và model (M) gãy nhiều nhất, dẫn số ở bảng trên: Zone `mid` là vùng bị gãy nhiều nhất với 8 ca bỏ sót (MISSING) của người gán nhãn (L) và 7 ca báo thừa (SPURIOUS) của Model (M). Zone `center` cũng có 4 ca báo thừa từ phía Model.
- Giả thuyết vì sao (méo fisheye, box lỏng, thiếu `ego_body`, ...) và giới hạn của slice ba frame: Nguyên nhân do ở vùng `mid`, hiệu ứng uốn cong của kính fisheye làm các phương tiện ở xa bị nén nhỏ và biến dạng, dẫn đến người gán nhãn dễ bỏ sót các xe hai bánh (`Bike`). Model YOLO bị lệch miền (domain shift) do huấn luyện trên ảnh phẳng, không biết bối cảnh `ego_body` nên sinh ra nhiều box giả (spurious) ở vùng méo và viền ống kính. Giới hạn slice 3 frame chưa đại diện đủ hết các tình huống giao thông phức tạp.