# Bài 4: Cảm biến gia tốc xác định hướng - Micro:bit V2 Go with Clips

## Mô tả dự án

Trong bài này, các bạn sẽ làm quen với cảm biến gia tốc được tích hợp sẵn trên mạch Micro:bit, cảm biến gia tốc giúp bạn xác định được góc nghiêng và hướng di chuyển vật lý của mạch Micro:bit, từ đó các bạn có thể thực hiện được các ứng dụng: hệ thống cân bằng điện tử, điều khiển robot bằng cử chỉ, các game tương tác thực tế ảo,...

![](/ex/less04/image/01_Microbit_accelerometer.png)  
Micro:bit accelerometer

## Các bước thực hiện

### Danh sách thiết bị

- 1 x Bo mạch Micro:bit
- 1 x Cáp MicroUSB
- 1 x Hộp pin 2 pin AAA và pin AAA

### Chuẩn bị trước dự án

- Tham khảo: [Hướng dẫn cài đặt phần mềm, nạp chương trình, cài đặt Extension mBlock cơ bản](https://github.com/makerlabvn/MakeCode-microbit)

### Các bước thực hiện

1. Tạo một dự án mới trong phần mềm MakeCode.
1. Bạn có thể lập trình kéo thả từng mã khối theo hình dưới trong mục **[Blocks]** hoặc copy đoạn code dưới và paste vào mục **[JavaScript]** để tiến hành nhanh hơn.
1. Nạp chương trình vào Micro:bit.

#### Blocks

![](/ex/less04/image/02_1050px-Microbit_V2_Go_Bai_4.png)  

#### Javascript

```js
// Khối "on start" - thực hiện 1 lần khi khởi động
basic.showString("play me")
basic.pause(100)
basic.clearScreen()

// Khối "forever" - vòng lặp chính của chương trình
basic.forever(function () {
  if (input.isGesture(Gesture.LogoUp)) {
    basic.showArrow(ArrowNames.North)
  } else if (input.isGesture(Gesture.LogoDown)) {
    basic.showArrow(ArrowNames.South)
  } else if (input.isGesture(Gesture.TiltLeft)) {
    basic.showArrow(ArrowNames.East)
  } else if (input.isGesture(Gesture.TiltRight)) {
    basic.showArrow(ArrowNames.West)
  } else if (input.isGesture(Gesture.ScreenUp)) {
    basic.showIcon(IconNames.Happy)
  } else if (input.isGesture(Gesture.ScreenDown)) {
    basic.showIcon(IconNames.Sad)
  }
})// Khối "on start" - thực hiện 1 lần khi khởi động
basic.showString("play me")
basic.pause(100)
basic.clearScreen()

// Khối "forever" - vòng lặp chính của chương trình
basic.forever(function () {
  if (input.isGesture(Gesture.LogoUp)) {
    basic.showArrow(ArrowNames.North)
  } else if (input.isGesture(Gesture.LogoDown)) {
    basic.showArrow(ArrowNames.South)
  } else if (input.isGesture(Gesture.TiltLeft)) {
    basic.showArrow(ArrowNames.East)
  } else if (input.isGesture(Gesture.TiltRight)) {
    basic.showArrow(ArrowNames.West)
  } else if (input.isGesture(Gesture.ScreenUp)) {
    basic.showIcon(IconNames.Happy)
  } else if (input.isGesture(Gesture.ScreenDown)) {
    basic.showIcon(IconNames.Sad)
  }
})
```

### Giải thích code
>
> Lưu ý:  
> Việc lấy các thông tin hướng, góc quay của cảm biến gia tốc tích hợp sẵn trong Micro:bit sẽ nằm trong mục "Input" của phần mềm MakeCode.
>
#### Chương trình sẽ hoạt động như sau

Trong khối **[ on start ]**.

1. Đầu tiên bo mạch sẽ hiển thị dòng chữ "play me" trên màn hình LED bằng khối **[ show string ]**.
1. Chờ 100ms (0.1s) qua khối **[ pause ]**.
1. Hiển thị xong sẽ xoá các nội dung hiển thị trên màn hình LED qua khối **[ clear screen ]**.
Phần khởi động này để chúng ta biết chương trình đã sẵn sàng.

Trong khối **[ forever ]**.

- Là một cấu trúc khối rẽ nhánh theo điều kiện **[ if else ]**.
- Mỗi một nhánh điều kiện được một khối logic **[ is gesture ]** kiểm tra.
- Nếu điều kiện đúng, thì khối **[ show arrow]** hay khối **[ show icon]** tương ứng được thực thi để hiển thị nội dung lên màn hình LED.  

Có tất cả 6 trường hợp xảy ra:

1. Khi bo mạch <u>hướng lên</u> → hiển thị mũi tên hướng **North**.
1. Khi bo mạch <u>hướng xuống</u> → hiển thị mũi tên hướng **South**.
1. Khi bo mạch <u>lật sang trái</u> → hiển thị mũi tên hướng **East**.
1. Khi bo mạch <u>lật sang phải</u> → hiển thị mũi tên hướng **West**.
1. Khi bo mạch <u>nằm ngửa</u> → hiển thị mặt `:)`.
1. Khi bo mạch <u>nằm sấp</u> → hiển thị mặt `:(`.

### Kết quả

Sau khi nạp chương trình, hãy tháo cáp MicroUSB và cấp nguồn cho Micro:bit bằng pin và hộp pin AAA trong bộ kit để dễ thao tác, thử dùng tay di chuyển Micro:bit theo các hướng để thấy chương trình hoạt động.

![](/ex/less04/image/03_1050px-Screenshot_2023-07-27_at_14.14.51.png)
Micro:bit Accelerometer Example

## Tài liệu tham khảo

- [Các khối Basic của Micro:Bit.](https://makecode.microbit.org/reference/basic)
- [Các khối Input của Micro:bit.](https://makecode.microbit.org/reference/input)

## Bài viết liên quan

- [Bộ Micro:bit V2 Go with Clips](/README.md)
- [Bài 3: Phát âm thanh với còi Buzzer](/ex/less03/README.md)
- [Bài 5: Đổ xúc xắc](/ex/less05/README.md)
