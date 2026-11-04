# Bài 10: Đánh Giá Đa Giải Pháp Xác Thực Đa Yếu Tố (2FA)
## Phần 1: Phân tích 2 Giải pháp Xác thực
1: Ba lớp yếu tố xác thực danh tính số
```Yeutoxacthuc
- Know: Mật khẩu (Password) hoặc mã PIN.
- Have: Điện thoại nhận SMS OTP hoặc thiết bị/ứng dụng sinh mã TOTP (Google/Microsoft Authenticator),
phần cứng khóa bảo mật (YubiKey).
- Are: Sinh học (Vân tay, khuôn mặt, mống mắt).
```
   Khi kích hoạt 2FA
```2FA
Mật khẩu đại diện cho yếu tố thứ nhất: Something You Know.
Mã OTP đại diện cho yếu tố thứ hai: Something You Have.
```
2. Nguyên lý hoạt động TOTP
- Ứng dụng Authenticator dùng Thời gian chuẩn (Epoch Time) kết hợp với Khóa bí mật chung (Shared Secret) để tự động sinh mã 6 số mới sau mỗi 30 giây.
- Hoạt động thuần túy trên phần cứng thiết bị, hoàn toàn không cần kết nối internet hay sóng di động nên vẫn chạy chính xác khi bật Chế độ Máy bay.
## Phần 2: Lập bảng So sánh Trade-off & Ra quyết định
3. Bảng so sánh SMS OTP và Autheticater TOTP

|Tiêu chí đánh giá|Giải pháp 1: SMS OTP|Giải pháp 2: TOTP Authenticator|
|:--|:--|:--|
|`1. Khả năng chống tấn công SIM Swapping & Nghe lén viễn thông SS7`|**Kém**: Dễ bị nghe lén hoặc chiếm đoạt số điện thoại|**Tuyệt đối**: Khóa bí mật lưu an toàn trong thiết bị|
|`2. Sẵn sàng khi Offline / Nước ngoài`|**Kém**: Phụ thuộc sóng nhà mạng|**Tuyệt đối**: Hoạt động 100% ngoại tuyến (Offline)|
|`3. Tiện dụng & Chi phí`|Quen thuộc nhưng tốn kém phí viễn thông cho doanh nghiệp|Miễn phí 100%, thao tác mở app quét mã nhanh chóng|
|`4. Rủi ro khi mất điện thoại`|Lấy lại qua làm lại SIM, nhưng nguy cơ trộm SIM cao|Cần dùng Mã Khôi phục (Backup Codes) hoặc Cloud Sync|

4. Kết luận lựa chọn
-Lựa chọn: Giải pháp 2 (TOTP Authenticator).

Lý do: Đáp ứng tuyệt đối tính sẵn sàng khi nhân sự đi công tác quốc tế (GDC) hoặc làm việc trên chuyến bay ngắt sóng; đồng thời loại bỏ hoàn toàn rủi ro tấn công Social Engineering/SIM Swapping để bảo vệ mã nguồn và tài sản giá trị lớn của công ty.
## Phần 3: Quản lý Rủi ro & Backup Codes
5. Mục đích Backup Codes: Đăng nhập dự phòng khi mất điện thoại, hỏng thiết bị hoặc lỡ xóa ứng dụng Authenticator.

2 vị trí lưu trữ an toàn:
- In ra giấy cất vào két sắt/sổ tay vật lý.
- Lưu trong tệp mã hóa của ứng dụng Password Manager cá nhân.

1 sai lầm tai hại: Lưu ảnh chụp màn hình chứa bộ mã trực tiếp vào thư viện ảnh mặc định (Google Photos/Apple Photos) hoặc gửi qua tin nhắn mạng xã hội không mã hóa.
