# Android Studio
## 1. Lý thuyết

# 1. Giới thiệu

Ngày nay, điện thoại thông minh đã trở thành thiết bị không thể thiếu trong học tập, làm việc và giải trí. Trong đó, Android là hệ điều hành di động phổ biến nhất hiện nay. Android cho phép lập trình viên xây dựng các ứng dụng chạy trên điện thoại, máy tính bảng và nhiều thiết bị thông minh khác.

Để phát triển ứng dụng Android, công cụ được sử dụng phổ biến là Android Studio với ngôn ngữ lập trình Java hoặc Kotlin. Báo cáo này trình bày các kiến thức cơ bản về AndroidManifest.xml, vòng đời ứng dụng Android, thiết kế giao diện XML, Resource, Layout và xử lý sự kiện.

# 2. AndroidManifest.xml

## 2.1 AndroidManifest.xml là gì?

AndroidManifest.xml là tệp cấu hình quan trọng nhất của một ứng dụng Android. Tệp này dùng để mô tả các thông tin cơ bản của ứng dụng cho hệ điều hành Android biết.

AndroidManifest.xml thường được sử dụng để:

* Khai báo tên ứng dụng.
* Khai báo Activity.
* Khai báo quyền truy cập.
* Cấu hình icon và theme.
* Xác định màn hình khởi động của ứng dụng.

### Ví dụ

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android">

    <application
        android:label="MyApplication">

        <activity android:name=".MainActivity">

            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>

                <category
                    android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>

        </activity>

    </application>

</manifest>
```

## 2.2 Khai báo quyền trong AndroidManifest

Một số chức năng của ứng dụng yêu cầu được cấp quyền như:

* Camera
* Microphone
* GPS
* Bộ nhớ
* Danh bạ

Ví dụ khai báo quyền Camera:

```xml
<uses-permission android:name="android.permission.CAMERA"/>
```

Ý nghĩa:

* Thông báo với Android rằng ứng dụng muốn sử dụng Camera.
* Nếu không khai báo, ứng dụng sẽ không được phép truy cập Camera.

## 2.3 App cần quyền để làm gì?

Android yêu cầu cấp quyền nhằm:

* Bảo vệ dữ liệu người dùng.
* Đảm bảo quyền riêng tư.
* Tránh ứng dụng truy cập trái phép.

Ví dụ:

* Ứng dụng gọi xe cần quyền GPS.
* Ứng dụng chụp ảnh cần quyền Camera.
* Ứng dụng ghi âm cần quyền Microphone.

# 3. Vòng đời của ứng dụng Android

Trong Android, mỗi màn hình thường được gọi là một Activity. Android quản lý Activity theo một chu trình gọi là Activity Lifecycle.

Vòng đời giúp:

* Quản lý bộ nhớ.
* Tạm dừng ứng dụng.
* Khôi phục trạng thái.
* Đóng ứng dụng khi cần.

## 3.1 Các hàm chính trong vòng đời Activity

### onCreate()

Được gọi khi Activity được tạo lần đầu.

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    setContentView(R.layout.activity_main);
}
```

Chức năng:

* Gắn giao diện XML.
* Khởi tạo dữ liệu.
* Ánh xạ View.
* Thiết lập sự kiện.

### onStart()

Được gọi khi Activity bắt đầu hiển thị trên màn hình.

### onResume()

Được gọi khi Activity sẵn sàng cho người dùng tương tác.

### onPause()

Được gọi khi Activity bị che một phần.

Ví dụ:

* Có cuộc gọi đến.
* Mở ứng dụng khác tạm thời.

### onStop()

Được gọi khi Activity không còn hiển thị trên màn hình.

### onDestroy()

Được gọi trước khi Activity bị hủy hoàn toàn.

## 3.2 Sơ đồ vòng đời Activity

```text
onCreate()
    ↓
onStart()
    ↓
onResume()
    ↓
[Ứng dụng đang chạy]

Nếu bị che:
onPause()

Nếu bị ẩn hoàn toàn:
onStop()

Quay lại:
onRestart()
    ↓
onStart()
    ↓
onResume()

Thoát:
onDestroy()
```

## 3.3 Tại sao Android Studio tạo sẵn hàm onCreate()?

Khi tạo project mới, Android Studio tự sinh hàm:

```java
protected void onCreate(Bundle savedInstanceState)
```

vì:

* Đây là điểm bắt đầu của Activity.
* Android tự động gọi hàm này khi Activity được tạo.
* Lập trình viên sử dụng để khởi tạo giao diện và dữ liệu.

Trong onCreate() thường:

* Gắn giao diện bằng setContentView().
* Khởi tạo biến.
* Thiết lập Button, TextView.
* Gắn sự kiện.

# 4. Kiểm tra quyền trong Java

Từ Android 6 trở lên, ngoài khai báo trong Manifest, ứng dụng còn phải kiểm tra quyền trong lúc chạy.

Ví dụ:

```java
if (checkSelfPermission(
        Manifest.permission.CAMERA)
        == PackageManager.PERMISSION_GRANTED) {

    // Đã có quyền

} else {

    requestPermissions(
            new String[]{
                    Manifest.permission.CAMERA
            },
            100
    );
}
```

## Ý nghĩa

### checkSelfPermission()

Dùng để kiểm tra người dùng đã cấp quyền hay chưa.

### requestPermissions()

Hiển thị hộp thoại yêu cầu cấp quyền.

Ví dụ:

```text
Allow app to use Camera?
```

Người dùng có thể:

* Allow
* Deny

# 5. Giao diện Android bằng XML

Giao diện Android thường nằm trong thư mục:

```text
res/layout/
```

và được mô tả bằng các tệp XML.

Ví dụ:

```xml
<TextView
    android:id="@+id/txtHello"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello"/>
```

## 5.1 UI Design và XML

Android Studio hỗ trợ hai chế độ thiết kế giao diện:

* Design View (kéo thả).
* Code XML.

Hai chế độ này được đồng bộ với nhau.

# 6. Resource và tham chiếu tài nguyên

## 6.1 Không nên hardcode dữ liệu

Không nên viết:

```xml
android:text="Xin chào"
```

vì:

* Khó đổi ngôn ngữ.
* Khó bảo trì.
* Không hỗ trợ Theme tốt.

## 6.2 Lưu dữ liệu vào Resource

Ví dụ file:

```text
res/values/strings.xml
```

Nội dung:

```xml
<resources>
    <string name="hello_text">Xin chào</string>
</resources>
```

## 6.3 Cú pháp tham chiếu

Ví dụ:

```xml
android:text="@string/hello_text"
```

Cú pháp chung:

```text
@loại_resource/tên_resource
```

Ví dụ:

```text
@string/app_name
@color/red
@drawable/logo
```

## 6.4 Ưu điểm của Resource

### Hỗ trợ đa ngôn ngữ

Ví dụ:

```xml
<!-- values/strings.xml -->
<string name="hello_text">Hello</string>

<!-- values-vi/strings.xml -->
<string name="hello_text">Xin chào</string>
```

Android sẽ tự động chọn theo ngôn ngữ của thiết bị.

### Hỗ trợ Theme và Dark Mode

Android có thể tự động sử dụng:

* Màu sáng.
* Màu tối.
* Icon phù hợp.

### Dễ bảo trì

Chỉ cần sửa tại một nơi, toàn bộ ứng dụng sẽ được cập nhật.

## 6.5 Android hỗ trợ Resource theo

* Ngôn ngữ.
* Quốc gia.
* Theme sáng/tối.
* Kích thước màn hình.

Ví dụ:

```text
values/
values-vi/
values-en/
values-night/
```

## 6.6 Lợi ích

Việc hỗ trợ Resource giúp ứng dụng:

* Đa ngôn ngữ.
* Hỗ trợ Dark Mode.
* Phù hợp nhiều quốc gia.
* Chạy tốt trên nhiều thiết bị.
* Tăng trải nghiệm người dùng.

# 7. Layout và bố cục giao diện

Layout là thành phần dùng để chứa và sắp xếp các View trên màn hình.

## 7.1 LinearLayout

Dùng để sắp xếp View theo chiều dọc hoặc chiều ngang.

Ví dụ:

```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

</LinearLayout>
```

## 7.2 Orientation

### Chiều dọc

```xml
android:orientation="vertical"
```

Các View được sắp xếp từ trên xuống dưới.

### Chiều ngang

```xml
android:orientation="horizontal"
```

Các View được sắp xếp từ trái sang phải.

## 7.3 Gravity

Dùng để căn chỉnh vị trí hiển thị.

Ví dụ:

```xml
android:gravity="center"
```

Các giá trị phổ biến:

* center
* left
* right
* top
* bottom

# 8. Code tương tác với Layout

Ví dụ hiển thị nội dung lên TextView.

### XML

```xml
<TextView
    android:id="@+id/txtHello"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"/>
```

### Java

```java
TextView txt;

txt = findViewById(R.id.txtHello);

txt.setText(R.string.hello_text);
```

## Tại sao dùng R.string?

Nên sử dụng:

```java
txt.setText(R.string.hello_text);
```

Không nên:

```java
txt.setText("Xin chào");
```

Vì:

* Hỗ trợ đa ngôn ngữ.
* Dễ bảo trì.
* Tránh hardcode dữ liệu.

# 9. Event và xử lý sự kiện

Event là hành động người dùng tác động vào ứng dụng.

Ví dụ:

* Click Button.
* Click TextView.
* Nhập dữ liệu.

## 9.1 Cách 1: Sử dụng android:onClick

### XML

```xml
<Button
    android:onClick="xuLyClick"/>
```

### Java

```java
public void xuLyClick(View view) {

    Toast.makeText(
            this,
            "Đã click",
            Toast.LENGTH_SHORT
    ).show();
}
```

Khi người dùng nhấn nút, Android sẽ tự động gọi hàm `xuLyClick()`.

## 9.2 Cách 2: Sử dụng setOnClickListener()

### XML

```xml
<Button
    android:id="@+id/btnClick"/>
```

### Java

```java
Button btn;

btn = findViewById(R.id.btnClick);

btn.setOnClickListener(
    new View.OnClickListener() {

        @Override
        public void onClick(View v) {

            Toast.makeText(
                    MainActivity.this,
                    "Đã click",
                    Toast.LENGTH_SHORT
            ).show();
        }
    }
);
```

## So sánh hai cách

| Cách                 | Ưu điểm               | Nhược điểm                |
| -------------------- | --------------------- | ------------------------- |
| android:onClick      | Nhanh, ít code        | Khó quản lý khi dự án lớn |
| setOnClickListener() | Linh hoạt, dễ mở rộng | Code dài hơn              |



## 2. Viết app sử dụng Android Studio

Mở Android Studio: Chọn New Project -> Empty Views Activity -> Nhấn Next.












<img width="1135" height="813" alt="image" src="https://github.com/user-attachments/assets/68e9a101-73c2-45c8-bfcb-ce4fbcfbf97a" />









<img width="1124" height="811" alt="image" src="https://github.com/user-attachments/assets/a1b79ac5-0388-4d49-bea2-a3d27f078744" />







## Bước 1: Cấu hình quyền Internet và thư viện

Vì ứng dụng có sử dụng API và WebView nên cần cấp quyền truy cập Internet.

Mở file **AndroidManifest.xml** (trong thư mục `app > manifests`) và thêm dòng sau phía trên thẻ `<application>`:

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

Tiếp theo, mở file **build.gradle.kts (Module :app)** trong mục **Gradle Scripts**, tìm đến phần `dependencies` và thêm thư viện Volley:

```kotlin
implementation("com.android.volley:volley:1.2.1")
```

Sau khi thêm xong, nhấn **Sync Now** để Android Studio tải và cài đặt thư viện.

## Bước 2: Tạo Activity2 và Activity3

Mặc định dự án chỉ có một Activity chính. Tiến hành tạo thêm hai Activity mới để phục vụ các chức năng của ứng dụng.

Thực hiện theo các bước:

1. Chuột phải vào thư mục:

```text
app > java > com.example.btl_quyen
```

2. Chọn:

```text
New > Activity > Empty Views Activity
```

3. Tạo lần lượt hai Activity với tên:

```text
Activity2
Activity3
```

Sau khi tạo thành công, Android Studio sẽ sinh tự động các file Java và giao diện XML tương ứng cho từng Activity.





<img width="571" height="350" alt="image" src="https://github.com/user-attachments/assets/13fa6c18-8de3-4bc7-9126-776e936e0c2f" />









<img width="1920" height="890" alt="image" src="https://github.com/user-attachments/assets/bcdf1f79-f254-4ea6-92f6-80524ad74eba" />









<img width="1896" height="941" alt="image" src="https://github.com/user-attachments/assets/532d55f9-eef6-490d-b3b4-40a1488fda20" />










<img width="1916" height="966" alt="image" src="https://github.com/user-attachments/assets/57040b06-e431-43cf-ab86-366c30148396" />







Tạo 3 file .xml





<img width="574" height="264" alt="image" src="https://github.com/user-attachments/assets/ae7659fe-f1de-4f32-b708-bd74056f764a" />









<img width="1776" height="766" alt="image" src="https://github.com/user-attachments/assets/dde016f2-d556-4ed9-9a0e-04d7a82787b3" />










<img width="1898" height="978" alt="image" src="https://github.com/user-attachments/assets/e7c98563-434e-42f0-ba5f-4740edcda0f7" />










<img width="1891" height="878" alt="image" src="https://github.com/user-attachments/assets/e252500b-2b85-464a-a758-0b8c2fcb98b8" />










## Kết quả









<img width="556" height="420" alt="image" src="https://github.com/user-attachments/assets/5057f2f6-1625-4d11-9062-201a9a9b9ef0" />



