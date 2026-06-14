# YÊU CẦU:
Viết App sử dụng Android Studio:
==> Tạo app1 sử dụng cơ chế Dữ liệu chuẩn bị trước trong Assets
==> APP2 (android studio): tạo app tương đương với Mit App inventor, app có 3 activity
# BÀI LÀM
## I. LÝ THUYẾT
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
