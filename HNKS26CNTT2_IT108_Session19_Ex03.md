# Bài 3 : Khắc phục sự cố rò rỉ thông tin đăng nhập
## Báo cáo phân tích
- Input: Mất quyền kiểm soát Facebook/Gmail, phiên đăng nhập lạ, cookie/token bị đánh cắp.
- Process (Quy trình 4 bước):
1. Ngắt kết nối: Rút mạng (Wi-Fi/LAN) ngay lập tức để chặn malware gửi dữ liệu ra ngoài.
2. Đăng xuất toàn bộ: Dùng điện thoại/thiết bị sạch đăng nhập tài khoản rồi chọn Log out of all sessions.
3. Đổi mật khẩu & Bật 2FA: Đổi pass mới toàn bộ và kích hoạt xác thực 2 bước (Authenticator App).
4. Thu hồi quyền (Revoke): Xóa các ứng dụng, token, OAuth app lạ đang liên kết ngầm.
- Output: Tài khoản được bảo mật, thiết bị cách ly sạch mã độc.
## Triển khai
B1: Đổi mật khẩu từ thiết bị khác
Vào cài đặt bảo mật (Google/Facebook) từ điện thoại => Đổi mật khẩu => Tích chọn "Đăng xuất khỏi tất cả thiết bị khác".
B2: Revoke Token trên GitHubGitHub => Settings => Developer settings => OAuth Apps / Personal access tokens => Nhấn Revoke các token lạ.
