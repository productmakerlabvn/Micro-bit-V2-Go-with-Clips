# Bài 7: Máy đo thông số môi trường - Micro:bit V2 Go with Clips

## Mô tả dự án

Trong bài này các bạn sẽ học cách sử dụng cảm biến ánh sáng & cảm biến nhiệt độ được tích hợp sẵn trên mạch Micro:bit, từ đó chế tạo một máy đo thông số môi trường đơn giản với hai thông số là nhiệt độ và ánh sáng.

![](/ex/less07/image/01_750px-Microbit_light_and_Temperature_Sensor.jpg)  
Micro:bit Light & Temperature Sensor

## Các bước thực hiện

### Danh sách thiết bị

- 1 x Bo mạch Micro:bit
- 1 x Cáp MicroUSB
- 1 x Hộp pin 2 pin AAA và pin AAA

### Chuẩn bị trước dự án

- Tham khảo: [Hướng dẫn cài đặt phần mềm, nạp chương trình, cài đặt Extension mBlock cơ bản](https://github.com/makerlabvn/MakeCode-microbit)

### Các bước thực hiện

1. Tạo một dự án mới trong phần mềm MakeCode.
2. Bạn có thể lập trình kéo thả từng mã khối theo hình dưới trong mục **[Blocks]** hoặc copy đoạn code dưới và paste vào mục **[JavaScript]** để tiến hành nhanh hơn.
3. Nạp chương trình vào Micro:bit.

#### Blocks

![](/ex/less07/image/02_1350px-Microbit_V2_Go_Bai_8.png)

#### Javascript

```js
// Khối input - thực hiện khi nhấn nút A
input.onButtonPressed(Button.A, function () {
  led.stopAnimation()
  mode = 0
  basic.showString("TEMPE")
  mode = 1
})

// Khối input - thực hiện khi nhấn nút B
input.onButtonPressed(Button.B, function () {
  led.stopAnimation()
  mode = 0
  basic.showString("LIGHT")
  mode = 2
})

// Khai báo các biến
let mode = 0

// Khối "on start" - thực hiện 1 lần khi khởi động
basic.showIcon(IconNames.Happy)
basic.pause(1000)
basic.clearScreen()
mode = 0

// Khối "forever" - vòng lặp chính của chương trình
basic.forever(function () {
  if (mode == 2) {
    led.plotBarGraph(
      input.lightLevel(),
      255
    )
  }
})

// Khối "loop" - vòng lặp phụ
loops.everyInterval(5000, function () {
  if (mode == 1) {
    basic.showString("" + input.temperature() + "\"C")
  }
})
```

## Giải thích code

Chương trình hoạt động:

Trong khối **[on start]**.

- Đầu tiên Micro:bit sẽ hiển thị "mặt cười" trong 1 giây rồi tắt, bước này để chúng ta biết bo mạch đã sẵn sàng hoạt động.
- Đồng thời biến "mode" được đặt thành 0.

Vai trò của biến "mode":

- Để cho chương trình biết phải hoạt động ở chế độ nào.
  - Bằng 0, nghĩa là không làm gì cả.
  - Bằng 1, thì sử dụng cảm biến Nhiệt độ.
  - Bằng 2, thì sử dụng cảm biến Ánh sáng.

Các khối sự kiện:

- Nhấn nút A để thực thi khối **[on button A pressed]**.
  - Đầu tiên thực thi khối **[stop animation]** để dừng việc hiển thị trên màn hình Led (nếu đang có).
  - Đặt biến "mode" thành 0, để tạm dừng việc sử dụng các cảm biến.
  - Hiển thị dòng chữ "TEMP" (viết tắt của Temperature), trên màn hình Led để thông báo chuẩn bị vào chế độ đọc Nhiệt độ môi trường.
  - Đặt biến "mode" thành 1 để micro:Bit được sử dụng cảm biến Nhiệt độ.

- Nhấn nút B để thực thi khối **[on button B pressed]**.
  - Đầu tiên thực thi khối **[stop animation]** để dừng việc hiển thị trên màn hình Led (nếu đang có).
  - Đặt biến "mode" thành 0, để tạm dừng việc sử dụng các cảm biến.
  - Hiển thị dòng chữ "LIGHT", trên màn hình Led để thông báo chuẩn bị vào chế độ đọc Ánh sáng môi trường.
  - Đặt biến "mode" thành 2 để micro:Bit được sử dụng cảm biến Ánh sáng.

Vai trò của khối **[forever]**:

- Khối này đảm nhiệm thực hiện đọc cảm biến Ánh sáng với tần suất liên tục.
  - Giá trị cường độ ánh sáng lấy từ khối **[light level]**, với dãi giá trị trả về "từ 0 đến 255".
  - Sau đó được đưa vào khối **[plot bar graph of ... up to "255"]** để hiển thị mức độ ánh sáng trên màn hình Led.

Vai trò của khối **[every "5000" ms]**:

- Khối này đảm nhiệm thực hiện đọc cảm biến Nhiệt độ với tần suất 5 giây mỗi lần.
  - Giá trị nhiệt độ lấy từ khối **[temperature (ºC)]**, đơn vị là độ Celsius.
  - Sau đó được đưa vào khối **[join...]** để tạo thành 1 chuỗi văn bản.
  - Chuỗi văn bản này được đưa tiếp vào khối **[show string...]** để hiển thị nội dung lên màn hình Led.

## Kết quả

Sau khi chương trình khởi động xong, nhấn nút A để đọc Nhiệt độ, nhấn nút B để đọc Ánh sáng.

![](/ex/less07/image/03_1050px-Microbit_light_n_temp_sensor.png)  
Micro:bit Light & Temperature sensor Example

## Tài liệu tham khảo

- [Các khối Basic của Micro:bit.](https://makecode.microbit.org/reference/basic)
- [Các khối Input của Micro:bit.](https://makecode.microbit.org/reference/input)
- [Các khối Led của Micro:bit.](https://makecode.microbit.org/reference/led)

## Bài viết liên quan

- [Bộ Micro:bit V2 Go with Clips](/README.md)
- [Bài 6: La bàn số](/ex/less06/README.md)
- [Bài 8: Đàn Piano lá cây](/ex/less08/README.md)
