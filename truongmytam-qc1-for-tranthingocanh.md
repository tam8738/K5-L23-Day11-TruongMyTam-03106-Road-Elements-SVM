# Phiếu QC 1 — Road v1.0

**Lô được kiểm** Trần Thị Ngọc Ánh (03157)\
**Người kiểm** Trương Mỹ Tâm (03106)\
**Ngày kiểm** 21/11/2026\
**File được kiểm** `task_15_annotations_2026_11_21_03_53_34_cvat for images 1.1.zip`. Chưa có manifest để đối chiếu `revision`.\
**Mẫu kiểm** A02, A04, A08, B02, B03, B06. Mẫu gồm ba ảnh camera trước và ba ảnh fisheye để kiểm vạch, vùng lái, đèn, biển và vị trí theo hướng camera.

| Ảnh | Hình vẽ đã kiểm | Tag đã kiểm |
| --- | ---: | ---: |
| A02 | 8 | 4 |
| A04 | 5 | 4 |
| A08 | 17 | 4 |
| B02 | 3 | 4 |
| B03 | 8 | 4 |
| B06 | 4 | 4 |
| **Tổng** | **45** | **24** |

## Tổng hợp theo mã

| Mã | Mục đã kiểm | Số lỗi | Mức |
| --- | --- | ---: | --- |
| QC1-01 | 24 tag, gồm 6 tag camera | 0 | nặng / nhẹ |
| QC1-02 | 6 vị trí L1/R1 trên 3 ảnh camera trước | 0 | nặng |
| QC1-03 | 17 polyline `lane` | 6 | nặng |
| QC1-04 | 13 polyline `lane` trên ảnh camera trước | 2 | chính |
| QC1-05 | 17 polyline `lane` | 1 | chính |
| QC1-06 | 17 polyline `lane` | 0 | chính |
| QC1-07 | 10 polygon `drivable` | 0 | chính |
| QC1-08 | 9 hộp đèn và màu hiển thị | 4 | nặng |
| QC1-09 | 13 hộp đèn hoặc biển và vị trí biển phụ trên 6 ảnh | 4 | chính |
| QC1-10 | 4 hộp biển và các vị trí biển nhìn thấy trên 6 ảnh | 3 | chính |
| QC1-11 | 4 polyline fisheye và 6 hộp đèn hoặc biển fisheye | 0 | chính |
| QC1-12 | 1 ZIP và 45 hình vẽ trong mẫu | 1 | nhẹ |

Trường hợp A02 bị báo thiếu `L1` đã có polyline trên vạch. Lỗi gốc là đặt sai `position`, được tính một lần ở QC1-03. B02 không có lỗi được xác nhận trong mẫu này. ID dạng `label#số@(x,y)` dùng thứ tự và tọa độ điểm đầu trong XML để tìm lại đối tượng.

## Danh sách lỗi

| # | Mã | Ảnh | Nhãn hoặc vị trí | Mức | Mô tả |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-03 | A02 | `lane#6@(416,719)` | Nặng | Vạch trắng đứt ở ngay bên trái làn xe được gán `R1`. Đổi thành `L1`. |
| 2 | QC1-04 | A02 | `lane#6@(416,719)` | Chính | Điểm đầu kéo xuống gần đáy ảnh, vượt quá nét sơn gần nhất còn thấy. Rút điểm đầu về nét sơn. |
| 3 | QC1-03 | A08 | `lane#14@(768,449)` | Nặng | Vạch đứt ngay bên phải làn xe mang `L1`. Sau khi gộp với đoạn cùng vạch, dùng `R1`. |
| 4 | QC1-04 | A08 | `lane#13@(621,282)` | Chính | Thứ tự điểm đi từ xa về gần. Khi gộp, vẽ từ gần ra xa. |
| 5 | QC1-05 | A08 | `lane#13@(621,282)`, `lane#14@(768,449)` | Chính | Hai polyline nối tiếp trên cùng một vạch trắng đứt. Gộp thành một polyline và chọn `style = dashed`. |
| 6 | QC1-08 | A08 | `traffic_light#2@(650,202)` | Nặng | Trong hộp thấy đèn sáng xanh. Nhãn đang là `red`. |
| 7 | QC1-08 | A08 | `traffic_light#6@(766,164)` | Nặng | Trong hộp thấy đèn sáng xanh. Nhãn đang là `red`. |
| 8 | QC1-08 | A08 | `traffic_light#7@(668,155)` | Nặng | Trong hộp thấy đèn sáng xanh. Nhãn đang là `red`. |
| 9 | QC1-08 | A08 | `traffic_light#9@(362,86)` | Nặng | Trong hộp thấy đèn sáng xanh. Nhãn đang là `red`. |
| 10 | QC1-09 | A08 | `traffic_light#1@(870,144)` | Chính | Ảnh chủ yếu cho thấy cạnh vỏ đèn. Đổi `facing` từ `front` sang `side` và rà lại màu. |
| 11 | QC1-09 | A08 | `traffic_sign`, tấm phía trên biển Harlem River Dr | Chính | Thiếu hộp riêng cho tấm trắng bổ sung điều kiện áp dụng phía trên biển chính. Dùng `group = supplementary`. |
| 12 | QC1-10 | A08 | `traffic_sign`, tấm trên cùng của cột biển sát thành cầu bên phải | Chính | Thiếu hộp cho tấm biển hạn chế trên cùng. |
| 13 | QC1-10 | A08 | `traffic_sign`, tấm giữa của cột biển sát thành cầu bên phải | Chính | Thiếu hộp riêng cho tấm biển có vòng tròn gạch chéo. |
| 14 | QC1-10 | A08 | `traffic_sign`, tấm dưới cùng của cột biển sát thành cầu bên phải | Chính | Thiếu hộp riêng cho tấm biển dưới vòng tròn gạch chéo. |
| 15 | QC1-03 | B03 | `lane#0@(957,629)` | Nặng | Ảnh camera sau hiển thị trực tiếp. Vạch sát làn ở bên phải ảnh nằm bên trái xe, nên dùng `L1`. |
| 16 | QC1-03 | B03 | `lane#4@(1024,427)` | Nặng | Vạch kế phía ngoài nằm bên trái xe, nên dùng `L2`. |
| 17 | QC1-09 | B03 | `traffic_sign#5@(174,300)` | Chính | Biển tròn viền đỏ thể hiện hạn chế, nên dùng `prohibitory`. |
| 18 | QC1-09 | B03 | `traffic_sign#6@(258,292)` | Chính | Biển cấm vào màu đỏ có thanh trắng ngang, nên dùng `prohibitory`. |
| 19 | QC1-12 | B03 | `drivable#2@(977,651)` | Nhẹ | Polygon có một điểm lặp liền nhau. Xóa điểm lặp. |
| 20 | QC1-03 | B06 | `lane#2@(277,252)` | Nặng | Ảnh camera bên trái yêu cầu `position = other`. Giá trị hiện tại là `R1`. |
| 21 | QC1-03 | B06 | `lane#3@(934,497)` | Nặng | Ảnh camera bên trái yêu cầu `position = other`. Giá trị hiện tại là `L1`. |

## Ca mơ hồ

| Ảnh | Câu hỏi cần xác nhận | Trạng thái |
| --- | --- | --- |
| A04 | Cặp vạch trắng sát phần đường màu xanh có thuộc nhóm vạch phải gán trên ảnh này không? | Chờ coach xác nhận phạm vi. |
| A08 | Với hộp đèn `#8`, đốm xanh nằm sát bên ngoài hộp. Cần xác nhận hộp đang nhắm vào cụm đèn nào và kiểm lại màu của đúng cụm đèn. | Chờ xác nhận từ ảnh phóng to. |
| B06 | Lint gợi ý rà lại độ bám cung của hai polyline lần lượt có 2 và 3 điểm. Cần kiểm độ lệch so với tâm sơn trước khi tính QC1-11. | Chưa tính vào số lỗi. |

## Quyết định

**Rework.** Có **10 lỗi nặng**, **10 lỗi chính trên 69 nhãn đã kiểm (14,49%)** và **1 lỗi nhẹ**. Các ca mơ hồ ở trên không ảnh hưởng đến quyết định vì mẫu đã có lỗi nặng. [Thang mức lỗi QC 1](docs/qc_severity_road_v1.0.md)
