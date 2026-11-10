****# IoT-Pomodoro-Lock-Box




## 1. Giới thiệu đề tài

Đề tài xây dựng một thiết bị phần cứng thông minh ứng dụng vi điều khiển ESP32, kết hợp giao thức truyền thông MQTT và hệ thống giám sát Node-RED Dashboard. Thiết bị này đóng vai trò như một "hộp khóa vật lý" tự động quản lý thời gian tập trung làm việc và học tập dựa trên phương pháp Pomodoro quen thuộc.

## 2. Vấn đề thực tế và giải pháp

* Trong thời đại số hiện nay, tình trạng nghiện smartphone và thói quen cầm điện thoại vô thức khi đang học tập hoặc làm việc làm giảm nghiêm trọng hiệu suất cá nhân của học sinh, sinh viên.
  
*  Các ứng dụng đếm giờ Pomodoro cài sẵn trên điện thoại tỏ ra kém hiệu quả vì người dùng vẫn có thể dễ dàng chạm tay vào thiết bị bất cứ lúc nào để lướt mạng xã hội.
  
*  Đề tài tạo ra một sự cách ly vật lý. Khi bắt đầu chu kỳ tập trung với thời gian đã được người dùng cài đặt, điện thoại sẽ bị khóa chặt bên trong hộp nhờ cơ chế điều khiển của động cơ servo. Người dùng không thể lấy ra trừ khi hoàn thành thời gian hoặc hệ thống ghi nhận kết quả lên đám mây qua MQTT, nếu người dùng cố ý vi phạm luật thì hệ thống cảm biến sẽ báo hiệu như còi buzzer kêu và đèn led nhấp nháy liên tục và hiển thị thông báo thất bại trên giao diện dashboard. Điều này giúp rèn luyện kỷ luật thép và theo dõi thói quen tập trung trực quan từ xa qua giao diện web Node-RED.

## 3. Danh mục phần cứng dự kiến
* Vi điều khiển  ESP32 Dev Board (tích hợp Wi-Fi kết nối MQTT Broker).
* Động cơ Servo  dùng làm chốt khóa nắp hộp tự động.
* Cảm biến khoảng cách siêu âm HC-SR04 để nhận diện xem điện thoại đã được đặt vào trong hộp hay chưa.
* Màn hình hiển thị thời gian đếm ngược và còi Buzzer phát âm thanh cảnh báo khi có sự cố hoặc hoàn thành chu kỳ.
  
****
