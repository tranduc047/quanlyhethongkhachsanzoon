- Họ và tên: Trần Quang Đức
- MSSV: K215480106140
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


3.4. Tạo thủ tục
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/8b33d782-7841-4996-9f32-0f26cbf3296c)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/92844b8b-23ca-4e5f-9153-fe46dcb17ff3)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/261cfc5c-b885-4743-bf27-ff69dd92e1ce)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/71b203b5-4168-4e8a-bf54-987710bcb726)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/95e77792-c6f4-4445-a2fe-da89b6a8e67d)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/c4715bca-1afb-4438-b6cb-7f7a8837ee76)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/492ddbaa-8b23-4697-9f13-59e4efe8354f)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/06f96ce6-2388-4ea5-bf76-80cd7d018229)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/5e94c271-bdff-4567-8141-a3200da3b348)

3.5 Function 
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/492f67aa-f5dc-4eb0-bcf1-3cd524f2d411)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/80c621ef-9f26-4d35-a9eb-81ed9f93a851)


3.6 Trigger
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/8848e080-7652-4fa6-88aa-19feb00c8cc4)
![image](https://github.com/tranduc047/quanlyhethongkhachsanzoon/assets/83036126/bf3a0fb0-8014-4a38-8da0-a46586d3c7ba)










