# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): **Phát** (`front_camera` task 33, `fish_eye` task 34)  
Người kiểm (học viên): Đặng Minh Huy (DangMinhHuy)  
Ngày: 2026-11-21 · Phiên bản guideline: Road v1.0  
File được kiểm: `front_qc (1).zip` (16 ảnh, 263 shape, 52 tag) và `fisheye_qc (1).zip` (12 ảnh, 64 shape, 48 tag). **Không kèm manifest** → không đối chiếu được `revision` và `sha256` (ghi ở QC1-12, mục Ca chờ lead).  
Số ảnh kiểm: **6** (A03, A04, A08, A09, B05, B07) — chọn rải cả hai task, có ảnh đông đèn/biển và camera hai bên. Ảnh thêm (A13–A16, B09–B12) **không** nằm trong mẫu; phần quét thêm ngoài mẫu ghi riêng ở cuối phiếu.  
Số nhãn đã kiểm (shape + tag): **116** (96 shape + 20 tag).

Mẫu số dùng cho mọi tỉ lệ trong phiếu là **116**, không phải số ảnh.

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 | 1 (+3 nhẹ) | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 8 | 1 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 24 | 4 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 33 | 4 (+4 chờ lead) | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 24 | 6 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 72 | 2 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 29 | 0 (13 chờ lead) | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 20 | 0 (6 chờ lead) | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 106 | 0 (5 chờ lead) | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 23 | 2 | nhẹ (gợi ý, không trừ điểm) |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 6 | 0 (2 chờ lead) | chính |
| QC1-12 file | lỗi file | 12 | 0 (1 chờ lead) | nhẹ / nặng |

Cột "chờ lead" là mục ở mục **Ca mơ hồ** dưới đây — chưa tính vào số lỗi vì cần ảnh gốc hoặc GT để quyết. Tổng 31 mục chờ lead, gom thành 6 câu hỏi.

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-01 | A09 | `tag:camera` | nặng | Thiếu tag `camera` (và thiếu luôn timeofday/weather/source — dòng 2–4) |
| 2 | QC1-01 | A09 | `tag:timeofday` | nhẹ | Thiếu tag |
| 3 | QC1-01 | A09 | `tag:weather` | nhẹ | Thiếu tag |
| 4 | QC1-01 | A09 | `tag:source` | nhẹ | Thiếu tag |
| 5 | QC1-02 | A09 | `lane` | nặng | Không có polyline nào `position = R1`; chỉ có L1@(520,665) và hai L2 |
| 6 | QC1-03 | B05 | `lane#1@(1123,440)` | nặng | Camera `fisheye_left`: `position = L1`, phải là `other` |
| 7 | QC1-03 | B07 | `lane#3@(1118,244)` | nặng | Camera `fisheye_right`: `position = R1`, phải là `other` |
| 8 | QC1-03 | B07 | `lane#4@(139,693)` | nặng | Camera `fisheye_right`: `position = R1`, phải là `other` |
| 9 | QC1-03 | B07 | `lane#8@(165,450)` | nặng | Camera `fisheye_right`: `position = R2`, phải là `other` |
| 10 | QC1-04 | A08 | `lane#6@(0,361)` | chính | Điểm đầu (y=361) cao hơn điểm cuối (y=367): vẽ từ xa về gần |
| 11 | QC1-04 | A08 | `lane#10@(519,302)` | chính | Điểm đầu (y=302) cao hơn điểm cuối (y=322): vẽ từ xa về gần |
| 12 | QC1-04 | A08 | `lane#12@(655,321)` | chính | Mẩu 2 điểm dài ~16 px nằm sát điểm tụ — hoặc là phần nối của vạch khác (sai điểm dừng), hoặc vẽ thừa |
| 13 | QC1-04 | A08 | `lane#13@(627,289)` | chính | Mẩu 2 điểm dài ~10 px sát điểm tụ, không có đầu gần xe |
| 14 | QC1-05 | A04 | `lane` | chính | 2 polyline cùng `L1`: lane#3@(23,554) và lane#4@(64,552) |
| 15 | QC1-05 | A04 | `lane` | chính | 2 polyline cùng `R1`: lane#12@(718,537) và lane#13@(1280,515) |
| 16 | QC1-05 | A08 | `lane` | chính | 2 polyline cùng `L1`: lane#8@(46,358) và lane#9@(413,294) |
| 17 | QC1-05 | A08 | `lane` | chính | 3 polyline cùng `R1`: lane#11@(764,449), lane#12@(655,321), lane#13@(627,289) |
| 18 | QC1-05 | A09 | `lane` | chính | 2 polyline cùng `L2`: lane#3@(470,660) và lane#4@(422,657) |
| 19 | QC1-05 | B07 | `lane` | chính | 2 polyline cùng `R1`: lane#3@(1118,244) và lane#4@(139,693) |
| 20 | QC1-06 | A04 | `lane#3`, `lane#4` | chính | Hai polyline cùng `L1` đều khai `kind = double` (vàng đôi): một vạch vàng đôi là **một** polyline `kind=double`, không phải hai polyline đơn |
| 21 | QC1-06 | A09 | `lane#3`, `lane#4` | chính | Hai polyline cùng `L2` đều `solid white double` — trùng như dòng 20 |
| 22 | QC1-10 | A04 | `traffic_sign#9@(763,248)` | nhẹ | Box cao 6,3 px (< 8 px): không bắt buộc gán, gợi ý tự kiểm |
| 23 | QC1-10 | A04 | `traffic_sign#5@(218,266)` | nhẹ | Box cao 7,9 px (< 8 px), sát ngưỡng — kiểm lại mép biển |

**Ảnh kiểm và không tìm thấy lỗi:** **A03** — 4 tag đủ và đúng (`camera=front`, `timeofday=dusk`, `weather=clear`, `source=real`); có `L1`@(222,704) và `R1`@(897,647); cả ba polyline vẽ từ gần ra xa (điểm đầu y=704/631/647 thấp hơn điểm cuối y=380/401/385); `position` không trùng; `drivable` có đủ `direct` + `alternative`; không box nào dưới 8 px. Chỉ còn 1 ca chờ lead ở mục Ca mơ hồ #1 (cặp đèn `#11`/`#3`).

## Ca mơ hồ (cần lead / cần ảnh gốc hoặc GT)
| # | Mã | Ảnh | Câu hỏi cho lead | Số mục | Lời đáp (nếu có) |
| --- | --- | --- | --- | ---: | --- |
| 1 | QC1-08 | A03, A08 | Có cặp box `traffic_light` trùng nhau: A03 `#11@(594,328)` đè `#3@(604,343)`; A08 5 cặp cùng trục x (871/871, 766/766, 670/670, 525/519, 608/603) lệch 20–35 px theo y. Hai đầu đèn khác nhau trên cùng một giá, hay một đèn bị box hai lần (thừa)? | 6 | |
| 2 | QC1-09 | A08 | 5 cặp `traffic_sign` chồng nhau (991/991, 290/290, 699/696, 434/435, 700/699) với `group` khác nhau (`prohibitory`, `warning`, `mandatory`): biển kép trên cùng cột hay gán trùng đối tượng? | 5 | |
| 3 | QC1-07 | A03, A04, A08, A09, B05, B07 | 13 polygon `drivable`: có tràn vỉa hè, thân xe hay phần sau cọc không? Không có GT nên không đo được IoU và phần tràn. | 13 | |
| 4 | QC1-04 | B05, B07 | Chiều polyline trên camera hai bên (B05 `lane#1@(1123,440)`; B07 `lane#3`, `lane#4`, `lane#8`): "gần → xa" áp theo khoảng cách tới xe hay theo y của ảnh? `lint` chỉ kiểm camera front nên tôi không dám kết luận. | 4 | |
| 5 | QC1-11 | B05, B07 | `road_curb` (B05 8 điểm, B07 22 điểm) đã bám đúng cung chưa — cần zoom đối chiếu tâm vạch, ngưỡng 5 px. | 2 | |
| 6 | QC1-12 | cả lô | Không kèm manifest bàn giao: không xác minh được `revision`, `sha256`, `contains_images`. Có tính là lỗi file không? | 1 | |

## Quyết định
Lỗi nặng: **6**   Lỗi chính: **12** / **116** nhãn = **10,3 %**   Lỗi nhẹ: **5**   Ca chờ lead: **31 mục / 6 câu hỏi**  
Quyết định: **Rework**  
Lý do (theo luật của phiếu): lô còn lỗi nặng (dòng 1, 5–9: thiếu tag `camera` ở A09 và 4 lane `position` sai quy tắc camera hai bên ở B05/B07) → Rework theo điều kiện một; đồng thời tỉ lệ lỗi chính 12/116 = 10,3 % vượt ngưỡng 5 % → Rework theo điều kiện hai. Không ra Hold vì 6 ca mơ hồ không làm đổi kết luận: dù lead trả lời theo hướng nào, vẫn còn lỗi nặng.

Ưu tiên sửa: (1) tag 4 mục cho A09; (2) `position = other` cho mọi lane ở B05–B08 (B06, B08 cũng bị, ghi ở phần ngoài mẫu); (3) `R1` cho A09; (4) đảo chiều lane#6, lane#10 ở A08 và nối hai mẩu lane#12/#13 vào vạch chủ; (5) gộp các polyline cùng `position` thành một vạch, riêng vạch vàng đôi dùng `kind = double`.

## Quét thêm ngoài mẫu (toàn lô, không tính vào tỉ lệ ở trên)
| Mã | Ảnh | Nội dung | Mức |
| --- | --- | --- | --- |
| QC1-01 | A11, A16 | thiếu tag `camera` (kèm 3 tag khác) | nặng |
| QC1-01 | B01 | `camera = fisheye_right`, tên file `_FV` → `fisheye_front` | nặng |
| QC1-01 | B12 | `camera = fisheye_left`, tên file `_MVR` → `fisheye_right` | nặng |
| QC1-03 | B06 `lane#2@(844,436)`, B08 `lane#3@(377,522)` | camera hai bên nhưng `position = L1`/`R1` | nặng |
| QC1-02 | A02, A05, A06, A07, A14 | chưa có đủ L1/R1 (A05 không có lane nào) — miễn nếu coach xác nhận không thấy vạch | nặng |
| QC1-05 | A01, A06, A10, A11 (4 cùng L1), A12, A14 | nhiều polyline cùng `position` | chính |
| QC1-04 | A11 `lane#1@(576,434)`, A16 `lane#3@(237,365)` | điểm đầu cao hơn điểm cuối | chính |
| QC1-11 | B01 `road_curb#3@(569,372)` (2 điểm), B08 `lane#3` (3 điểm) | polyline quá thưa trên fisheye | chính |
| QC1-11 | B03 `traffic_sign#0`, B04 `traffic_sign#5`, B10 `traffic_sign#0` | tâm box ngoài 80 % bán kính nhưng `edge_zone` tắt | chính |
| QC1-10 | A10 (4 box), A11, A12, A15 | box biển dưới 8 px | nhẹ |

---
Cách kiểm: `PYTHONPATH=src python -m road_lab.road_check lint front_qc.zip fisheye_qc.zip` (lint không có GT) cộng với đọc trực tiếp `annotations.xml` cho `position`, chiều polyline, `kind=double` và box trùng. Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng (ISO/IEC 5259-4, 8.4.2). Xếp mức theo [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
