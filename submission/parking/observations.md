# Quan sát vạch ô đỗ

- **Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh)**: Nhóm tập trung vẽ các vạch sơn phân chia từng ô đỗ xe riêng biệt nhìn rõ ở khu vực tiền cảnh (ví dụ vạch từ x=528.3, y=720.0 đến x=406.4, y=653.3 và vạch từ x=960.0, y=690.4 đến x=700.2, y=623.2) cùng các vạch chia ô tương ứng ở trung cảnh.
- **Một vạch/dấu sơn hoặc biên không vẽ, và vì sao**: Loại bỏ không vẽ các gờ lề đường (curb line) xung quanh bãi đỗ và không vẽ vạch ranh giới làn đường chạy ngang bãi đỗ xe vì chúng chỉ có vai trò phân định làn xe chạy / lối lưu thông chứ không phân chia từng ô đỗ riêng lẻ theo quy định rubric.
- **Polygon `free_space` dừng ở đâu; có phần bị che nào không**: Polygon `free_space` bao phủ toàn bộ vùng mặt đường trống của lối xe chạy; dừng lại tại chân hàng rào/rặng cây phía xa và được vẽ vòng né quanh chiếc xe ô tô màu đỏ đang đỗ.
- **Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”)**: Không có.

