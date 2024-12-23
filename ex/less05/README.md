# Bài 5: Đổ xúc xắc - Micro:bit V2 Go with Clips

## Mô tả dự án

Trong bài này các bạn sẽ kết hợp giữa cảm biến gia tốc để phát hiện chuyển động và màn hình Led để tạo ra trò chơi đổ xúc xắc trên Micro:bit, hãy cùng làm nhé!

![](/ex/less05/image/01_7aee32e26ee.jpg)  
Micro:bit Dice

## Các bước thực hiện

### Danh sách thiết bị

- 1 x Bo mạch Micro:bit
- 1 x Cáp MicroUSB.
- 1 x Hộp pin 2 pin AAA và pin AAA

### Chuẩn bị trước dự án

- Tham khảo: [Hướng dẫn cài đặt phần mềm, nạp chương trình, cài đặt Extension mBlock cơ bản](https://github.com/makerlabvn/MakeCode-microbit)

### Các bước thực hiện

1. Tạo một dự án mới trong phần mềm MakeCode.
1. Bạn có thể lập trình kéo thả từng mã khối theo hình dưới trong mục [Blocks] hoặc copy đoạn code dưới và paste vào mục [JavaScript] để tiến hành nhanh hơn.
1. Nạp chương trình vào Micro:bit.

#### Blocks

![](/ex/less05/image/02_1049px-Microbit_V2_Go_Bai_5.png)  

#### Javascript

```js
// Khối input - thực hiện khi lắc bo mạch
input.onGesture(Gesture.Shake, function () {
  basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        `)
  zigzac = randint(1, 6)
  if (zigzac == 1) {
    basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
  } else if (zigzac == 2) {
    basic.showLeds(`
            . . # . .
            . . . . .
            . . . . .
            . . . . .
            . . # . .
            `)
  } else if (zigzac == 3) {
    basic.showLeds(`
            . . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . .
            `)
  } else if (zigzac == 4) {
    basic.showLeds(`
            # . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . #
            `)
  } else if (zigzac == 5) {
    basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . #
            `)
  } else if (zigzac == 6) {
    basic.showLeds(`
            # . . . #
            . . . . .
            # . . . #
            . . . . .
            # . . . #
            `)
  }
})

// Khai báo các biến
let zigzac = 0

// Khối "on start" - thực hiện 1 lần khi khởi động
basic.showString("shake me")
basic.pause(1000)
basic.showIcon(IconNames.Happy)
basic.pause(1000)
```

### Giải thích code

<u>Chương trình hoạt động:</u>

Trong khối **[ on start ]**.

1. Đầu tiên Micro:bit sẽ hiển thị dòng chữ *"shake me"* trên màn hình LED bằng khối **[ show string ]**.
1. Chờ 1000ms (1s) qua khối **[ pause ]**.
1. Sau đó hiển thị *"mặt cười"* lên qua khối **[ show icon ]**.
1. Tiếp tục chờ 1000ms (1s) qua khối **[ pause ]**.  

Phần khởi động này để chương trình nói cho chúng ta biết là Micro:bit đã sẵn sàng "bị lắc".

<u>Khối sự kiện:</u>

Khối điều kiện **[ on shake ]** sẽ chạy khi Micro:bit bị "lắc" (shake).

- Đầu tiên sẽ cho tắt đèn trên màn hình LED qua việc để trống khối **[ show leds ]**, bước này giúp đôi mắt chúng ta nhìn thấy được sự thay đổi giữa mỗi lần đổ xúc xắc.
- Tiếp theo ta chọn một giá trị ngẫu nhiên "từ 1 đến 6" bằng khối **[ pick random ]** và lưu vào biến **"zigzac"** qua khối **[ set to ]**.
- Dựa theo giá trị mà biến **"zigzac"** nhận được ta sử dụng khối điều kiện **[ if else ]** để hiển thị 6 trường hợp có thể xảy ra qua khối **[ show leds ]**:
    1. Biến **"zigzac"** nhận được số `1` → hiển thị `⚀` .
    1. Tương tự là số `2` → sẽ hiển thị `⚁`.
    1. Là số `3` → hiển thị `⚂`.
    1. Là số `4` → hiển thị `⚃`.
    1. Là số `5` → hiển thị `⚄`.
    1. Là số `6` → hiển thị `⚅`.

### Kết quả

Sau khi nạp chương trình, hãy tháo cáp MicroUSB và cấp nguồn cho Micro:bit bằng pin và hộp pin AAA trong bộ kit để dễ thao tác, thử dùng tay "lắc" Micro:bit để thấy chương trình hoạt động.

![](/ex/less05/image/03_1050px-Microbit_dice.png)  
Microbit Dice Example

## Tài liệu tham khảo

- [Các khối Basic của Micro:bit.](https://makecode.microbit.org/reference/basic)
- [Các khối Input của Micro:bit.](https://makecode.microbit.org/reference/input)

## Bài viết liên quan

- [Bộ Micro:bit V2 Go with Clips](/README.md)
- [Bài 4: Cảm biến gia tốc xác định hướng](/ex/less04/README.md)
- [Bài 6: La bàn số](/ex/less06/README.md)
