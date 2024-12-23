# Bài 8: Đàn Piano lá cây - Micro:bit V2 Go with Clips

## Mô tả dự án

Trong bài này các bạn sẽ sử dụng các chân tín hiệu có chức năng cảm ứng chạm (Touch Sensing) trên Micro:bit là: P0, P1, P2 để tạo một chiếc đàn Piano từ lá cây, các bạn cũng có thể thử trên các vật thể dẫn điện (chứa nước, kim loại) khác như: giấy bạc, thìa, trái cây,...

![](/ex/less08/image/01_750px-Fruit-Keyboard-no-wires_bb.png)  
Micro:bit Touch Sensing Pins

## Các bước thực hiện

### Danh sách thiết bị

- 1 x Bo mạch Micro:bit
- 1 x Cáp MicroUSB
- 1 x Hộp pin 2 pin AAA và pin AAA
- 4 x Dây nối kẹp cá sấu

### Chuẩn bị trước dự án

- Tham khảo: [Hướng dẫn cài đặt phần mềm, nạp chương trình, cài đặt Extension mBlock cơ bản](https://github.com/makerlabvn/MakeCode-microbit)

### Các bước thực hiện

1. Tạo một dự án mới trong phần mềm MakeCode.
2. Bạn có thể lập trình kéo thả từng mã khối theo hình dưới trong mục **[Blocks]** hoặc copy đoạn code dưới và paste vào mục **[JavaScript]** để tiến hành nhanh hơn.
3. Nạp chương trình vào Micro:bit.

#### Blocks

![](/ex/less08/image/02_1500px-Microbit_V2_Go_Bai_6.png)

#### Javascript

```js
// Khối "Button 0" - do người dùng tạo
function Button_0() {
  if (input.pinIsPressed(TouchPin.P0)) {
    line0 = 0
  } else {
    line0 = 1
  }
}

// Khối "Button 1" - do người dùng tạo
function Button_1() {
  if (input.pinIsPressed(TouchPin.P1)) {
    line1 = 0
  } else {
    line1 = 1
  }
}

// Khối "Button 2" - do người dùng tạo
function Button_2() {
  if (input.pinIsPressed(TouchPin.P2)) {
    line2 = 0
  } else {
    line2 = 1
  }
}

// Khối "play music notes" - do người dùng tạo
function play_music_notes() {
  if (line2 && (line1 && !(line0))) {
    music.ringTone(262)
  } else if (line2 && (!(line1) && line0)) {
    music.ringTone(294)
  } else if (line2 && (!(line1) && !(line0))) {
    music.ringTone(330)
  } else if (!(line2) && (line1 && line0)) {
    music.ringTone(349)
  } else if (!(line2) && (line1 && !(line0))) {
    music.ringTone(392)
  } else if (!(line2) && (!(line1) && line0)) {
    music.ringTone(440)
  } else if (!(line2) && (!(line1) && !(line0))) {
    music.ringTone(494)
  } else {
    music.stopAllSounds()
  }
}

// Khai báo các biến
let line2 = 0
let line1 = 0
let line0 = 0

// Khối "on start" - thực hiện 1 lần khi khởi động
music.setVolume(255)
basic.showIcon(IconNames.EighthNote)

// Khối "forever" - vòng lặp chính của chương trình
basic.forever(function () {
  Button_0()
  Button_1()
  Button_2()
  play_music_notes()
})
```

## Giải thích code

<u>Chương trình hoạt động</u>:

Trong khối **[on start]**.

- Đầu tiên bo mạch sẽ bật âm lượng còi lên mức cao nhất qua khối **[set volume "255"]**.
- Và cho hiển thị kí hiệu 🎼.
- Phần khởi động này để chúng ta biết chương trình đã sẵn sàng.

Trong khối **[forever]**.

- Thực hiện lệnh gọi tuần tự các khối do người dùng tạo.
  - Đầu tiên là khối "Button_0", đến "Button_1", "Button_2".
  - Cuối cùng là khối "play_music_notes" và cứ thế lặp lại.

<u>Vai trò của nhóm các khối [function "Button_..."]</u>:

Trong khối "Button_0".

- Đọc giá trị Digital từ chân P0.
- Nếu phát hiện chân đang được nhấn, hay chạm → biến "line0" được đặt thành 0.
- Ngược lại, biến "line0" đặt thành 1.
- Chức năng này cũng tương tự với các khối "Button_1" cho chân P1 và "Button_2" cho chân P2.

| Chân | Biến  | Đang nhấn | Không nhấn |
|------|-------|-----------|------------|
| P0   | line0 | 0         | 1          |
| P1   | line1 | 0         | 1          |
| P2   | line2 | 0         | 1          |

<u>Vai trò của khối [function "play_music_notes"]</u>:

- Dựa theo giá trị hiện tại của các biến "line0", "line1", "line2" chương trình sẽ ra quyết định.
  - Phát ra note nhạc nào bằng khối **[ring tone (Hz)...]**.
  - Hoặc dừng phát nhạc bằng khối **[stop all sounds]**.

| line0 | line1 | line2 | Còi           |
|-------|-------|-------|---------------|
| nhấn  | .     | .     | Đồ - **[C]**  |
| .     | nhấn  | .     | Rê - **[D]**  |
| .     | .     | nhấn  | Mi - **[E]**  |
| nhấn  | nhấn  | .     | Fa - **[F]**  |
| .     | nhấn  | nhấn  | Sol - **[G]** |
| nhấn  | .     | nhấn  | La - **[A]**  |
| nhấn  | nhấn  | nhấn  | Si - **[B]**  |
| .     | .     | .     | Dừng phát nhạc|

## Kết quả

Ngắt kết nối cáp MicroUSB với máy tính và cấp nguồn cho Micro:bit bằng hộp pin AAA (bắt buộc), sau đó sử dụng 3 dây nối kẹp cá sấu để kẹp vào lá cây (hoặc các vật thể có nước, kim loại như trái cây, thìa,...) kết nối vào 3 chân: 0, 1 và 2 của Micro:bit, dùng một dây kẹp cá sấu còn lại kết nối với chân GND và cầm vào dây này, sau đó chạm vào lá cây để thấy âm thanh phát ra theo chương trình:

![](/ex/less08/image/03_1050px-Microbit_touch_sensing_Example.png)  
Micro:bit Touch Sensing Example

## Tài liệu tham khảo

- [Các khối Basic.](https://makecode.microbit.org/reference/basic)
- [Các khối Input.](https://makecode.microbit.org/reference/input)
- [Các khối Music.](https://makecode.microbit.org/reference/music)
- [Các khối Pins.](https://makecode.microbit.org/reference/pins)

## Bài viết liên quan

- [Bộ Micro:bit V2 Go with Clips](/README.md)
- [Bài 7: Máy đo thông số môi trường](/ex/less07/README.md)
