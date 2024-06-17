Họ và tên: Trần Quang Đức
MSSV: K215480106140
1. Tên bài toán: quản lý hệ thống khách sạn Zoon
2. readme gồm các ý sau: thông tin cá nhân + bước 1+ bước 3 + bước 4
3. mô tả bài toán: 
Xây dựng quản lí hệ thống khách sạn nhằm hỗ trợ quản lý công việc thu chi, quản lý phòng, thiết bị, dịch vụ và thuê phòng để tránh việc thất thoát và hạn chế số lượng nhân viên. Nhân viên sẽ không còn phải mất nhiều thời gian cho công việc ghi chép sổ sách và người quản lí có thể thống kê tình hình kinh doanh mà không phải chờ đến các báo cáo từ nhân viên. Đồng thời người quản lý có thể quản lý đội ngũ nhân viên một cách dễ dàng hơn.
![Screenshot 2024-06-17 223817](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/c531fab1-5a11-43b8-8935-cf82cbccc764)
3.1 các chức năng:
- Quản lý nhân viên: cho phép thêm, sửa, xóa thông tin nhân viên
- Quản lý thiết bị: cho phép thêm, sửa, xóa thông tin thiết bị
- Quản lý loại phòng: cho phép thêm, sửa, xóa thông tin loại phòng
- Quản lý phòng: cho phép thêm, sửa thông tin phòng
- Quản lý sử dụng thiết bị phòng: cho phép thêm, sửa số lượng, xóa thiết bị trong phòng.
- Quản lý khách hàng: cho phép thêm, sửa  thông tin khách hàng
- Quản lý hóa đơn thuê phòng: cho phép thêm, sửa  thông tin thuê phòng của khách hàng.
- Quản lý hóa đơn thanh toán: cho phép thêm, sửa  thông tin thanh toán thuê phòng của khách hàng.
- Thống kê doanh thu theo tháng: Cho phép thống kê doanh thu của khách sạn theo tháng.

3.2. Báo cáo: 
- Báo cáo doanh thu theo tháng
- Báo cáo tình trạng các phòng cho thuê
- Báo cáo số lượng khách thuê phòng theo tháng


3.3. Các bảng của hệ thống 
Với các mô tả chức năng và báo cáo như trên thì bài toán cần có các bảng sau:
- NHANVIEN (#MANHANVIEN, MATKHAU, HOTEN, NGAYSINH, GIOITINH, DIACHI, SODIENTHOAI, NGAYVAOLAM)
- Khóa chính: Mã nhân viên là thuộc tính phân biệt các nhân viên với nhau.
- KHACHHANG (#MAKHACH, HOTEN, GIOITINH, CMND, DIENTHOAI)
- Khóa chính: Mã khách là thuộc tính phân biệt các khách hàng với nhau.
- THIETBI (#MATHIETBI, TENTHIETBI, DVT, GIATIEN)
- Khóa chính: Mã thiết bị là thuộc tính phân biệt các thiết bị với nhau.
- LOAIPHONG (#MALOAIPHONG, LOAIPHONG, GIATIEN)
- Khóa chính: Mã loại phòng là thuộc tính phân biệt các loại phòng với nhau.
- PHONG (#MAPHONG, @MALOAIPHONG, TINHTRANG)
- Khóa chính: Mã phòng là thuộc tính phân biệt các phòng với nhau.
- Khóa ngoại: mã loại phòng cho biết phòng đó thuộc loại phòng nào.
- THIETBI_PHONG (#@MAPHONG, MATHIETBI, SOLUONG)
- Khóa chính: Mã phòng, mã thiết bị cho biết chi tiết số lượng của 1 thiết bị ở 1 phòng.
- Khóa ngoại: Mã phòng, mã thiết bị tham chiếu từ bảng Phong và ThietBi
- HDTHUEPHONG (#SHDTHUEPHONG, @MAKHACH, @MANHANVIEN, @MAPHONG, NGAYTHUE, NGAYTRA)
- Khóa chính: SHDTHUEPHONG  là thuộc tính phân biệt các hóa đơn thuê phòng
- Khóa ngoại: @MAKHACH tham chiếu từ bảng khách hàng cho biết khách hàng nào đã thuê phòng, @MANHANVIEN tham chiếu từ bảng nhân viên cho biết nhân viên nào lập hóa đơn
- HDTHANHTOAN (#SHDTHANHTOAN, @SHDTHUEPHONG, @MANHANVIEN, NGAYTHANHTOAN, TIENPHONG)
- Khóa chính: SHDTHANHTOAN là thuộc tính phân biệt các hóa đơn thanh toán
- Khóa ngoại: @SHDTHUEPHONG tham chiếu từ bảng hóa đơn thuê phòng cho biết hóa đơn thuê phòng cần thanh toán, @MANHANVIEN tham chiếu từ bảng nhân viên cho biết nhân viên nào lập hóa đơn thanh toán
![Screenshot 2024-06-17 224005](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/835511b1-137b-4302-8807-dc59865c0059)

![Screenshot 2024-06-17 224034](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/65cb2a20-8276-49d8-a220-27167030878b)
![Picture1](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/57bf09aa-7fed-4300-898e-4dfdad6c5ed8)

Trên đây là mô hình dữ liệu sau khi tạo các bảng trên sql server. 
- Một loại phòng có nhiều phòng. Một phòng thuộc 1 loại phòng duy nhất.
- Một thiết bị được sử dụng cho nhiều phòng và mỗi phòng có nhiều thiết bị.
- Một khách hàng có thể có nhiều hóa đơn thuê phòng. Một hóa đơn thuê chỉ thuộc về 1 khách hàng duy nhất.
- Một nhân viên có thể lập nhiều hóa đơn thuê.
- Một hóa đơn thuê phòng có 1 hóa đơn thanh toán phòng.
- Một nhân viên có thể lập nhiều hóa đơn thanh toán phòng.


3.4. Tạo thủ tục, trigger
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/2e3a0025-b702-42a8-980e-488e57ea625e)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/d0bf6abc-d5a2-40f1-bbf1-54be37a00ee8)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/43a4b897-979f-4b46-a78f-2d25d5412c71)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/de4b51d2-d921-4595-9c76-b0d756e60163)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/3d72cac5-4075-4c56-932d-20950ddbeee3)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/2af05dbf-ef43-4ae4-aac0-9ab4fcdd051a)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/9317ccee-7340-4776-875a-e795f644c957)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/aeed55e7-0753-4fb1-940b-075b25ba285a)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/c4bfe237-fbcb-4ca8-a9fd-40110e892f20)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/17541318-53eb-4dfb-baff-24afb4f7b52e)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/d7b32e11-8283-45a8-a63d-103e4bd89575)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/4fcd3770-ed8e-473d-8027-7148d521e44f)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/85275ce4-3245-4cf8-a717-f37e1fb52bfc)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/0211bc36-7e17-48a4-8ef9-ecce0c6e497b)







