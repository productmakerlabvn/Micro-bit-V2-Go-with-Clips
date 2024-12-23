# Bài 3: Phát âm thanh với còi Buzzer - Micro:bit V2 Go with Clips

## Mô tả dự án

Trong bài này các bạn sẽ học cách phát âm thanh với còi Buzzer tích hợp trên Micro:bit, kết hợp với nút nhấn và màn hình Led để điều khiển.

![](/ex/less03/image/01_Microbit_buzzer.jpg)
Microbit buzzer

## Các bước thực hiện

### Danh sách thiết bị

- 1x Bo mạch Micro:bit
- 1x Cáp MicroUSB

### Chuẩn bị trước dự án

Tham khảo: [Hướng dẫn cài đặt phần mềm, nạp chương trình, cài đặt Extension mBlock cơ bản](https://github.com/makerlabvn/MakeCode-microbit)

### Các bước thực hiện

1. Tạo một dự án mới trong phần mềm MakeCode.
1. Bạn có thể lập trình kéo thả từng mã khối theo hình dưới trong mục [Blocks] hoặc copy đoạn code dưới và paste vào mục [JavaScript] để tiến hành nhanh hơn.
1. Nạp chương trình vào Micro:bit.

#### Blocks

![](/ex/less03/image/02_1050px-Microbit_V2_Go_Bai_3.png)

#### Javascript

```js
// Khối input - thực hiện khi nhấn nút A
input.onButtonPressed(Button.A, function () {
  music.stopAllSounds()
  song += 1
  if (song > 9) {
    song = 0
  }
  basic.showNumber(song)
  play()
})

// Khối input - thực hiện khi nhấn nút B
input.onButtonPressed(Button.B, function () {
  music.stopAllSounds()
  song += -1
  if (song < 0) {
    song = 9
  }
  basic.showNumber(song)
  play()
})

// Khối "play" - do người dùng tạo
function play() {
  if (song == 0) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Dadadadum), music.PlaybackMode.InBackground)
  } else if (song == 1) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Entertainer), music.PlaybackMode.InBackground)
  } else if (song == 2) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
  } else if (song == 3) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Ode), music.PlaybackMode.InBackground)
  } else if (song == 4) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Wawawawaa), music.PlaybackMode.InBackground)
  } else if (song == 5) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Ringtone), music.PlaybackMode.InBackground)
  } else if (song == 6) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Punchline), music.PlaybackMode.InBackground)
  } else if (song == 7) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Chase), music.PlaybackMode.InBackground)
  } else if (song == 8) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Birthday), music.PlaybackMode.InBackground)
  } else if (song == 9) {
    music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Wedding), music.PlaybackMode.InBackground)
  }
}

// Khai báo các biến
let song = 0

// Khối "on start" - thực hiện 1 lần khi khởi động
music.setVolume(255)
song = 0
basic.showString("A or B")
basic.pause(100)
basic.showIcon(IconNames.EighthNote)
```

### Giải thích code
>
> Lưu ý:  
> Màu sắc của các khối lệnh sẽ tương ứng với các mục chứa khối lệnh trên phần mềm MakeCode, các bạn dựa vào màu sắc này để có thể tìm kiếm dễ dàng hơn.
>
#### Chương trình sẽ hoạt động như sau

Trong khối **[ on start ]**.

1. Đầu tiên bo mạch sẽ bật âm lượng còi lên mức cao nhất là 255 qua khối **[ set volume ]**.
1. Và đặt giá trị ban đầu của biến **"song"** là `0`, tương ứng đang chọn <u>bài hát số 0</u> qua khối **[ set to ]**.
1. Kế tiếp cho hiển thị dòng chữ *"A or B"* trên màn hình LED qua khối **[ show string ]**.
1. Chờ 100ms (0.1s) qua khối **[ pause ]**.
1. Cuối cùng hiển thị kí hiệu 🎼 qua khối **[ show icon ]**.  

Phần khởi động này để chúng ta biết chương trình đã sẵn sàng.

<u>Vai trò của khối</u> **[ function "play" ]**:

- Đây là khối chức năng do người dùng tạo. Khối này được thực hiện <u>1 lần</u> mỗi khi được gọi.
- Bao gồm các khối điều kiện **[ if else ]** dựa theo giá trị của biến **"song"** để phát bài nhạc tương ứng qua khối **[ play ]**, có tất cả **10 bản nhạc**, với số thứ tự *"từ 0 đến 9"*.
*Các khối sự kiện:*

Nhấn **nút A** để thực thi khối **[ on button A pressed ]**.

1. Đầu tiên là cho dừng phát nhạc (nếu có đang phát) qua khối **[ stop all sounds ]**.
1. Tăng giá trị của biến **"song"** lên 1 đơn vị qua khối **[ change by ]**.
1. Đặt điều khiện qua khối **[ if then ]** nếu giá trị **"song"** vượt qua số 9, đặt giá trị **"song"** về lại số 0 qua khối **[ set to ]**.
1. Cho hiển thị số hiện tại lúc này của biến **"song"** lên màn hình LED qua khối **[ show number ]**.
1. Cuối cùng, gọi khối **[ function play ]** để phát nhạc.
Nhấn nút B để thực thi khối **[ on button B pressed ]**.

1. Đầu tiên là cho dừng phát nhạc (nếu có đang phát)qua khối **[ stop all sounds ]**.
1. Giảm giá trị của biến **"song"** xuống 1 đơn vị qua khối **[ change by ]**.
1. Đặt điều khiện qua khối **[ if then ]** nếu giá trị **"song"** giảm dưới số 0, đặt giá trị **"song"** về lại số 9. qua khối **[ set to ]**.
1. Cho hiển thị số hiện tại lúc này của biến **"song"** lên màn hình LED qua khối **[ show number ]**.
1. Cuối cùng, gọi khối **[ function play ]** để phát nhạc.
Kết quả
Sau khi chương trình khởi động, còi Buzzer sẽ phát âm thanh là các bài nhạc, nhấn A hoặc B để chuyển bài nhạc, màn hình Led sẽ hiển thị số thứ tự của bài nhạc.

![](/ex/less03/image/03_1050px-Screenshot_2023-07-27_at_11.09.15.png)  
Nhấn A hoặc B để chọn bài hát, màn hình Led trên Micro:bit hiển thị số thứ tự của bài hát.  
![](/ex/less03/image/04_1050px-Screenshot_2023-07-27_at_11.08.14.png)  
Còi Buzzer trên Micro:bit sẽ phát ra âm thanh của bài hát được lựa chọn.

## Tài liệu tham khảo

- [Các khối Basic của Micro:bit.](https://makecode.microbit.org/reference/basic)
- [Các khối Input của Micro:bit.](https://makecode.microbit.org/reference/input)
- [Các khối Music của Micro:bit.](https://makecode.microbit.org/reference/music)

## Bài viết liên quan

- [Bộ Micro:bit V2 Go with Clips](/README.md)
- [Bài 2: Nhận tín hiệu từ nút nhấn](/ex/less02/README.md)
- [Bài 4: Cảm biến gia tốc xác định hướng](/ex/less04/README.md)
