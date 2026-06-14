# YÊU CẦU:
Viết App sử dụng Android Studio:
==> Tạo app1 sử dụng cơ chế Dữ liệu chuẩn bị trước trong Assets
==> APP2 (android studio): tạo app tương đương với Mit App inventor, app có 3 activity
# BÀI LÀM
## I. LÝ THUYẾT
### 1. Tập tin Cấu trúc AndroidManifest.xml là gì?
Tập tin AndroidManifest.xml là một trong những thành phần quan trọng nhất của một ứng dụng Android. Hãy tưởng tượng nó giống như một "bản căn cước" hoặc "sách hướng dẫn sử dụng" mà ứng dụng gửi cho hệ điều hành Android.

Khi bạn cài đặt hoặc chạy ứng dụng, hệ điều hành Android sẽ đọc tập tin này đầu tiên để biết ứng dụng của bạn có những gì, cần những quyền gì và hoạt động ra sao.

#### Các thông tin bắt buộc phải khai báo
- Tên gói ứng dụng (package): Đây là định danh duy nhất (Unique ID) của ứng dụng trên toàn bộ hệ sinh thái Android (và trên chợ ứng dụng Google Play). Hệ điều hành dựa vào đây để phân biệt ứng dụng của bạn với các ứng dụng khác.
  
- Thành phần ứng dụng (Ít nhất một Activity chính): Một ứng dụng có thể không có Service, không có Content Provider, nhưng bắt buộc phải có ít nhất một Activity được cấu hình làm "Cổng vào" (LAUNCHER). Nếu không có màn hình này, người dùng sẽ không thể bấm vào icon để mở app của bạn lên được.

- Các thuộc tính cơ bản của Ứng dụng (<application>): Thẻ <application> là bắt buộc để bao bọc các thành phần bên trong. Trong thẻ này, bạn thường phải chỉ định icon (android:icon) và tên hiển thị của app (android:label) để hệ thống hiển thị trên màn hình điện thoại.
  
#### Ví dụ khai báo Activity khởi chạy chính (Launcher Activity):

``` 
<activity android:name=".MainActivity" android:exported="true">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```
### 2. hệ thống quyền trong Android

Hệ thống Quyền (Permission) trong Android là cơ chế bảo mật được thiết kế để bảo vệ quyền riêng tư của người dùng. Nó đảm bảo rằng một ứng dụng không thể tự ý truy cập vào dữ liệu cá nhân (tin nhắn, danh bạ, vị trí) hoặc các phần cứng nhạy cảm (camera, micro) nếu chưa được sự cho phép rõ ràng.

## 🔐 Android Permissions (Quyền ứng dụng)

Để ứng dụng có thể hoạt động chính xác với các tính năng phần cứng và dữ liệu hệ thống, các quyền (Permissions) tương ứng dưới đây cần được khai báo trong tệp `AndroidManifest.xml`.

Chi tiết các quyền được cấu hình trong dự án:

| Chức năng phần cứng / dữ liệu | Tên Permission tương ứng |
| :--- | :--- |
| Truy cập mạng Internet toàn diện | `android.permission.INTERNET` |
| Sử dụng phần cứng máy ảnh | `android.permission.CAMERA` |
| Lấy vị trí chính xác thông qua GPS | `android.permission.ACCESS_FINE_LOCATION` |
| Đọc dữ liệu từ bộ nhớ lưu trữ ngoài | `android.permission.READ_EXTERNAL_STORAGE` |
| Thực hiện cuộc gọi điện thoại trực tiếp | `android.permission.CALL_PHONE` |

*(Sơ đồ tham khảo chi tiết cấu trúc quyền xem tại tệp: `image_28bb07.png`)*

### Cách khai báo trong AndroidManifest.xml

Thêm các dòng sau vào trước thẻ `<application>` trong tệp cấu hình của bạn:

```xml
<manifest xmlns:android="[http://schemas.android.com/apk/res/android](http://schemas.android.com/apk/res/android)" ...>

    <!-- Khai báo các quyền sử dụng trong ứng dụng -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.CALL_PHONE" />

    <application ...>
        ...
    </application>
</manifest>
```
### 3. Vòng đời của Activity trong Android
Vòng đời của Activity (Activity Lifecycle) là một tập hợp các trạng thái mà một Activity đi qua, từ lúc nó bắt đầu được khởi tạo cho đến khi bị hủy hoàn toàn.

Hệ điều hành Android quản lý vòng đời này thông qua một chuỗi các hàm gọi lại (callback methods). Việc hiểu rõ vòng đời giúp bạn quản lý tốt tài nguyên (tránh rò rỉ bộ nhớ), lưu trữ trạng thái ứng dụng khi người dùng xoay màn hình, hoặc tạm dừng các tác vụ tốn pin (như định vị, camera) khi app bị ẩn đi.

#### Các hàm Callback cốt lõi và ý nghĩa
Có 6 callback quan trọng nhất tạo thành các cặp trạng thái đối lập nhau:

Giai đoạn Khởi tạo & Xuất hiện
- onCreate():

Thời điểm: Được gọi duy nhất một lần khi Activity lần đầu tiên được tạo ra.

Hành động: Nơi bạn thiết lập giao diện (gọi hàm setContentView()), khởi tạo các biến toàn cục, hoặc liên kết dữ liệu.

- onStart():

Thời điểm: Chạy ngay sau onCreate(). Lúc này màn hình ứng dụng bắt đầu xuất hiện công khai trước mắt người dùng.

Hành động: Chuẩn bị các thành phần giao diện để sẵn sàng tương tác.

- onResume():

Thời điểm: Được gọi khi Activity bước vào trạng thái "Foreground" (nằm trên cùng). Người dùng bắt đầu tương tác trực tiếp (chạm, vuốt, gõ chữ) được với ứng dụng.

Hành động: Bật lại các tính năng tốn tài nguyên như camera, bộ lắng nghe cảm biến, hoặc chạy tiếp hoạt ảnh (animation).

Giai đoạn Bị che khuất & Hủy bỏ
- onPause():

Thời điểm: Chạy khi Activity bị mất tiêu điểm (focus) nhưng vẫn hiển thị một phần. Ví dụ: Khi có một hộp thoại (dialog) nhỏ của hệ thống đè lên, hoặc khi chia đôi màn hình ứng dụng.

Hành động: Dừng tạm thời các tác vụ tốn pin hoặc các tiến trình không cần chạy lúc giao diện bị che khuất một phần.

- onStop():

Thời điểm: Được kích hoạt khi Activity hoàn toàn ẩn đi (người dùng bấm nút Home để ra màn hình chính, hoặc mở hẳn một Activity mới đè lên).

Hành động: Giải phóng các tài nguyên nặng (như ngắt kết nối GPS, dừng tải dữ liệu từ mạng) để nhường RAM cho hệ thống.

- onDestroy():

Thời điểm: Hàm cuối cùng được gọi trước khi Activity bị hủy bỏ hoàn toàn khỏi bộ nhớ (khi người dùng bấm nút Back để thoát, tắt ứng dụng ở trình đa nhiệm, hoặc do hệ thống tự giải phóng RAM).

Hành động: Dọn dẹp sạch sẽ tài nguyên, hủy bỏ các kết nối chạy ngầm đang dang dở.

🔄 Hàm bổ trợ onRestart(): Nếu một Activity đang nằm ở trạng thái onStop() (bị ẩn hoàn toàn) nhưng người dùng mở lại nó, hệ thống sẽ chạy hàm onRestart() trước khi quay lại quy trình onStart() -> onResume().
## II. TẠO APP1: SỬ DỤNG CƠ CHẾ DỮ LIỆU CHUẨN BỊ TRƯỚC TRONG ASSETS
### Bước 1. Tạo project trên Android Studio
- Mở Android Studio -> New Project -> Empty Views Activity -> Next
  
<img width="958" height="509" alt="image" src="https://github.com/user-attachments/assets/aabbc178-7b2e-444e-bc4d-201db4dd236c" />

- Sau đó điền:
```
Name: BaiTap2-App1
Package Name: com.example.baitap2_app1
Language: Java
Minimum SDK: API 24
```
Nhấn Finish

### Bước 2. Tạo thư mục Assets và file dữ liệu JSOn địa điểm
#### Tạo thư mục Assets 
Mặc định dự án mới sẽ không có thư mục này vì vậy ta phải tạo nó. Tại cột danh sách thư mục bên trái:
- Chọn App -> New -> Directory -> Assets Folder ->. Sau khi nhấn Finish dưới thư mục mainsẽ xuất hiện 1 thư mục tên là Assets

<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/7b19d686-6df3-42b3-8071-8c772757772a" />

<img width="325" height="281" alt="image" src="https://github.com/user-attachments/assets/ff9e8d9a-54e2-4cd0-b717-81ea06b9b5c6" />

#### Tạo file dữ liệu Camnang.json
- Chọn Assets vừa tạo -> New -> File
- Đặt tên file là: Camnang.json
   
<img width="960" height="512" alt="image" src="https://github.com/user-attachments/assets/69f5791f-e80a-49b7-bb7f-a143f206c659" />

<img width="253" height="284" alt="image" src="https://github.com/user-attachments/assets/3a706d11-8b0a-4ce2-871d-baf44fc7bf0c" />

#### Thêm ảnh vào app
tải ảnh trên google ssau đó đổi tên 5 món thành pho_thin.jpg; bun_cha.jpg; mi_quang.jpg; com_tam.jpg; banh_mi.jpg.
- Copy ảnh và lưu về.
- Tìm thư mục app -> res -> drawable -> dán ảnh vào

<img width="234" height="294" alt="image" src="https://github.com/user-attachments/assets/0de05387-d537-49b4-b8e8-5b8e380b2356" />

### Bước 3. Thiết kế giao diện XML (layout)

#### Màn hình chính file activity_main.xml

Mở file activity_main.xml và chuyển sang chế độ xem Code sau đó sửa lại file activity_main.xml

<img width="958" height="509" alt="image" src="https://github.com/user-attachments/assets/f13c8434-3591-4eb6-9ff1-b19f7ae00f48" />

#### Thiết kế ô hiển thị file item

Click chuột phải vào thư mục Layout -> New -> Layout Resource File. Đặt tên file là item_camnang sau đó mở file này ra và viết code thiết kế khung dạng thẻ vào.

<img width="958" height="510" alt="image" src="https://github.com/user-attachments/assets/eaefa5b7-71bc-4b94-8a27-4b2211e248be" />

<img width="960" height="509" alt="image" src="https://github.com/user-attachments/assets/716b4875-1425-4f55-a29b-227b40d88d3d" />


### Bước 4. Viết mã nguồn cấu trúc logic (java)
#### Tạo dữ liệu mẫu (CamNang.java)
- Trong thư mục kotlin+java, nhấp chuột phải vào thư mục com.example.app1_bt2 (dòng đầu) -> New -> Java Class

<img width="960" height="512" alt="image" src="https://github.com/user-attachments/assets/eb913663-86eb-4d78-b004-3c7493ff8242" />

- Đặt tên Cam_Nang -> Enter
- Xoá hết code ban đầu và cho code mới vào

<img width="960" height="506" alt="image" src="https://github.com/user-attachments/assets/72c45fbb-f85f-44ab-bdee-c8d5f6424443" />

#### Tạo bộ nạp dữ liệu lên màn hình
Tạo 1 class Java tên CamNangAdapter trong thư mục com.example.app1_bt2. File này đóng vai trò cầu nối, lấy dữ liệu từ file JSON đổ vào file giao diện item_camnang.xml

<img width="960" height="510" alt="image" src="https://github.com/user-attachments/assets/a08f4906-15a8-4eaa-b60c-e6ac64b3107e" />

#### Cập nhật mã nguồn file MainActivity.java
Mở file MainActivity.java có sẵn ra và cập nhật lại toàn bộ code để thực hiện việc: Đọc file JSON từ Assets -> Chạy thuật toán tìm kiếm tuyến tính

<img width="960" height="509" alt="image" src="https://github.com/user-attachments/assets/4cfe4359-c34d-4c8d-b342-fa5e9d5743ff" />

### Bước 5. Chạy kiểm thử.

Bấm vào nút tam giác màu xanh lá cây (Run app) hoặc nhấn tổ hợp phím Shift + F10.

Đợi một lát máy ảo sẽ khởi động lên, tự động cài đặt app và hiển thị danh sách du lịch hoạt động Offline hoàn toàn!

<img width="953" height="511" alt="image" src="https://github.com/user-attachments/assets/2ba42e3d-7e0c-4345-a882-1607f5ba23be" />

## III. TẠO APP2
### Bước 1. Tạo project mới




