# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_152940.jpg
- L1 edge IGNORE_SCOPE
- L5+R1 mid ATTRIBUTE
- R6 mid MISSING
## adasind_167700.jpg
- L4 mid IGNORE_SCOPE
- L10+R8 center ATTRIBUTE
- L7+R4 center WRONG_CLASS
- L8+R6 edge WRONG_CLASS
- L11 edge SPURIOUS
## adasind_212280.jpg
- L1 edge IGNORE_SCOPE
- L4+R3 edge WRONG_CLASS

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 10 | 9 | 1 | 1 |
| mid | 6 | 5 | 1 | 0 |
| edge | 2 | 0 | 2 | 3 |
