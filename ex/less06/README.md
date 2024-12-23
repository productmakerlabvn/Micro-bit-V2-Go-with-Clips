# Bài 6: La bàn số - Micro:bit V2 Go with Clips

## Mô tả dự án

Trong bài này, các bạn sẽ làm quen với cảm biến la bàn số được tích hợp sẵn trên mạch Micro:bit, cảm biến la bàn số giúp bạn xác định được hướng di chuyển của mạch Micro:bit theo từ trường của trái đất, từ đó các bạn có thể thực hiện các ứng dụng cần xác định phương hướng như: la bàn, xác định vị trí, hướng di chuyển,...

![](/ex/less06/image/01_750px-Microbit_compasses.jpg)   
Micro:bit compasses

## Các bước thực hiện

### Danh sách thiết bị

- 1 x Bo mạch Micro:bit.
- 1 x Cáp MicroUSB.
- 1 x Hộp pin 2 pin AAA và pin AAA

### Chuẩn bị trước dự án

- Tham khảo: [Hướng dẫn cài đặt phần mềm, nạp chương trình, cài đặt Extension mBlock cơ bản](https://github.com/makerlabvn/MakeCode-microbit)

### Các bước thực hiện

1. Tạo một dự án mới trong phần mềm MakeCode.
1. Bạn có thể lập trình kéo thả từng mã khối theo hình dưới trong mục **[Blocks]** hoặc copy đoạn code dưới và paste vào mục **[JavaScript]** để tiến hành nhanh hơn.
1. Nạp chương trình vào Micro:bit.

#### Blocks

![](/ex/less06/image/02_675px-Microbit_V2_Go_Bai_7.png)  

#### Javascript

```js
// Khối input - thực hiện khi nhấn cả hai nút A và B cùng lúc
input.onButtonPressed(Button.AB, function () {
  input.calibrateCompass()
})

// Khai báo các biến
let degrees = 0

// Khối "forever" - vòng lặp chính của chương trình
basic.forever(function () {
  degrees = input.compassHeading()
  if (degrees < 22.5) {
    basic.showArrow(ArrowNames.North)
  } else if (degrees < 67.5) {
    basic.showArrow(ArrowNames.NorthEast)
  } else if (degrees < 112.5) {
    basic.showArrow(ArrowNames.East)
  } else if (degrees < 157.5) {
    basic.showArrow(ArrowNames.SouthEast)
  } else if (degrees < 202.5) {
    basic.showArrow(ArrowNames.South)
  } else if (degrees < 247.5) {
    basic.showArrow(ArrowNames.SouthWest)
  } else if (degrees < 292.5) {
    basic.showArrow(ArrowNames.West)
  } else if (degrees < 337.5) {
    basic.showArrow(ArrowNames.NorthWest)
  } else {
    basic.showArrow(ArrowNames.North)
  }
})
```

### Giải thích code

- Trước khi chương trình đi vào hoạt động, micro:Bit sẽ <u>tự động "hiệu chỉnh"</u> lại cảm biến la bàn số (nếu chưa). Lúc này màn hình Led sẽ hiển thị dòng chữ: `TILT TO FILL SCREEN`.
- Hoặc nếu bạn muốn <u>tự "hiệu chỉnh"</u> lại để tăng độ chính xác, bạn có thể nhấn đồng thời **2 nút A+B** để thực thi khối [ calibrate compass ].
- Sau khi màn hình Led chạy xong dòng thông báo trên, bạn sẽ cần xoay bo micro:Bit mọi hướng sao cho làm sáng hết tất cả đèn Led trên màn hình.
- Khi đã hiệu chỉnh thành công, micro:Bit sẽ hiển thị **"mặt cười"** cho bạn biết đã kết thúc quá trình hiệu chỉnh.

#### Chương trình sẽ hoạt động như sau

Trong khối **[ forever ]**.

- Chương trình sẽ lấy giá trị góc quay của cảm biến la bàn số bằng khối **[ compass heading (º) ]** (từ 0º đến 359º) để lưu vào biến "degrees" qua khối **[ set to ]**.
- Dựa theo giá trị mà cảm biến trả về, ta sử dụng khối điều khiện **[ if else ]** để hiển thị 8 trường hợp xảy ra ra màn hình led qua khối **[ show arrow ]**:
    1. Giá trị nằm trong khoảng `(337.5º - 22.5º)`, màn hình Led hiển thị mũi tên hướng North **[↑]**, tức đầu bo micro:Bit đang hướng về phía Bắc.
    2. Trong khoảng `(22.5º - 67.5º)`, màn hình Led hiển thị mũi tên hướng North East **[↗]**.
    3. Trong khoảng `(67.5º - 112.5º)`, màn hình Led hiển thị mũi tên hướng East **[→]**.
    4. Trong khoảng `(112.5º - 157.5º)`, màn hình Led hiển thị mũi tên hướng South East **[↘]**.
    5. Trong khoảng `(157.5º - 202.5º)`, màn hình Led hiển thị mũi tên hướng South **[↓]**.
    6. Trong khoảng `(202.5º - 247.5º)`, màn hình Led hiển thị mũi tên hướng South West **[↙]**.
    7. Trong khoảng `(247.5º - 292.5º)`, màn hình Led hiển thị mũi tên hướng West **[←]**.
    8. Trong khoảng `(292.5º - 337.5º)`, màn hình Led hiển thị mũi tên hướng North West **[↖]**.

### Kết quả

Sau khi nạp chương trình, hãy tháo cáp MicroUSB và cấp nguồn cho Micro:bit bằng pin và hộp pin AAA trong bộ kit để dễ thao tác, thử cầm Micro:bit trên tay và xoay theo các hướng khác nhau để thấy chương trình hoạt động, mũi tên trên "la bàn Micro:bit" sẽ luôn chỉ về hướng Bắc.

![](/ex/less06/image/03_1050px-Screenshot_2023-07-31_at_13.24.50.png)  
Micro:bit Compass Example

## Tài liệu tham khảo

- [Các khối Basic của Micro:bit.](https://makecode.microbit.org/reference/basic)
- [Các khối Input của Micro:bit.](https://makecode.microbit.org/reference/input)

## Bài viết liên quan

- [Bộ Micro:bit V2 Go with Clips](/README.md)
- [Bài 5: Đổ xúc xắc](/ex/less05/README.md)
- [Bài 7: Máy đo thông số môi trường](/ex/less07/README.md)
