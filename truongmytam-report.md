# Báo cáo cá nhân — Ngày 11

**Họ tên** Trương Mỹ Tâm\
**Mã học viên** 03106\
**Phiên bản CVAT** 2.81.0\
**Guideline** Road v1.0\
**Lần nộp (`revision`)** 1, theo `truongmytam-manifest.json`.\
**Thời điểm export** 09:23:16 ngày 21/11/2026 (giờ Việt Nam), theo `meta/dumped` trong XML.\
**Số lần nộp lại sau Rework** Chưa có thông tin xác nhận.

## 1. Kiểm project

| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label đúng kiểu | Có | `lane` và `road_curb` là polyline. `crosswalk` và `drivable` là polygon. `traffic_light` và `traffic_sign` là rectangle. |
| Thuộc tính và giá trị | Có | Khai báo trong XML xuất từ job #19 khớp `configs/road_v1_labels.json`. |
| 4 tag ảnh | Có | Cả 28 ảnh đủ `camera`, `timeofday`, `weather`, `source`. Tag camera khớp tên ảnh. |

Khi vẽ polyline, đặt các điểm từ gần xe ra xa rồi nhấn **N** để kết thúc. Dùng công cụ **Tag** ở thanh bên trái, đặt `camera` trước, rồi chọn `value` của từng tag trong **Objects → Details**. [Hướng dẫn CVAT](docs/huong_dan_cvat_bang_hinh.md)

## 2. Số lượng đã gán

Job #19 chứa cả Set A và Set B. Bảng đếm theo mã ảnh trong ZIP export mới nhất.

| Nhóm | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Front A01–A12 | 12 | 34 | 17 | 4 | 23 | 21 | 36 |
| Front-extra A13–A16 | 4 | 12 | 3 | 5 | 8 | 7 | 13 |
| Fisheye B01–B08 | 8 | 5 | 16 | 9 | 5 | 3 | 5 |
| Fisheye-extra B09–B12 | 4 | 1 | 8 | 5 | 6 | 1 | 0 |
| **Tổng** | **28** | **52** | **44** | **23** | **42** | **32** | **54** |

## 3. Bảng ca khó

| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A03 | `lane` | Vạch vàng dọc và các nét vàng ngang kề bên | `L1 / solid / yellow / single` cho vạch dọc phía sát làn | Vạch dọc đánh dấu ranh giới bên trái của làn xe. |
| A08 | `lane` | Phân vị trí cho vạch trắng liền phía xa bên trái | `position = other` | Chưa đủ căn cứ để xác định vạch đó là L1 hay L2 của làn xe. |
| B08 | `drivable`, `road_curb`, `crosswalk` | Mép vùng lái khi bó vỉa cong và một phần bị xe đạp che | Thu vùng lái về phía mặt đường, vẽ chân bó vỉa ở đoạn thấy rõ và khoanh cả cụm vạch qua đường | Giữ vùng lái trong phần mặt đường nhìn thấy và ngoài phần thân xe mình. |
| B11 | `drivable`, `road_curb` | Ranh giới giữa lối xe chạy và ô đỗ dành cho xe lăn | Khoanh phần đường bên trái và vẽ theo chân bó vỉa cạnh ô đỗ | Ô đỗ và vùng kẻ chéo nằm ngoài vùng lái. |

## 4. Phiếu QC 1 nhận được

Trương Mỹ Tâm chưa nhận Phiếu QC 1 bằng văn bản cho lô job #19.

Lab Coach và mentor đã xác nhận trực tiếp **7 cảnh báo QC1-02** do ảnh thật sự không thấy vạch. A05 và A06 không thấy L1/R1, A07 không thấy L1, A09 và A14 không thấy R1. Giữ nguyên nhãn theo xác nhận này. [Hồ sơ xác nhận của coach](qc1-xac-nhan-coach-job-19.md)

Phiếu QC 1 kiểm lô của Trần Thị Ngọc Ánh được lưu riêng. [Phiếu QC 1 đã lập](truongmytam-qc1-for-tranthingocanh.md)

## 5. Kiểm file export

Bản export `job_19_annotations_2026_11_21_02_22_49_cvat for images 1.1.zip` được tách thành hai ZIP bàn giao. Mỗi ZIP chỉ chứa `annotations.xml` phiên bản 1.1. Hai ZIP có tổng cộng 247 hình vẽ và 112 tag, khớp nội dung bản export gộp. CVAT báo job #19 đã `completed`.

| File bàn giao | Mở lại được? | Số hình ở ảnh 1 (job / file) | Số hình ở ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| `truongmytam-front.zip` | Có | A01: 9 / 9 | A02: 8 / 8 | Có |
| `truongmytam-fisheye.zip` | Có | B01: 5 / 5 | B02: 6 / 6 | Có |

Lint trên hai ZIP ghi 18 cảnh báo, gồm 7 trường hợp QC1-02 đã được xác nhận trực tiếp, 6 cảnh báo trùng vị trí ở cặp vạch đặt `kind = double`, 2 gợi ý thêm điểm polyline ở B03 và B09, và 3 hộp biển dưới 8 px. Manifest xác nhận `contains_images = false` cho cả hai ZIP. [Manifest bàn giao](truongmytam-manifest.json)

## 6. Ảnh chụp màn hình

**Tab Labels của job #19**

![Tab Labels hiển thị sáu nhãn vẽ và bốn tag](<Screenshot 2026-11-21 111553.png>)

**A01 với lane, vùng lái và biển báo**

![A01 đã gán nhãn trên CVAT](<Screenshot 2026-11-21 111210.png>)

**B03 với các polyline trên ảnh fisheye**

![B03 đã gán nhãn trên CVAT](<Screenshot 2026-11-21 111636.png>)

**Đoạn XML trích từ A01**

```xml
<polyline label="lane" source="manual" occluded="0" points="109.90,720.00;334.33,528.42;360.97,508.28" z_order="0">
  <attribute name="position">L1</attribute>
  <attribute name="style">solid</attribute>
  <attribute name="color">white</attribute>
  <attribute name="kind">single</attribute>
</polyline>
```

## 7. Tự đánh giá

Từ các chỉnh sửa đã ghi nhận, một lỗi cần chú ý là `QC1-07`, vùng `drivable` lấn lên bó vỉa ở B08. Khi làm Ngày 20, sau khi đóng polygon nên phóng to chân bó vỉa và mép thân xe để rà từng đoạn biên trước khi lưu.

Polygon `drivable` được dùng để tạo mặt nạ huấn luyện của vùng xe có thể đi. Nếu polygon ở B08 lấn lên bó vỉa, các pixel trên bó vỉa sẽ bị gán thành vùng lái. Mô hình có thể học biên vùng lái rộng hơn phần mặt đường thực tế. Đường bao B08 đã được thu về phía mặt đường.

## 8. Hoạt động row-anchor

Mục này là hoạt động tùy chọn.
