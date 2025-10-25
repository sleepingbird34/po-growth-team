# FAQ: Đăng nhập bằng Passkey cho người dùng MoMo

<!-- https://fidoalliance.org/passkeys -->
<!-- https://www.passkeycentral.org/resources-and-tools/customer-support -->

## Passkey là gì?
Passkey là một phương thức đăng nhập an toàn và tiện lợi, thay thế cho mật khẩu. Nó cho phép bạn đăng nhập vào MoMo bằng cách sử dụng các phương thức bạn dùng để mở khóa điện thoại của mình (ví dụ: vân tay, khuôn mặt, mã PIN hoặc hình vẽ).
Khi dùng passkey, bạn không cần phải nhớ hay nhập tên đăng nhập và mật khẩu của MoMo nữa. Thay vào đó, bạn chỉ cần xác nhận đăng nhập bằng cách mở khóa thiết bị.

## Nếu đăng nhập vào MoMo bằng các phương thức mở khóa điện thoại thì các thông tin 


Passkey giúp bạn đăng nhập vào ứng dụng MoMo an toàn, nhanh chóng và đơn giản. Khác với mật khẩu, passkey chống lừa đảo, luôn mạnh và không có bí mật chung giữa trình quản lý thông tin xác thực và dịch vụ (ví dụ: MoMo).

## Dữ liệu sinh trắc học của tôi có an toàn không?
An toàn. Dữ liệu sinh trắc học và việc xử lý luôn nằm trên thiết bị của bạn, không gửi lên máy chủ. Máy chủ MoMo chỉ nhận kết quả xác minh thành công hay không.

## Vì sao passkey tốt hơn mật khẩu + yếu tố thứ hai?
Passkey là thông tin xác thực FIDO, an toàn hơn tổ hợp mật khẩu + OTP/duyệt điện thoại. Mật khẩu dễ bị lừa đảo và rò rỉ; OTP/duyệt cũng có thể bị lừa và bất tiện. Với passkey, trải nghiệm tốt hơn và an toàn hơn.

## Đồng bộ passkey sang thiết bị khác có an toàn không?
Có. Đồng bộ passkey được mã hóa đầu cuối và tài khoản đám mây có cơ chế bảo vệ mạnh. Khả năng chống phishing được đảm bảo dù khóa có gắn phần cứng hay không. Không có mật khẩu để bị đánh cắp.

## Tính sẵn sàng của passkey trên các nền tảng
Passkey tích hợp sẵn và tự đồng bộ giữa các thiết bị ngày càng phổ biến:
- iOS 16+, iPadOS 16 và macOS Ventura trở lên
- Android (từ 10/2022) và ChromeOS (từ 2023)
- Windows (đã mở rộng hỗ trợ từ 2023–2024)
Hầu hết nền tảng cho phép đăng nhập bằng passkey từ thiết bị lân cận (điện thoại hoặc khóa bảo mật): Edge/Chrome trên Windows; Safari/Edge/Chrome trên macOS; ChromeOS. Passkey sử dụng WebAuthn; việc đồng bộ do hệ điều hành quản lý.

## Passkey khả dụng trên nhiều thiết bị như thế nào?
Nhiều thiết bị hỗ trợ đồng bộ passkey qua tài khoản đám mây của bạn (mã hóa đầu cuối). Tạo passkey một lần, bạn có thể dùng trên mọi thiết bị đăng nhập cùng tài khoản. Thiết bị mới sẽ tự đồng bộ sau khi đăng nhập tài khoản đám mây.

## Đăng nhập thế nào nếu thiết bị chưa có passkey MoMo?
Bạn có thể:
- Dùng passkey từ thiết bị khác hoặc khóa bảo mật FIDO để đăng nhập
- Làm theo hướng dẫn hiển thị khi đăng nhập trên thiết bị mới
MoMo sẽ hiển thị nhắc nhở và hướng dẫn bước tiếp theo.

## Bảo mật khi đăng nhập cận kề qua Bluetooth là gì?
FIDO Cross-Device Authentication (CTAP 2.2) dùng Bluetooth LE để kiểm tra “gần kề”, nhưng bảo mật chính nằm ở lớp mật mã tiêu chuẩn bổ sung (không phụ thuộc vào bảo mật Bluetooth).

## Passkey có được xem là xác thực đa yếu tố (MFA) không?
Có. Passkey kết hợp:
- Thiết bị bạn sở hữu (something you have)
- Sinh trắc học hoặc PIN (something you are/know), khi dịch vụ yêu cầu xác minh người dùng
Nhà cung cấp nền tảng còn xét nhiều tín hiệu bổ sung khi khôi phục passkey. Một số cơ quan quản lý chưa liệt kê chính thức, và FIDO Alliance đang thúc đẩy công nhận.

## Chuyển nền tảng (Android ↔ iOS) như thế nào?
- Còn thiết bị cũ: dùng passkey để đăng nhập MoMo trên thiết bị mới, sau đó tạo passkey trên thiết bị mới
- Có khóa bảo mật: dùng để xác thực trên thiết bị mới
- Không còn thiết bị cũ/khóa: dùng quy trình khôi phục tài khoản MoMo

## Khóa bảo mật FIDO có hỗ trợ passkey không?
Có. Khóa bảo mật FIDO hỗ trợ passkey trên một thiết bị (single‑device passkey). Các nền tảng và trình duyệt phổ biến đều hỗ trợ sử dụng khóa bảo mật.

