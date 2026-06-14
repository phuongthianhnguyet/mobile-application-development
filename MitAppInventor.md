# BÀI TẬP MÔN : PHÁT TRIỂN ỨNG DỤNG TRÊN THIẾT BỊ DI ĐỘNG
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
- Tạo Label Mssv
- Tạo Label tên Lớp học
  
<img width="960" height="446" alt="image" src="https://github.com/user-attachments/assets/f6c321c5-cf93-4a12-adc2-ec7d396ff4dc" />

#### Thêm Button sang screen2 ( giải toán ) và screen3 ( Viewer 1 trang web có sẵn )
- Kéo Button vào màn hình -> Đặt tên -> chọn phông chữ
  
<img width="960" height="445" alt="image" src="https://github.com/user-attachments/assets/a4464b0b-dc15-4c60-b33b-69a418c1cfec" />

### 4. Tạo các màn hình đích Screen2, screen3
- Click vào dấu + để thêm màn hình mới -> Đặt tên cho screen -> OK
-> Kết quả là sẽ có 3 màn hình.

<img width="960" height="447" alt="image" src="https://github.com/user-attachments/assets/47e43cc0-618f-435b-9a10-873790150366" />


#### Thiết kế và cấu hình Screen2 - Giải toán

Screen2 được sử dụng để xây dựng chức năng giải bài toán đơn giản trtên thiết bị di động. Trong bài này, bài toán được chọn là tính chỉ số BMI dựa vào cân nặng và chiều cao người dùng
- Tương tự thực hiện các bước cơ bản như ở Screen1

<img width="960" height="449" alt="image" src="https://github.com/user-attachments/assets/8f6ee4e4-8663-46ab-ac16-ef74f9b75054" />

- Kéo HozizontalArrangement vào trong VA_BMI, HozizontalArrangemen là khung chứa (container) dùng để sắp xếp các thành phần giao diện theo chiều ngang từ trái qua phải.
- Label: Cân nặng (Kg)
- Label: Chiều cao (Cm)
- TextBox tích chọn NumbersOnly: Chỉ cho phép nhập số
  
<img width="957" height="451" alt="image" src="https://github.com/user-attachments/assets/ac8ac8ef-d247-43f7-aa2a-ced8dcae8e1b" />

- Nút tính toán:
   
<img width="957" height="451" alt="image" src="https://github.com/user-attachments/assets/cd3693fe-883a-40e7-9fa9-b81b082ea014" />

- label: Hiển thị kết quả tính BMI
- Label: phân loại

<img width="960" height="444" alt="image" src="https://github.com/user-attachments/assets/0c6d1f2f-dea3-42dc-b8b7-1209de748c3f" />

#### Lập trình logic cho Screen 2 (Tính BMI)

Tại màn hình Screen2 chọn Block

##### Bước 1. Sự kiện Click
- Chọn btnCaculate trong Screen2 -> Kéo when btnCaculate ra màn hình

<img width="960" height="445" alt="image" src="https://github.com/user-attachments/assets/3084255e-e2b2-4bdd-b435-38cb6df35614" />

##### Bước 2. Hiển thị kết quả

- Kết quả tính xong sẽ là label tên IblResult
- Chọn IblResult -> kéo khối màu xanh đậm có chữ set IblResult.Text to ra màn hình và lắp bên trong khối when btnCaculate.click do

<img width="960" height="480" alt="image" src="https://github.com/user-attachments/assets/9b4ec983-1d87-44b1-a7cf-2aa598234336" />

##### Bước 3. Lắp ráp công thức toán học và logic:

Công thức tính BMI là: Cân nặng / (Chiều cao x Chiều cao).

- Kéo lên trên cùng cột bên trái, bấm vào nhóm Math (màu xanh dương).

- Tìm khối có dấu chia /, kéo nó gắn vào cái đuôi còn trống của khối set IblResult.Text to.

<img width="960" height="449" alt="image" src="https://github.com/user-attachments/assets/a8fda6a6-f0a5-41b6-bf6d-519de3742e86" />

- Click vào chữ TextWeight ở cột bên trái -> Chọn khối TextBox1.Text -> Kéo ra và gắn vào ô trống bên trái dấu / của phép chia.

<img width="960" height="443" alt="image" src="https://github.com/user-attachments/assets/033e01dc-841d-4022-acba-c46d5c2d06b3" />

- Vào lại nhóm Math lấy khối nhân x và gắn vào ô trống thứ hai bên phải dấu chia / để tạo phép nhân mẫu số

<img width="959" height="433" alt="image" src="https://github.com/user-attachments/assets/d3562d09-4789-433e-afa2-f86793937b1c" />

- Chiều cao x Chiều cao:
Nhấn vào chữ TextBox2 ở cột bên trái, tìm khối TextBox2.Text -> Kéo vào ô trống đầu tiên của khối x. Tiếp tục lấy thêm một khối TextBox2.Text nữa gắn vào ô trống thứ hai của khối nhấn x.

<img width="960" height="441" alt="image" src="https://github.com/user-attachments/assets/6000c52a-7adc-4a4a-9e40-590aac37ed99" />

##### Tạo biến toàn cục để lưu giá trị BMI

- Tìm nhóm Variables, kéo khối initialize global name to (màu cam) ra màn hình -> Nhấn vào chữ name và đổi tên thành BMI_Value. Vào nhóm Math kéo hối số 0 ghép vào đuôi khối màu cam này. Ý nghĩa của phần này là khởi tạo một biến tên là BMI_Value với giá trị ban đầu bằng 0.

<img width="958" height="441" alt="image" src="https://github.com/user-attachments/assets/4a88ffbb-d13d-459b-9952-a030e111e740" />

- Vào nhóm Variables, kéo khối set to ra màn hình sau đó click vào mũi tên xuống giữa set và to chọn global BMI_Value

<img width="959" height="440" alt="image" src="https://github.com/user-attachments/assets/5bd22ea5-71ca-4dd1-a1ab-c29c63a81afa" />

##### Gán công thức toán học vào biến.
Vào nhóm Variables, kéo khối set global BMI_Value to thả vào ngay dòng đầu tiên bên trong lòng khối màu nâu Click.

Kéo cả cụm phép tính toán học (phép chia và phép nhân chiều cao, cân nặng) đang gắn ở chữ set IblResult.Text to-> Chuyển nó sang gắn vào đuôi của khối set global BMI_Value to.

Tiếp theo, dòng set IblResult.Text to lúc này đang bị trống phần đuôi. Vào Variables, lấy khối get global BMI_Value gắn vào chỗ trống đó. (Ý nghĩa: Khi bấm nút -> Tính toán công thức và cất vào biến BMI_Value -> Sau đó lấy biến BMI_Value in ra màn hình ở dòng IblResult).

<img width="959" height="482" alt="image" src="https://github.com/user-attachments/assets/40ad4f8d-08fc-4fc9-af36-b542e99d263f" />

##### Lập trình Logic Phân loại (If - Else)
Theo tiêu chuẩn của WHO: Dưới 18.5 là Gầy; Dưới 25 là Bình thường; Dưới 30 là Thừa cân; Còn lại là Béo phì.

- Vào nhóm Control (màu cam nhạt), kéo khối if then thả vào ngay dưới khối set IbIResult.Text to

- Mở rộng if-Else: Bấm vào hình bánh răng màu xanh dương nhỏ xíu trên khối if đó. Một hộp nhỏ hiện ra.

- Kéo 2 cái khối else if và 1 khối else ở bên trái, thả vào lồng bên dưới chữ if ở bên phải. Xong thì bấm lại hình bánh răng để đóng hộp. Lúc này khối lệnh đã có 4 nhánh.

<img width="960" height="434" alt="image" src="https://github.com/user-attachments/assets/61ce721f-0db7-4a3b-8fd5-1fa551e581d1" />

<img width="960" height="472" alt="image" src="https://github.com/user-attachments/assets/ff9eefd9-ed65-4e3c-b49b-0d9f246963ab" />

##### Thiết kế và lập trình Screen3 (WebView - Xem Website)

- Tại giao diện thiết kế Screen3. Tại cột Palette bên trái màn hình chọn mục User Interface
- Giữ chuột WebViewer kéo vào màn hình điện thoại.

<img width="959" height="448" alt="image" src="https://github.com/user-attachments/assets/093c27fa-0ae9-43de-95ae-5804118143d9" />

- Tại cột bên phải, tìm HomeURL, copy và dán 1 địa chỉ trang web bất kì có hỗ trợ giao điệni động vào đây. Tìm dòng IgnoreSslErrors (Bỏ qua lỗi bảo mật SSL): đánh dấu ô vuông này. Cực kì quan trọng đảm bảo điện thoại có thể load được trang web mượt mà không bị hệ thống chặn lại

<img width="956" height="476" alt="image" src="https://github.com/user-attachments/assets/6f8a0c31-f4c9-4f03-86d0-9140dbc30eab" />

### 5. Chạy thử ứng dụng
#### Kết nối điện thoại với máy tính ( Dùng MIT AI2 Companion )
- Trên điện thoại tải ứng dụng tên MIT AI2 Companion. Kết nối điện thoại và máy tính cùng 1 wifi
- Trên máy tính vào connect -> chọn AI Companion -> Hiển thị mã QR Code. Mở ứng dụng MIT AI2 trên điện thoại -> Scan QR Code để quét mã QR trên máy tính.

<img width="960" height="451" alt="image" src="https://github.com/user-attachments/assets/bfb830ee-5993-43db-8b22-9c3ad7ef737c" />

<img width="1920" height="2560" alt="image" src="https://github.com/user-attachments/assets/bba1ebbd-3163-4c1a-aac3-4e7f4303a33b" />

## III. CƠ CHẾ HOẠT ĐỘNG VÀ LẬP TRÌNH KHỐI (BLOCKS PANEL)

### 1. Bản chất của việc lập trình kéo thả
Sau khi hoàn thiện giao diện, tab **Blocks** là nơi xây dựng logic xử lý ("bộ não") cho ứng dụng.
* **Bản chất thao tác:** Đây là phương thức **Lập trình trực quan (Visual Programming)**. Thay vì gõ code bằng văn bản (Text-based), người dùng chọn các khối hình học đại diện cho biến, hàm, câu lệnh điều kiện... rồi lắp ghép lại với nhau.
* **Cơ chế kiểm soát:** Các khối được thiết kế các "khớp ngậm" logic dựa trên kiểu dữ liệu. Nếu sai logic hoặc sai kiểu dữ liệu, các khối sẽ từ chối liên kết, giúp ngăn chặn lỗi hệ thống ngay từ đầu.

### 2. So sánh Lập trình khối và Viết code truyền thống

| Tiêu chí | Lập trình kéo thả (Blocks) | Lập trình truyền thống (Code văn bản) |
| :--- | :--- | :--- |
| **Ưu điểm** | • **Không lo lỗi cú pháp:** Loại bỏ hoàn toàn lỗi thiếu dấu `;`, sai dấu `{}` hoặc gõ sai chính tả từ khóa.<br>• **Trực quan, dễ nhớ:** Phân loại chức năng bằng màu sắc (Toán học màu xanh, Văn bản màu hồng, Điều khiển màu cam) giúp dễ theo dõi.<br>• **Tập trung vào logic:** Người làm chỉ cần tập trung thiết kế thuật toán (ví dụ: công thức BMI và rẽ nhánh If-Else) thay vì học thuộc lòng ngôn ngữ. | • Quản lý dự án lớn rất tốt.<br>• Tốc độ gõ phím cực nhanh khi đã thành thạo.<br>• Can thiệp sâu vào phần cứng và tối ưu tài nguyên RAM/CPU tốt hơn. |
| **Nhược điểm** | • **Rối mắt khi app lớn:** Hàng ngàn khối lệnh đan xen sẽ gây khó tìm kiếm và gỡ lỗi (Debug).<br>• **Tốc độ thao tác chậm:** Việc di chuột, tìm và kéo thả tốn thời gian hơn gõ phím.<br>• **Giới hạn tính năng:** Bị bó hẹp trong các tính năng mà nền tảng hỗ trợ sẵn. | • Rất dễ sai cú pháp đối với người mới.<br>• Dốc đường cong học tập cao (khó tiếp cận). |

### 3. Cơ chế Sao chép - Dán bằng chiếc Balo (Backpack)
* **Khái niệm:** Biểu tượng **Backpack** (ở góc trên bên phải vùng Blocks) đóng vai trò như một bộ nhớ tạm (Clipboard) dùng chung cho toàn bộ dự án.
* **Cách vận hành:** 1. **Sao chép (Copy):** Kéo cụm block cần tái sử dụng (ví dụ: cụm lệnh click chuyển đổi màn hình) thả vào Balo.
    2. **Dán (Paste):** Chuyển sang màn hình khác (`Screen2`, `Screen3`), bấm mở Balo và kéo cụm block đó ra ngoài không gian làm việc.
* **Ý nghĩa:** Đây là giải pháp tối ưu giúp lập trình viên tái sử dụng mã nguồn nhanh chóng, tránh việc phải kéo thả lại các đoạn logic giống nhau giữa các màn hình, tăng tốc độ phát triển phần mềm.



