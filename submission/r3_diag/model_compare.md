# L / R / M

L/R/M là thứ tự box in-scope theo XML của từng frame.

## adasind_249480.jpg
- L1+R1+M1: LRM (center)
- L2+R2+M5: LRM (mid)
- M2: M_only (center)
- M4: M_only (center)
- M6: M_only (edge)
## adasind_261480.jpg
- L3+R7+M9: LRM (mid)
- L5+R3+M3: LRM (mid)
- L6+R1+M1: LRM (center)
- L4+R2+M7: LRM (mid)
- L1+R4: LR_noM (center)
- L2: L_only (mid)
- R5: R_only (mid)
- R6: R_only (mid)
- M2: M_only (mid)
- M5: M_only (mid)
- M6: M_only (mid)
- M8: M_only (mid)
- M10: M_only (center)
- M11: M_only (mid)
- M12: M_only (center)
- M13: M_only (mid)
## adasind_265065.jpg
- L3+R4+M4: LRM (center)
- L1+R3+M1: LRM (mid)
- L2: L_only (center)
- R1+M3: RM_noL (mid)
- R2+M2: RM_noL (mid)
- R5+M7: RM_noL (mid)
- R6+M6: RM_noL (mid)
- R7: R_only (mid)
- R8+M5: RM_noL (mid)
- M8: M_only (mid)

## Zone × cell
| zone | LRM | LR_noM | LM_noR | L_only | RM_noL | R_only | M_only |
|---|---|---|---|---|---|---|---|
| center | 3 | 1 | 0 | 1 | 0 | 0 | 4 |
| mid | 5 | 0 | 0 | 1 | 5 | 3 | 7 |
| edge | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
