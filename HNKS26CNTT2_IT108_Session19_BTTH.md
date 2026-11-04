# (Bài tập tổng hợp) Rà Soát An Toàn Thông Tin Trước Khi Bàn Giao Dự Án SmartCampus
## Phần 1: Nhận diện rủi ro và xử lý sự cố
Tình huống 1: Typosquatting & Phishing (dùng miền githuh-security.com giả mạo github.com để lừa nhập pass).
Tình huống 2: Mã độc qua crack. Tắt Windows Defender tạo lỗ hổng để trojan/stealer xâm nhập, đánh cắp dữ liệu.
Quy tắc 5 KHÔNG: Tình huống 1 áp dụng KHÔNG click link lạ; Tình huống 2 áp dụng KHÔNG dùng phần mềm crack.
4 Bước Cấp cứu: Ngắt mạng $\rightarrow$ Quét virus Safe Mode $\rightarrow$ Đổi toàn bộ mật khẩu $\rightarrow$ Cài lại hệ điều hành (Clean Install).
## Phần 2: Chuyển sang Password Manager
1. Hậu quả: Dùng chung 1 mật khẩu dẫn đến Credential Stuffing (lộ 1 nơi => mất sạch GitHub, Vercel, Email).
2. Zero-Knowledge: Dữ liệu mã hóa tại thiết bị trước khi đồng bộ; máy chủ Bitwarden hoàn toàn không giữ khóa giải mã nên an toàn tuyệt đối ngay cả khi bị hack.
3. Cấu hình Generator: Độ dài: 16–32 | Chữ hoa: Có | Chữ thường: Có | Chữ số: Có | Ký tự đặc biệt: Có.
## Phần 3: Kích hoạt 2FA cho tài khoản GitHub tổ chức
1. Nhược điểm SMS OTP: Dễ dính SIM Swapping và phụ thuộc sóng viễn thông => Nên dùng Authenticator App (TOTP) bảo mật ngoại tuyến.
2. Các bước bật: GitHub Settings => Password and authentication => Enable 2FA => Chọn Authenticator app => Quét mã QR bằng Google Authenticator => Nhập mã 6 số.
3. Mã khôi phục:
- Nên: In ra giấy cất tủ / lưu trong Password Manager.
- Không nên: Chụp ảnh lưu điện thoại / lưu file text ngoài Desktop.
## Phần 4: Bảo vệ Secrets trước khi push code
- 2 Secrets bị hardcode: API_KEY và DB_PASSWORD.
- Code đã sửa (process.env):
```
const API_KEY = process.env.API_KEY;
const DB_PASSWORD = process.env.DB_PASSWORD;
function connectDatabase() { return connect(DB_PASSWORD); }
```
- Nội dung 3 file:

.env: API_KEY=sk-proj-abc123456789 / DB_PASSWORD=SmartCampus@2026

.gitignore: Thêm .env

.env.example: API_KEY=your_api_key_here / DB_PASSWORD=your_db_password_here
- 4 Bước kiểm tra trước Push: Kiểm tra git status => Kiểm tra git diff => Test chạy thử cục bộ => Kiểm tra kỹ file .gitignore.
