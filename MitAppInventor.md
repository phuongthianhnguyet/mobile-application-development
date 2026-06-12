<img width="960" height="440" alt="image" src="https://github.com/user-attachments/assets/70f62ad4-1473-419e-8275-04675636dc25" /># BÀI TẬP MÔN : PHÁT TRIỂN ỨNG DỤNG TRÊN THIẾT BỊ DI ĐỘNG
# YÊU CẦU:
1. Viết phần mềm trên công cụ Mit App inventor
   (tập trung vào quy trình tạo ra phần mềm)
   app có 3 screen:
   + about về bản thân+nút gọi sang 2 screen còn lại
   + giải 1 bài toán đơn giản
   + sử dụng webview: hiển thị 1 trang web có sẵn, hỗ trợ giao diện điện thoại
   mô tả: thanh công cụ có gì? kéo thả + thay đổi thuộc tính: làm ntn, để làm gì?
          block: mô tả bản chất việc kéo thả block ntn?
                 ưu điểm gì so với viết code? nhược điểm?
                 copy paste block ? (backpack)
# BÀI LÀM:
## I. TỔNG QUAN VỀ CÔNG CỤ & BẢN CHẤT HỆ THỐNG

### 1. Không gian làm việc (Workspace) trên MIT App Inventor
Giao diện của MIT App Inventor được chia làm 2 phần chính:

* **Giao diện thiết kế (Designer screen):** Gồm 4 cột chức năng chính:
    * **Palette (Bảng công cụ):** Chứa các linh kiện (components) được chia theo nhóm (User Interface, Layout, Media, Webview...).
    * **Viewer (Màn hình mô phỏng):** Vùng hiển thị trực quan giao diện điện thoại, nơi thực hiện kéo thả các linh kiện vào.
    * **Components (Danh sách linh kiện):** Cây thư mục quản lý và đổi tên các linh kiện đã sử dụng trong màn hình.
    * **Properties (Thuộc tính):** Nơi thay đổi thông số của linh kiện (màu sắc, kích thước, nội dung hiển thị, căn lề...) để định dạng thẩm mỹ và cấu hình ban đầu.

* **Giao diện lập trình (Blocks screen):** Nơi lập trình logic cho ứng dụng bằng các khối lệnh.

### 2. Bản chất của việc kéo thả Block
* **Bản chất:** Thay vì gõ mã nguồn (code) dạng văn bản dễ sai cú pháp, App Inventor đóng gói các hàm, biến, câu lệnh điều kiện thành các "khối hình học" (giống Lego). Việc lập trình dựa trên tư duy kích hoạt sự kiện: *“Khi sự kiện X xảy ra (ví dụ: Click nút) -> Thực hiện hành động Y (ví dụ: Chuyển màn hình)”*.
* **Ưu điểm (so với viết code truyền thống):**
    * Trực quan, dễ tiếp cận, không bị lỗi cú pháp (Syntax error) như thiếu dấu `;` hay `{}`.
    * Tốc độ phát triển ứng dụng (Prototyping) cực kỳ nhanh.
* **Nhược điểm:**
    * Giao diện rối mắt, khó quản lý khi dự án mở rộng quy mô lớn (hàng ngàn block).
    * Bị giới hạn các tính năng chuyên sâu chưa được nền tảng đóng gói sẵn.
    * Hiệu năng không tối ưu tuyệt đối bằng code thuần (Native code như Java/Kotlin).

### 3. Tính năng Copy-Paste Block bằng Balo (Backpack)
* **Khái niệm:** Biểu tượng chiếc balo (**Backpack**) ở góc trên bên phải vùng Blocks đóng vai trò như một bộ nhớ tạm (Clipboard).
* **Cách hoạt động:** Người dùng kéo thả một cụm block logic vào Backpack để lưu trữ. Khi chuyển sang một `Screen` (màn hình) khác, chỉ cần bấm vào Backpack và kéo cụm block đó ra để tái sử dụng. Điều này giúp tiết kiệm thời gian và giảm thiểu việc làm lại các logic giống nhau giữa các màn hình.

## II. HƯỚNG DẪN THỰC HÀNH TỪNG BƯỚC.
### Bước 1. Khởi tạo dự án
- Truy cập trang chủ MIT App Inventor, chọn Create Apps và đăng nhập bằng tài khoản Google
  
<img width="960" height="509" alt="image" src="https://github.com/user-attachments/assets/9eef7d39-f92b-4dfe-84ce-9073901fb3b3" />

- Sau khi đăng nhập MIT Apps, chọn New project để tạo mới -> đặt tên mới -> OK
  
Giao diện ban đầu sẽ hiển thị chế độ Designer cho Screen1 gồm các thành phần:
- Palette chứa các thành phần giao diện như: Button, Label, TextBox, Image, WebViewer
- Viewer là khu vực thiết kế giao diện ứng dụng.
- Components là danh sách các thành phần đã được thêm vào màn hình
- Properties cho phép thay đổi thuộc tính của các thành phần như: Text, Width, Height, Front Size, Background Color.
  
<img width="960" height="482" alt="image" src="https://github.com/user-attachments/assets/71153338-f129-4bd6-bf17-1f4896ea3c8e" />

### Bước 2. Thiết kế giao diện (UI) cho Screen 1 (About Me)
#### Đặt tiêu đề (Title) cho Screen 1:

Ở cột bên phaiả kéo xuống dưới tìm thuộc tính Title và điền tên tiêu đề, tích Scrollable để cho phép màn hình cuộn xuống. AlignHorizontal điền giá trị Center để căn giữa các thành phần trên màn hình.

<img width="960" height="476" alt="image" src="https://github.com/user-attachments/assets/9a80fe6d-bd16-4e23-9654-5cb1153987a1" />

#### Tạo khung chứa giao diện bằng Vertical Arrangement:
- Kéo Vertical Arrangement vào khung hình
- Cấu hình cho Vertical Arrangement với các tham số:
  - Height: Automatic
  - Width: Fill parent
  - AlighHorizol: Center
 
<img width="960" height="451" alt="image" src="https://github.com/user-attachments/assets/4110747c-95a2-40cb-9b67-f330dd14f4cb" />
 
#### Thêm tiêu đề cho bài viết.
- Kéo Label vào trong VerticalArrangement
- Chọn fontbold
- FrontSize: kích cỡ chữ
- Text: GIỚI THIỆU BẢN THÂN
- TextAlignment:Căn giữa nội dung trong label
  
<img width="960" height="448" alt="image" src="https://github.com/user-attachments/assets/2b5bb627-36ed-461f-9d97-b08916ccc5cf" />

#### Thêm ảnh đại diện
- Tương tự: Kéo Image vào bên trong VerticalArrangement
- Picture: Upload File
- Chỉnh kích cỡ của ảnh cho phù hợp khung ảnh
  
<img width="959" height="437" alt="image" src="https://github.com/user-attachments/assets/a5347aa2-b1ab-47b7-bfcb-26a292e7fe57" />

#### Điền thông tin giới thiệu bản thân (About me)
- Tạo Label họ tên
