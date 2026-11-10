# IoT-Pomodoro-Lock-Box
Hộp "Cai nghiện" Smartphone



## 1. Giới thiệu đề tài
Đề tài xây dựng một thiết bị phần cứng thông minh ứng dụng vi điều khiển **ESP32**, kết hợp giao thức truyền thông **MQTT** và hệ thống giám sát **Node-RED Dashboard**. Thiết bị này đóng vai trò như một "hộp khóa vật lý" tự động quản lý thời gian tập trung làm việc và học tập dựa trên phương pháp Pomodoro quen thuộc.

## 2. Lý do chọn đề tài & Vấn đề thực tế giải quyết
* **Thực trạng cuộc sống:** Trong thời đại số hiện nay, tình trạng nghiện smartphone và thói quen cầm điện thoại vô thức khi đang học tập hoặc làm việc làm giảm nghiêm trọng hiệu suất cá nhân của học sinh, sinh viên. 
* **Nhược điểm của giải pháp cũ:** Các ứng dụng đếm giờ Pomodoro cài sẵn trên điện thoại tỏ ra kém hiệu quả vì người dùng vẫn có thể dễ dàng chạm tay vào thiết bị bất cứ lúc nào để lướt mạng xã hội.
* **Giải pháp giải quyết:** Đề tài tạo ra một **sự cách ly vật lý bắt buộc**. Khi bắt đầu chu kỳ tập trung (ví dụ 25 phút), điện thoại sẽ bị khóa chặt bên trong hộp nhờ cơ chế điều khiển của động cơ servo. Người dùng không thể lấy ra trừ khi hoàn thành thời gian hoặc hệ thống ghi nhận kết quả lên đám mây qua MQTT. Điều này giúp rèn luyện kỷ luật thép và theo dõi thói quen tập trung trực quan từ xa qua giao diện web Node-RED.

## 3. Danh mục phần cứng dự kiến
* **Vi điều khiển chính:** ESP32 Dev Board (tích hợp Wi-Fi kết nối MQTT Broker).
* **Cơ cấu chấp hành:** Động cơ Servo (MG90S hoặc tương đương) dùng làm chốt khóa nắp hộp tự động.
* **Cảm biến hiện diện:** Cảm biến khoảng cách siêu âm (HC-SR04) để nhận diện xem điện thoại đã được đặt vào trong hộp hay chưa.
* **Cảnh báo & Hiển thị:** Màn hình OLED 0.96 inch (I2C) hiển thị thời gian đếm ngược và còi Buzzer phát âm thanh cảnh báo khi có sự cố hoặc hoàn thành chu kỳ.
* **Nguồn cấp:** Mạch nguồn ổn định 5V cho hệ thống vi điều khiển và cơ cấu cơ khí.
