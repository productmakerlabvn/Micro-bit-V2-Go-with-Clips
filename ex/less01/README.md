# Bài 1: Hiển thị trên màn hình Led - Micro:bit V2 Go with Clips

## Mô tả dự án

Trên mạch Micro:bit có tích hợp một màn hình Led 5 x 5 giúp các bạn có thể hiển thị thông tin bất kỳ như ký hiệu, chữ, số,..., trong bài đầu tiên này chúng ta sẽ cùng tìm hiểu cách sử dụng màn hình này nhé!

![](/ex/less01/image/01_Cover.png)  
Micro:Bit Led Screen 5x5

## Các bước thực hiện

### Danh sách thiết bị

- 1x Bo mạch Micro:bit
- 1x Cáp MicroUSB

### Chuẩn bị trước dự án

- Tham khảo: Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode - MakerLab Wiki.

### Các bước thực hiện

1. Tạo một dự án mới trong phần mềm MakeCode.
1. Bạn có thể lập trình kéo thả từng mã khối theo hình dưới trong mục **[Blocks]** hoặc copy đoạn code dưới và paste vào mục **[JavaScript]** để tiến hành nhanh hơn.
1. Nạp chương trình vào Micro:bit.

#### Blocks

![](/ex/less01/image/02_1050px-Microbit_V2_Go_Bai_1.png)  

#### Javascript

```js
// Khối "on start" - thực hiện 1 lần khi khởi động
basic.showIcon(IconNames.Happy)
basic.pause(1000)
basic.showLeds(`
    . . # . .
    . # . # .
    . # # # .
    # # . # #
    . # # # .
    `)
basic.pause(1000)
basic.clearScreen()

// Khối "forever" - vòng lặp chính của chương trình
basic.forever(function () {
  for (let index = 0; index <= 9; index++) {
    basic.pause(1000)
    basic.showNumber(index)
  }
})
```

### Giải thích code
>
> Lưu ý:  
> Màu sắc của các khối lệnh sẽ tương ứng với các mục chứa khối lệnh trên phần mềm MakeCode, các bạn dựa vào màu sắc này để có thể tìm kiếm dễ dàng hơn.

Chương trình sẽ được đặt trong hai khối cơ bản của một chương trình chạy trên Micro:bit là Khối **[ on start ]** và Khối **[ forever ]**:  

Khối **[ on start ]** - các khối lệnh nằm trong khối này được thực hiện đầu tiên và chỉ thực hiện 1 lần duy nhất, khi Micro:bit khởi động.  

- Khối **[ show icon ]**: Hiển thị một Icon có sẵn lên màn hình Led của Micro:bit.
- Khối **[ Pause (ms) ]**: Chương trình tạm dừng trong khoảng thời gian mong muốn, đơn vị là mili giây (ms), 1000ms = 1s.
- Khối **[ show leds ]**: Hiển thị hình ảnh tuỳ chọn bất kỳ lên màn hình Led của Micro:bit.
- Khối **[ clear screen ]**: Xoá các nội dung hiển thị lên màn hình Led của Micro:bit.  

Khối **[ forever ]** - khối này được thực hiện sau khối **[ on start ]**, và được lặp lại liên tục cho đến khi Micro:bit tắt nguồn.

- Khối **[ for do ]**: giúp thay đổi giá trị "index" tăng dần từ 0 đến 9.
- Khối **[ show number ]**: Hiển thị giá trị dạn số (từ 0 đến 9) lên màn hình Led của Micro:bit.

### Kết quả

Sau khi hiển thị các Icon và hình ảnh, màn hình Led sẽ hiển thị số từ 0 đến 9 và lặp lại như hình:

![](/ex/less01/image/03_1050px-Screenshot_2023-07-26_at_16.39.50.png)  
Led Screen 5x5 Example Micro:bit

## Tài liệu tham khảo

- [Các khối Basic của Micro:bit.](https://makecode.microbit.org/reference/basic)

## Bài viết liên quan

[Bộ Micro:bit V2 Go with Clips](/README.md)
[Bài 2: Nhận tín hiệu từ nút nhấn](/ex/less02/README.md)
