****# IoT-Pomodoro-Lock-Box




## 1. Giới thiệu đề tài

Đề tài xây dựng một thiết bị phần cứng thông minh ứng dụng vi điều khiển ESP32, kết hợp giao thức truyền thông MQTT và hệ thống giám sát Node-RED Dashboard. Thiết bị này đóng vai trò như một "hộp khóa vật lý" tự động quản lý thời gian tập trung làm việc và học tập dựa trên phương pháp Pomodoro quen thuộc.

## 2. Vấn đề thực tế và giải pháp

* Trong thời đại số hiện nay, tình trạng nghiện smartphone và thói quen cầm điện thoại vô thức khi đang học tập hoặc làm việc làm giảm nghiêm trọng hiệu suất cá nhân của học sinh, sinh viên.
  
*  Các ứng dụng đếm giờ Pomodoro cài sẵn trên điện thoại tỏ ra kém hiệu quả vì người dùng vẫn có thể dễ dàng chạm tay vào thiết bị bất cứ lúc nào để lướt mạng xã hội.
  
*  Đề tài tạo ra một sự cách ly vật lý. Khi bắt đầu chu kỳ tập trung với thời gian đã được người dùng cài đặt, điện thoại sẽ bị khóa chặt bên trong hộp nhờ cơ chế điều khiển của động cơ servo. Người dùng không thể lấy ra trừ khi hoàn thành thời gian hoặc hệ thống ghi nhận kết quả lên đám mây qua MQTT, nếu người dùng cố ý vi phạm luật thì hệ thống cảm biến sẽ báo hiệu như còi buzzer kêu và đèn led nhấp nháy liên tục và hiển thị thông báo thất bại trên giao diện dashboard. Điều này giúp rèn luyện kỷ luật thép và theo dõi thói quen tập trung trực quan từ xa qua giao diện web Node-RED.

## 3. Danh mục phần cứng dự kiến

| STT | Tên linh kiện | Số lượng | Chức năng |
| :---: | :--- | :---: | :--- |
| 1 | **Vi điều khiển ESP32 Dev Board**<br><br><img width="150" src="https://github.com/user-attachments/assets/a7cd7388-2dfb-45e1-a1d7-4b225a7369f7" /> | 1 | - Quản lý logic toàn bộ hệ thống.<br>- Xử lý dữ liệu từ cảm biến siêu âm và điều khiển động cơ servo, màn hình, còi buzzer, đèn LED.<br>- Kết nối Wi-Fi và truyền tải trạng thái qua giao thức MQTT. |
| 2 | **Động cơ Servo SG90**<br><br><img width="120" src="https://github.com/user-attachments/assets/a2b707d8-adc2-4d07-9f25-6cd2decf6490" /> | 1 | - Nhận xung PWM từ vi điều khiển để đóng/mở chốt khóa nắp hộp tự động trong suốt chu kỳ Pomodoro. |
| 3 | **Cảm biến khoảng cách siêu âm HC-SR04**<br><br><img width="120" src="https://github.com/user-attachments/assets/ebb3e66f-a2f6-4dfc-a3d0-a42d09078284" /> | 1 | - Đo khoảng cách để nhận diện xem điện thoại đã được đặt vào đúng vị trí bên trong hộp hay chưa trước khi kích hoạt khóa. |
| 4 | **Màn hình OLED 1.3 inch**<br><br><img width="120" src="https://github.com/user-attachments/assets/0f653fdb-d065-4647-be0f-9f0d7740290b" /> | 1 | - Giao tiếp qua chuẩn I2C.<br>- Hiển thị thời gian đếm ngược của chu kỳ tập trung và trạng thái hoạt động trực tiếp tại thiết bị. |
| 5 | **Còi Buzzer**<br><br><img width="120" src="https://github.com/user-attachments/assets/6b3d90b9-ba7f-455d-9143-01d5557d8a85" /> | 1 | - Phát âm thanh cảnh báo khi phát hiện hành vi cố tình mở hộp trái phép hoặc báo hiệu hoàn thành chu kỳ Pomodoro. |
| 6 | **Đèn LED báo hiệu**<br><br><img width="120" src="https://github.com/user-attachments/assets/ab0ca55f-c28e-4dbb-9022-3b171b850c57" /> | 1 | - Cung cấp tín hiệu cảnh báo trực quan tại chỗ.<br>- Hiển thị trạng thái hoạt động. |

## 4. Sơ đồ khối kết nối

<img width="835" height="549" alt="IOT_ROOM_SODOKHOI" src="https://github.com/user-attachments/assets/211e367a-bca9-42f2-bb77-b9116e5c6ce4" />


  
* ## 5. Nguyên lý hoạt động
* Khởi động: Người dùng đặt điện thoại vào hộp, cảm biến xác nhận thiết bị nằm đúng vị trí.
* Khóa hộp: Nhấn nút kích hoạt, ESP32 điều khiển servo đóng chốt khóa và bắt đầu đếm ngược thời gian Pomodoro.
* Giám sát: MQTT truyền tải trạng thái thời gian thực về Node-RED Dashboard để hiển thị trực quan.
* Xử lý hoàn thành: Hết thời gian, hộp tự động mở khóa, còi báo hiệu thành công.
* Xử lý vi phạm: Nếu mở hộp sớm khi chưa hết giờ, còi buzzer hú lớn, đèn LED nhấp nháy và gửi cảnh báo về Dashboard qua MQTT.

## 6. Lưu đồ thuật toán

<img width="724" height="550" alt="luu_do_thuat_toan LOCKBOX" src="https://github.com/user-attachments/assets/bc1b1998-5063-4207-9cbb-5606c59d91bc" />



## 7. Tài liệu tham khảo & Datasheet linh kiện

* [ESP32 DevKit Datasheet - Espressif Systems](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf)
* [HC-SR04 Ultrasonic Sensor Datasheet](https://cdn.sparkfun.com/datasheets/Sensors/Proximity/HCSR04.pdf)
* [PubSubClient MQTT Library Documentation](https://github.com/knolleary/pubsubclient)
* [Node-RED Documentation](https://nodered.org/docs/)
  
****
