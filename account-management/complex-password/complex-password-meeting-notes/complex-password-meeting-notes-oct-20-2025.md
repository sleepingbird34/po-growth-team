# [ProductGrowth] Review và Grooming giải pháp để giải quyết vấn đề của user đang sử dụng Complex Password



- Date: Oct 25, 2025
- Time: 16:00–17:00
- Location/Call: <Link or Room>
- Meeting type: Retro & Grooming

## Attendees
- ACS:
  - hoangson.pham
  - nguyen.nguyen26
  - han.nguyen2
- SCA:
  - toan.le
  - dat.le1
  - mien.pham
  - thien.nguyen4
- Growth:
  - hien.cao
  - khanh.ho
  - nhat.nguyen12

## Objectives
- Review lại các vấn đề hiện có của người dùng đang đăng nhập bằng Password
- Grooming các giải pháp giải quyết vấn đề của người dùng

## Problems
- Từ ngữ: PIN, Password

### Flow cấp lại Password cho user thông qua CS - chưa có
- Lấy lại mật khẩu thông qua CS
- Nhập sai mật khẩu nhiều lần -> Chờ 60 phút 
- Nhập sai mật khẩu tiếp tục 

Người dùng Password bị khóa tài khoản do nhập sai mật khẩu nhiều lần. Gọi lên CS để mở khóa tài khoản. CS mở khóa tài khoản và trả về PIN. Người dùng nhập PIN vào text field Password và bị kẹt ở đó

### Người dùng có Password và đăng nhập bằng Password nhưng vẫn muốn đăng nhập bằng PIN
Người dùng có Password và đăng nhập bằng Password nhưng vẫn muốn đăng nhập bằng PIN

### Chưa thấy bắn email về khi nhập mật khẩu sai 

### nội dung khi bắn email


## Giải pháp đề xuất
### Các vấn đề có thể gặp khi rollout xác thực Password ở quy mô lớn

- Trải nghiệm người dùng
  - Nhầm lẫn giữa PIN và Password; nhập PIN vào trường Password (và ngược lại)
  - Chính sách độ phức tạp gây mệt mỏi; tăng bỏ cuộc ở đăng ký/chuyển đổi; tỷ lệ quên mật khẩu cao
  - Autofill/Password Manager không tương thích; bàn phím/IME, ký tự có dấu, khoảng trắng, Unicode/emoji
  - Thông điệp lỗi, hiển thị toggle show/hide không rõ ràng; accessibility (screen reader)

- Bảo mật và rủi ro gian lận
  - Gia tăng bề mặt tấn công: brute force, credential stuffing, phishing
  - Cần rate limit/lockout/CAPTCHA/risk scoring; nhưng lockout có thể gây bùng nổ yêu cầu hỗ trợ
  - Lưu trữ mật khẩu: hash chậm (argon2/bcrypt/scrypt), salt/pepper, rotation; cấm ghi cleartext vào log/analytics
  - Kiểm tra reuse/leak (Have I Been Pwned), chính sách đổi mật khẩu sau sự cố

- Dòng chảy sản phẩm và đồng tồn tại với PIN
  - Onboarding người dùng PIN sang Password: chọn vào/ra, ép buộc theo thời gian, nhắc nhiều lần gây khó chịu
  - Đồng bộ trạng thái khóa/mở giữa PIN và Password; tránh vòng lặp “mở khóa → gửi PIN → người dùng nhập vào Password”
  - Khôi phục tài khoản: reset qua email/SMS/OOB dễ bị lạm dụng nếu KYC yếu; thiếu kênh recovery cho người dùng không có email/phone
  - Quản lý phiên: remember-me, refresh token, logout-all, rủi ro chiếm dụng phiên

- Hạ tầng và hiệu năng
  - Hash mật khẩu tốn CPU → độ trễ đăng nhập tăng, cần scale/queue/burst handling
  - Thay đổi schema DB, migration đồng bộ, idempotent; đồng thời ghi/đọc nhiều phương thức đăng nhập
  - Tương thích SSO/OAuth/legacy API; khác biệt nền tảng (web/app) và môi trường (prod/staging)
  - Giám sát/alerting thiếu → khó phát hiện sớm tỷ lệ lỗi, gian lận, timeouts

- Thiết bị và nền tảng
  - Web vs native: iOS Keychain/Android Credential Manager, autofill hành xử khác nhau
  - Mạng yếu/ngoại tuyến: timeout, retry, UX phục hồi không tốt
  - Người dùng dùng chung thiết bị, đa tài khoản, kiosk

- Vận hành và tuân thủ
  - Tải CS tăng (quên mật khẩu, khóa tài khoản); thiếu công cụ mở khóa/audit/playbook
  - Yêu cầu pháp lý (GDPR/PDPA): consent, retention, xóa dữ liệu, cập nhật ToS/Privacy Notice
  - Cần feature flag, canary, kế hoạch rollback an toàn cho data/migration

- Rủi ro tung ra diện rộng
  - Đột biến lưu lượng vào luồng “Quên mật khẩu” và hỗ trợ
  - False positive từ anti-abuse (VPN/CGNAT) chặn người dùng hợp lệ
  - Thông báo thay đổi kém → người dùng bối rối, tăng khiếu nại và churn


