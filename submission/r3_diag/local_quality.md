# Đối chiếu chất lượng cục bộ — rectangle

Teaching reference, không phải gold set đã phê duyệt; không có điểm đạt tự động.
Nguồn: export r1_craft đã khóa SHA256 `a91b0a4b9af8c9a5e2324e68c4ac08d99398aacf04a3d6596f8a79878e432741`; slice `B3-center`.
Ghép hình học greedy một-một theo IoU ≥ 0.50, rồi so class; H ≥ 40 px.
Box trái nằm chủ yếu trong ignore_region reference không tính. Polygon, polyline, track không được chấm.
Đây là phép tính offline của lab, không phải báo cáo hay kết quả tương đương CVAT Premium.

Frame được tính: adasind_152940.jpg, adasind_167700.jpg, adasind_212280.jpg. Frame thiếu trong export: không.
TP=14; FP=4; FN=4; số lần đối chiếu=19; mean IoU của TP=0.793.

| Chỉ số | Micro | Macro | Nhãn thấp nhất |
|---|---:|---:|---:|
| accuracy | 0.737 | 0.930 | 0.842 |
| precision | 0.778 | 0.410 | 0.000 |
| recall | 0.778 | 0.500 | 0.000 |
| jaccard | 0.636 | 0.410 | 0.000 |
| dice | 0.778 | 0.445 | 0.000 |

| Nhãn | TP | FP | FN | Accuracy | Precision | Recall | Jaccard | Dice |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Bike | 8 | 1 | 0 | 0.947 | 0.889 | 1.000 | 0.889 | 0.941 |
| Bus | 0 | 0 | 1 | 0.947 | 0.000 | 0.000 | 0.000 | 0.000 |
| Car | 0 | 0 | 1 | 0.947 | 0.000 | 0.000 | 0.000 | 0.000 |
| Pedestrian | 2 | 0 | 0 | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 |
| ThreeWheeler | 0 | 0 | 2 | 0.895 | 0.000 | 0.000 | 0.000 | 0.000 |
| Truck | 4 | 3 | 0 | 0.842 | 0.571 | 1.000 | 0.571 | 0.727 |

| Frame | TP | FP | FN | Accuracy | Precision | Recall |
|---|---:|---:|---:|---:|---:|---:|
| adasind_152940.jpg | 5 | 0 | 1 | 0.833 | 1.000 | 0.833 |
| adasind_167700.jpg | 7 | 3 | 2 | 0.700 | 0.700 | 0.778 |
| adasind_212280.jpg | 2 | 1 | 1 | 0.667 | 0.667 | 0.667 |

Confusion matrix: hàng = teaching reference; cột = export đã khóa.
`<missing>` là thiếu box; `<extra>` là box thừa. Xem `local_quality_confusion.csv`.

| Reference \ Export | Bike | Bus | Car | Pedestrian | ThreeWheeler | Truck | <missing> |
|---|---:|---:|---:|---:|---:|---:|---:|
| Bike | 8 | 0 | 0 | 0 | 0 | 0 | 0 |
| Bus | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| Car | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| Pedestrian | 0 | 0 | 0 | 2 | 0 | 0 | 0 |
| ThreeWheeler | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| Truck | 0 | 0 | 0 | 0 | 0 | 4 | 0 |
| <extra> | 1 | 0 | 0 | 0 | 0 | 0 | 0 |

Chi tiết xung đột trong `local_quality_conflicts.csv`; dữ liệu máy đọc trong `local_quality.json`.
Mismatching label đóng góp một FP cho class vẽ và một FN cho class reference; attribute khác được báo riêng.
Micro accuracy đếm mỗi cặp ghép sai class là một lần đối chiếu; Jaccard đếm cả FP và FN.
Macro/worst bỏ nhãn không xuất hiện ở cả hai phía; chỉ số không có mẫu là N/A.
