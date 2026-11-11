****# IoT-Pomodoro-Lock-Box




## 1. Giới thiệu đề tài

Đề tài xây dựng một thiết bị phần cứng thông minh ứng dụng vi điều khiển ESP32, kết hợp giao thức truyền thông MQTT và hệ thống giám sát Node-RED Dashboard. Thiết bị này đóng vai trò như một "hộp khóa vật lý" tự động quản lý thời gian tập trung làm việc và học tập dựa trên phương pháp Pomodoro quen thuộc.

## 2. Vấn đề thực tế và giải pháp

* Trong thời đại số hiện nay, tình trạng nghiện smartphone và thói quen cầm điện thoại vô thức khi đang học tập hoặc làm việc làm giảm nghiêm trọng hiệu suất cá nhân của học sinh, sinh viên.
  
*  Các ứng dụng đếm giờ Pomodoro cài sẵn trên điện thoại tỏ ra kém hiệu quả vì người dùng vẫn có thể dễ dàng chạm tay vào thiết bị bất cứ lúc nào để lướt mạng xã hội.
  
*  Đề tài tạo ra một sự cách ly vật lý. Khi bắt đầu chu kỳ tập trung với thời gian đã được người dùng cài đặt, điện thoại sẽ bị khóa chặt bên trong hộp nhờ cơ chế điều khiển của động cơ servo. Người dùng không thể lấy ra trừ khi hoàn thành thời gian hoặc hệ thống ghi nhận kết quả lên đám mây qua MQTT, nếu người dùng cố ý vi phạm luật thì hệ thống cảm biến sẽ báo hiệu như còi buzzer kêu và đèn led nhấp nháy liên tục và hiển thị thông báo thất bại trên giao diện dashboard. Điều này giúp rèn luyện kỷ luật thép và theo dõi thói quen tập trung trực quan từ xa qua giao diện web Node-RED.

## 3. Danh mục phần cứng dự kiến
* Vi điều khiển  ESP32 Dev Board.

<img width="433" height="176" alt="ESP32" src="https://github.com/user-attachments/assets/a7cd7388-2dfb-45e1-a1d7-4b225a7369f7" />

  
* Động cơ Servo  dùng làm chốt khóa nắp hộp tự động.

<img width="210" height="178" alt="servo_SG90" src="https://github.com/user-attachments/assets/a2b707d8-adc2-4d07-9f25-6cd2decf6490" />

  
* Cảm biến khoảng cách siêu âm HC-SR04 để nhận diện xem điện thoại đã được đặt vào trong hộp hay chưa.

<img width="225" height="190" alt="cam_bien_sieu_am_HCSR04" src="https://github.com/user-attachments/assets/ebb3e66f-a2f6-4dfc-a3d0-a42d09078284" />

  
* Màn hình oled 1.3 inch hiển thị thời gian đếm ngược và trạng thái.
  
<img width="239" height="205" alt="oled_1 3inch" src="https://github.com/user-attachments/assets/0f653fdb-d065-4647-be0f-9f0d7740290b" />


* Còi Buzzer

  <img width="254" height="117" alt="BUZZER" src="https://github.com/user-attachments/assets/6b3d90b9-ba7f-455d-9143-01d5557d8a85" />

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
* [SG90 TowerPro Micro Servo Specification](https://www.electronicshub.org/mg90s-servo-motor/)
* [HC-SR04 Ultrasonic Sensor Datasheet](https://cdn.sparkfun.com/datasheets/Sensors/Proximity/HCSR04.pdf)
* [Piezo Buzzer Working Principle - Electronics Hub](https://www.electronicshub.org/piezo-buzzer/)
* [PubSubClient MQTT Library Documentation](https://github.com/knolleary/pubsubclient)
* [Node-RED Documentation](https://nodered.org/docs/)
  
****
