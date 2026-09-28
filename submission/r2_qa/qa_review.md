# QA review · B4-mid

Mã khóa: 5CED-14DA

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_249480.jpg | Truck | R01 | Xe tải nhỏ có chiều cao > 40px, box bao trọn phần nhìn thấy trên ảnh fisheye gốc. |
| adasind_249480.jpg | ego_body | R07 | Polygon ego_body được vẽ chuẩn ở viền đáy ảnh, không phủ lấn lên các phương tiện xung quanh. |
| adasind_261480.jpg | ThreeWheeler | R04 | Xe ba bánh chở hàng được gán đúng class ThreeWheeler và bật occluded=1 do bị che một phần. |
| adasind_261480.jpg | Bike | R03 | Xe 2 bánh ở vùng bên phải được vẽ 1 box Bike duy nhất gộp cả xe và người lái theo đúng luật rider. |
| adasind_265065.jpg | Bike | R05 | Các xe 2 bánh ở tiền cảnh được phân tách từng box riêng lẻ, thuộc tính occluded=0 do nhìn thấy rõ. |