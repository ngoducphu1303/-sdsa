# Artemis – Leo: bộ Attack vẽ nhiều tư thế (bản thử)

## Đã hoàn thành
- 6 frame **Attack thực sự khác tư thế** (không chỉ xoay/co giãn toàn bộ ảnh).
- Tách từ ảnh động AI mới (~507 px mỗi frame), xuất PNG RGBA 512×512, đồng kích cỡ.
- `spritesheets/leo_attack_6x1.png` có kích thước 3072×512, nền trong suốt sau xử lý.
- `preview/leo_attack_preview.gif` và `preview/leo_attack_contact_sheet.jpg` để xem thử.
- `leo_idle_static.png` là **1 khung đứng trung tính**, không phải hoạt ảnh Idle.
- `leo_original_1024.png` là hình Leo gốc do bạn cung cấp.

## Chưa hoàn thành / giới hạn
- **CHƯA tạo đủ 6 Idle, 4 Hit, 6 Death** đúng tư thế/độ nét theo yêu cầu.
- GIF tạo bởi AI có nền caro sáng giả lập alpha. Đã dùng thuật toán tách nền; nên soi mép tóc, giáp, lửa ở nền tối và sáng trước khi phát hành. Không được hiểu là alpha gốc từ mô hình.
- Mỗi khung nguồn khoảng 507×507, không phải 1024 px chi tiết gốc. Không khẳng định đây là bộ 22 frame chất lượng sản xuất.
- Giáp, vũ khí và tỷ lệ giữa các frame còn khác nhau nhẹ do mô hình AI; cần kiểm soát continuity trước khi dùng làm sprite chính thức.
- Chưa sửa hoặc push GitHub, chưa kiểm tra trình duyệt mobile/gameplay.

## Sử dụng thử trong Artemis
Tách các frame như manifest. Với Canvas 2D, render sprite theo rectangle nguồn `sx=frameIndex*512`, `sy=0`, `sw=512`, `sh=512`.
Giữ nguyên logic hitbox, sát thương, vị trí enemy và các cảnh báo. Nếu không tải được ảnh, dùng fallback Canvas hiện có.

## Gợi ý bước tiếp
Tạo riêng Idle/Hit/Death từ cùng ảnh nhân vật đã khóa, sử dụng sprite sheet dạng 2×3 (Idle, Death) và 2×2 (Hit), với độ phân giải khung ít nhất tương đương 512px, nền trong suốt thật; kiểm lại sự nhất quán giữa các tư thế trước khi tích hợp.
