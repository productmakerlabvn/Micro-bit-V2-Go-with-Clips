# Bài 2: Nhận tín hiệu từ nút nhấn - Micro:bit V2 Go with Clips

## Mô tả dự án

Trong bài này các bạn sẽ học cách sử dụng hai nút nhấn tích hợp sẵn trên mạch Micro:bit để tương tác với màn hình Led, từ đó có thể ứng dụng để thực hiện các chức năng điều khiển bằng nút nhấn này.

![](/ex/less02/image/01_EGXriFLX0AEJkk5.png)  
Micro:bit button

## Các bước thực hiện

### Danh sách thiết bị

- 1x Bo mạch Micro:bit.
- 1x Cáp MicroUSB.

### Chuẩn bị trước dự án

- Tham khảo: Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode - MakerLab Wiki.

### Các bước thực hiện

1. Tạo một dự án mới trong phần mềm MakeCode.
1. Bạn có thể lập trình kéo thả từng mã khối theo hình dưới trong mục [Blocks] hoặc copy đoạn code dưới và paste vào mục [JavaScript] để tiến hành nhanh hơn.
1. Nạp chương trình vào Micro:bit.

#### Blocks

![](/ex/less02/image/02_1050px-Microbit_V2_Go_Bai_2.png)

#### Javascript

```js
// Khối input - thực hiện khi nhấn nút A
input.onButtonPressed(Button.A, function () {
  enable = 0
  basic.showLeds(`
        . . # . .
        . # . . .
        # # # # #
        . # . . .
        . . # . .
        `)
})

// Khối input - thực hiện khi nhấn cả hai nút A và B cùng lúc
input.onButtonPressed(Button.AB, function () {
  enable = 1
  while (enable) {
    blink()
  }
})

// Khối input - thực hiện khi nhấn nút B
input.onButtonPressed(Button.B, function () {
  enable = 0
  basic.showLeds(`
        . . # . .
        . . . # .
        # # # # #
        . . . # .
        . . # . .
        `)
})

// Khối "blink" - do người dùng tạo
function blink() {
  basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        `)
  basic.showLeds(`
        . . . . .
        . . . . .
        . . # . .
        . . . . .
        . . . . .
        `)
  basic.showLeds(`
        . . . . .
        . . # . .
        . # # # .
        . . # . .
        . . . . .
        `)
  basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . . # . .
        `)
  basic.showLeds(`
        . . . . .
        . . # . .
        . # # # .
        . . # . .
        . . . . .
        `)
  basic.showLeds(`
        . . . . .
        . . . . .
        . . # . .
        . . . . .
        . . . . .
        `)
}

// Khai báo các biến
let enable = 0

// Khối "on start" - thực hiện 1 lần khi khởi động
basic.showString("A or B")
basic.pause(100)
basic.showIcon(IconNames.Happy)
basic.pause(100)
basic.clearScreen()
```

### Giải thích code
>
> Lưu ý:
> Màu sắc của các khối lệnh sẽ tương ứng với các mục chứa khối lệnh trên phần mềm MakeCode, các bạn dựa vào màu sắc này để có thể tìm kiếm dễ dàng hơn.

Khối **[ on start ]** - các khối lệnh nằm trong khối này được thực hiện đầu tiên và chỉ thực hiện 1 lần duy nhất, khi Micro:bit khởi động.

- Khối **[ show string ]**: Hiển thị chuỗi ký tự lên màn hình Led của Micro:bit.
- Khối **[ show icon ]**: Hiển thị một Icon có sẵn lên màn hình Led của Micro:bit.
- Khối **[ Pause (ms) ]**: Chương trình tạm dừng trong khoảng thời gian mong muốn, đơn vị là mili giây (ms), 1000ms = 1s.
- Khối **[ clear screen ]**: Xoá các nội dung hiển thị lên màn hình Led của Micro:bit.
Các khối sự kiện: Trong chương trình này sẽ không có khối **[ forever ]** mà thay vào đó là các khối sự kiện như sau:

- Khối **[ on button A pressed ]**: Các khối lệnh nằm trong khối này được chạy 1 lần khi nút A được nhấn.
- Khối **[ on button A+B pressed ]**: Các khối lệnh nằm trong khối này được chạy 1 lần khi nút A và B được nhấn đồng thời.
- Khối **[ on button B pressed ]**: Các khối lệnh nằm trong khối này được chạy 1 lần khi nút B được nhấn.
  - Khối **[ set to ]**: Thiết lập giá trị cho biến "enable".
  - Khối **[ show leds ]**: Hiển thị hình ảnh tuỳ chọn bất kỳ lên màn hình Led của Micro:bit.
  - Khối **[ while do ]**: Khi điều khiện trong "while" đúng (khác 0), chạy các khối lệnh phía trong "do".
Khối **[ function ]**:

- Đây là khối chức năng do người dùng tạo và sẽ được gọi bằng khối **[ call ]**: .

### Kết quả

Khi nhấn **nút A** sẽ hiển thị kí tự `←` trên màn hình LED, tương tự nhấn **nút B** sẽ hiển thị `→`, và nếu như bạn nhấn đồng thời cả 2 nút **A+B** cùng lúc, bo mạch sẽ chạy một hiệu ứng hiển thị đặc biệt.

![](/ex/less02/image/03_1050px-Screenshot_2023-07-26_at_16.13.22.png)
Button Example Micro:bit

## Tài liệu tham khảo

- [Các khối Basic của Micro:bit.](https://makecode.microbit.org/reference/basic)
- [Các khối Input của Micro:bit.](https://makecode.microbit.org/reference/input)

## Bài viết liên quan

- [Bộ Micro:bit V2 Go with Clips](/README.md)
- [Bài 1: Hiển thị trên màn hình Led](/ex/less01/README.md)
- [Bài 3: Phát âm thanh với còi Buzzer](/ex/less03/README.md)
