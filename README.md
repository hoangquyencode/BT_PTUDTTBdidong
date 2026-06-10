# BT_PTUDTTBdidong
## 1. Viết phần mềm trên công cụ Mit App inventor








<img width="1823" height="924" alt="image" src="https://github.com/user-attachments/assets/ed33bab5-21a7-4ca4-a1c7-c4696f55c24e" />








<img width="1790" height="915" alt="image" src="https://github.com/user-attachments/assets/5799fef7-0be6-444b-9e31-323086a2c1ca" />





# about về bản thân+nút gọi sang 2 screen còn lại
## Thanh công cụ (Palette) có gì?
Thanh công cụ nằm ở phía ngoài cùng bên trái, chứa toàn bộ các linh kiện (Components) được chia theo các nhóm chức năng rõ rệt:

User Interface (Giao diện): Nút bấm (Button), Ô nhập văn bản (TextBox), Nhãn hiển thị (Label), Ô hiển thị web (WebViewer), v.v.

Layout (Sắp xếp): Giúp căn chỉnh linh kiện theo hàng ngang (HorizontalArrangement), hàng dọc (VerticalArrangement).

Media (Truyền thông): Máy ảnh, trình phát nhạc, ghi âm.

Maps, Sensors (Cảm biến): Định vị GPS, cảm biến lắc điện thoại, la bàn.


## Screen1
### 1. Thành phần giao diện

- **Label1**: Hiển thị dòng chữ chào mừng chạy ngang "Xin chào! Đây là app BTL".
- **Image1**: Hiển thị ảnh chân dung của tác giả.
- **Label2**: Hiển thị họ tên và lớp: Hoang_Thi_Quyen - K58KTP.
- **Label3**: Giới thiệu ngắn gọn về sinh viên Đại học Kỹ thuật Công nghiệp Thái Nguyên (TNUT).

#### Các nút chức năng

- **Button1 - Giải toán**: Chuyển sang màn hình giải bài toán định lý Pytago (Screen2).
- **Button2 - Web of Me**: Chuyển sang màn hình giới thiệu bản thân bằng WebView (Screen3).









<img width="1415" height="889" alt="image" src="https://github.com/user-attachments/assets/218b2a73-bb73-4db7-92b6-946ca5a70be2" />








<img width="1353" height="445" alt="image" src="https://github.com/user-attachments/assets/0daa1173-ecb7-4e0e-8312-eaefa22c40a3" />









## Screen2
### 2. Màn hình giải toán Pytago

- **Image**: Hiển thị ảnh nhà toán học Pytago và công thức \(c^2 = a^2 + b^2\).
- **TextBox1, TextBox2**: Nhập độ dài hai cạnh góc vuông \(a\) và \(b\).
- **Button1 - Giải**: Thực hiện tính toán theo định lý Pytago.
- **TextBox5, TextBox6, TextBox7**: Hiển thị kết quả gồm:
  - Độ dài cạnh huyền \(c\).
  - Chu vi tam giác vuông.
  - Thông báo giải thích hoặc kiểm tra định lý đảo.
- **Button3 - Quay lại**: Trở về màn hình chính (Screen1).









<img width="484" height="778" alt="image" src="https://github.com/user-attachments/assets/444c83ce-ff58-4a30-808e-eb2f346537e2" />









<img width="1299" height="534" alt="image" src="https://github.com/user-attachments/assets/8947b124-3e23-491d-b7cd-9f45956c12c0" />







## Screen3
### 3. Màn hình Web of Me

- Sử dụng **WebViewer** để hiển thị bài viết về Định lý Pytago.
- Nút **Quay lại** dùng để trở về màn hình chính.








<img width="720" height="831" alt="image" src="https://github.com/user-attachments/assets/8d25ed49-0dfa-4c95-9095-f688660e8dbb" />







<img width="579" height="170" alt="image" src="https://github.com/user-attachments/assets/9e4f273a-d217-4951-b2ad-6ced3e559f9a" />




## Kết quả









<img width="746" height="416" alt="image" src="https://github.com/user-attachments/assets/f7b20dd7-da5d-46cc-8e1e-c0b05bc59f0f" />









## 2. Viết app sử dụng Android Studio

Mở Android Studio: Chọn New Project -> Empty Views Activity -> Nhấn Next.












<img width="1135" height="813" alt="image" src="https://github.com/user-attachments/assets/68e9a101-73c2-45c8-bfcb-ce4fbcfbf97a" />









<img width="1124" height="811" alt="image" src="https://github.com/user-attachments/assets/a1b79ac5-0388-4d49-bea2-a3d27f078744" />


