# Xác nhận của coach về QC1-02 trong job 19

Lab Coach và mentor đã xác nhận trực tiếp bảy cảnh báo `QC1-02` thuộc các trường hợp không thấy vạch chia làn tương ứng trong ảnh. Ghi nhận này áp dụng cho bản export `job_19_annotations_2026_11_21_02_22_49_cvat for images 1.1.zip` và hai ZIP bàn giao được tách từ bản đó.

| Ảnh | Vạch không thấy | Số cảnh báo được xác nhận |
| --- | --- | ---: |
| A05 | `L1`, `R1` | 2 |
| A06 | `L1`, `R1` | 2 |
| A07 | `L1` | 1 |
| A09 | `R1` | 1 |
| A14 | `R1` | 1 |
| **Tổng** | | **7** |

Các trường hợp trên được miễn theo quy định nộp bài. Giữ nguyên nhãn của các ảnh này. `road_check lint` vẫn sẽ liệt kê bảy cảnh báo trong kết quả kiểm tra và tính chúng vào `lint.nặng` trong manifest. [Quy định nộp bài](SUBMISSION.md) · [Đặc tả bàn giao](docs/delivery_road_v1.0.md)

## Hướng dẫn vẽ và kiểm vạch đôi trong job 19

- Dùng nhãn `lane` và vẽ **hai polyline**, mỗi đường bám **tâm một nét sơn**, từ gần xe ra xa. Với ảnh fisheye, thêm điểm ở đoạn cong để đường bám tâm nét sơn.
- Đặt `kind = double` cho cả hai đường và dùng cùng `position`, `style`, `color`. Ví dụ, cặp vạch vàng liền ngay bên trái làn xe dùng `L1 / solid / yellow / double` cho cả hai đường.
- Khi `lint` báo `QC1-05` do trùng `position`, mở ảnh để xác nhận hai polyline bám hai nét sơn của cùng một vạch đôi. Nếu hai đoạn sơn thuộc cùng một nét đứt, nối chúng bằng một polyline.
