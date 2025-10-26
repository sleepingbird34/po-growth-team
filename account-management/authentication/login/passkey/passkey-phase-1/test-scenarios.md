# Test Scenarios: Đăng Nhập Bằng Passkey

Nguồn tham chiếu: `sequence-diagram.pu` (Luồng Đăng Nhập Bằng Passkey)

## 1. Phạm vi
Bao phủ các nhánh chính:
- Phát hiện hỗ trợ Passkey trên thiết bị
- Đăng nhập bằng Passkey (Xác thực hệ điều hành thành công/thất bại/hủy)
- Kiểm tra rủi ro tài khoản (High risk vs Low risk)
- Rơi về luồng đăng nhập bằng SĐT khi cần
- Xử lý lỗi kỹ thuật (network, signature, format)
- Các trường hợp bảo mật & edge cases

## 2. Quy ước
- ID: `PK-XX`
- Priority: (H)igh / (M)edium / (L)ow
- Risk flag: đánh dấu các case quan trọng về bảo mật: `🔐`
- Expected Result viết ở mức hành vi người dùng + phản hồi hệ thống (app + backend)

---
## 3. Danh sách Test Scenario
Phiên bản này chuyển tất cả scenario sang định dạng Given / When / Then rõ ràng để thuận tiện tự động hoá.

### Nhóm A: Khả năng hiển thị & điều kiện ban đầu
| ID       | Title                                | Given                                                   | When                       | Then                                                              | Notes                   |
| -------- | ------------------------------------ | ------------------------------------------------------- | -------------------------- | ----------------------------------------------------------------- | ----------------------- |
| TC-PK-01 | Hiển thị nút Passkey khi được hỗ trợ | Thiết bị iOS ≥16 hoặc Android ≥9 và có screen lock      | User mở màn hình đăng nhập | Nút "Đăng nhập bằng Passkey" xuất hiện một lần, trạng thái enable |                         |
| TC-PK-02 | Ẩn nút khi không hỗ trợ              | Thiết bị không đạt yêu cầu OS hoặc không có screen lock | User mở màn hình đăng nhập | Không có nút Passkey                                              | Không placeholder trống |
| TC-PK-03 | Vẫn hiển thị dù tắt biometric        | Thiết bị hỗ trợ nhưng biometric disable; PIN tồn tại    | User mở màn hình đăng nhập | Nút Passkey hiển thị (OS sẽ fallback PIN)                         |                         |

### Nhóm B: Fallback SĐT
| ID    | Title                         | Given                     | When                           | Then                                       | Notes          |
| ----- | ----------------------------- | ------------------------- | ------------------------------ | ------------------------------------------ | -------------- |
| PK-10 | Luồng SĐT hoạt động song song | Thiết bị hỗ trợ passkey   | User nhập SĐT và nhấn Tiếp tục | Luồng SĐT chạy bình thường, không bị block |                |
| PK-11 | Chuyển SĐT -> Passkey         | User đang ở form nhập SĐT | User bấm Back rồi chọn Passkey | Prompt Passkey được khởi tạo               | UX consistency |

### Nhóm C: Xác thực Passkey (OS Prompt)
| ID    | Title                    | Given                           | When                            | Then                                             | Notes                                      |
| ----- | ------------------------ | ------------------------------- | ------------------------------- | ------------------------------------------------ | ------------------------------------------ |
| PK-20 | Hiển thị prompt OS       | Nút Passkey hiển thị            | User bấm nút Passkey            | OS prompt hiển thị ≤300ms                        | Loading state hiển thị trong thời gian chờ |
| PK-21 | Thành công bằng vân tay  | Thiết bị đã đăng ký fingerprint | User xác thực vân tay hợp lệ    | App nhận dữ liệu, chuyển sang gửi backend        | Log event time                             |
| PK-22 | Thành công FaceID        | Thiết bị hỗ trợ FaceID          | User xác thực FaceID            | Như PK-21                                        |                                            |
| PK-23 | Fallback PIN             | Biometrics đã fail trước đó     | User chọn dùng PIN và nhập đúng | App nhận dữ liệu xác thực hợp lệ                 |                                            |
| PK-24 | User hủy prompt          | OS prompt đang hiển thị         | User chọn Cancel                | App hiển thị thông báo hủy nhẹ, không coi là lỗi | Không popup lỗi đỏ                         |
| PK-25 | Sai sinh trắc nhiều lần  | OS prompt hiển thị              | User xác thực sai vượt ngưỡng   | App hiển thị thông báo thất bại + cho phép retry | Không tiết lộ lý do chi tiết               |
| PK-26 | Lỗi không xác định từ OS | OS trả lỗi bất thường           | User thực hiện đăng nhập        | App hiển thị generic error + nút Retry           |                                            |

### Nhóm D: Gửi dữ liệu lên Backend
| ID    | Title                        | Given                                | When                            | Then                                                                               | Notes                  |
| ----- | ---------------------------- | ------------------------------------ | ------------------------------- | ---------------------------------------------------------------------------------- | ---------------------- |
| PK-30 | Payload hợp lệ               | OS auth success                      | App chuẩn bị request            | Payload chứa challenge, credentialId, clientDataJSON, authenticatorData, signature | Không log PII          |
| PK-31 | Thiếu signature 🔐            | OS auth success                      | App gửi request thiếu signature | Backend trả 400; UI báo không đăng nhập được                                       | Không retry tự động    |
| PK-32 | Signature sai 🔐              | Có payload gốc                       | App sửa signature rồi gửi       | Backend trả invalid signature; UI báo chung                                        | Không lộ hash expected |
| PK-33 | CredentialId không tồn tại 🔐 | Không có credential id trong backend | App gửi credentialId random     | Backend trả lỗi credential invalid; UI gợi ý fallback SĐT                          |                        |
| PK-34 | Network timeout              | Kết nối yếu                          | Request quá timeout             | UI hiển thị Retry + fallback SĐT                                                   | Spinner dừng           |
| PK-35 | Retry thành công             | Một lần timeout đã xảy ra            | User bấm Retry                  | Request thành công, tiếp tục risk check                                            | Max retry ≤2           |

### Nhóm E: Phân loại rủi ro
| ID    | Title                      | Given                        | When                        | Then                                    | Notes             |
| ----- | -------------------------- | ---------------------------- | --------------------------- | --------------------------------------- | ----------------- |
| PK-40 | Low risk -> login          | Backend đánh dấu low risk    | App nhận response backend   | App lưu token & vào Home                | Secure storage    |
| PK-41 | High risk -> bổ sung       | Backend đánh dấu high risk   | App nhận response backend   | App mở flow Captcha/Face Matching entry | Không lưu token   |
| PK-42 | High risk pass -> vào Home | User hoàn thành Captcha      | Backend re-evaluate success | App điều hướng Home                     | Integration point |
| PK-43 | High risk bỏ dở            | High risk flow đang hiển thị | User đóng màn hình          | Không có session; vẫn ở login           |                   |

### Nhóm F: Điều hướng & Phiên
| ID    | Title                       | Given                                     | When                               | Then                                    | Notes             |
| ----- | --------------------------- | ----------------------------------------- | ---------------------------------- | --------------------------------------- | ----------------- |
| PK-50 | Chỉ điều hướng khi low risk | Có cả tài khoản high/low để test          | User đăng nhập bằng cả 2 tài khoản | Home chỉ mở ở low risk                  |                   |
| PK-51 | Chống double prompt         | Nút Passkey sẵn sàng                      | User tap nhanh ≥3 lần              | Chỉ 1 prompt hiển thị, không crash      | Debounce hiệu lực |
| PK-52 | Giữ phiên hợp lệ            | User đã đăng nhập trước đó (token hợp lệ) | User mở app lại                    | Bỏ qua màn hình login                   |                   |
| PK-53 | Token hết hạn               | Token đã expired                          | User mở app                        | Quay lại màn hình login với nút Passkey |                   |

### Nhóm G: Bảo mật & Edge Cases
| ID    | Title                  | Given                                | When                                  | Then                                           | Notes                        |
| ----- | ---------------------- | ------------------------------------ | ------------------------------------- | ---------------------------------------------- | ---------------------------- |
| PK-60 | Replay attack 🔐        | Đã có request hợp lệ trước đó        | Gửi lại y nguyên payload              | Backend từ chối (challenge invalid)            | Challenge single-use         |
| PK-61 | Lệch giờ client 🔐      | Đồng hồ hệ thống bị chỉnh            | User đăng nhập                        | Xác thực vẫn hoạt động bình thường             | Nếu phụ thuộc clock phải doc |
| PK-62 | Thêm field lạ 🔐        | Có proxy modify                      | App gửi payload thêm field bất thường | Backend 400 hoặc bỏ qua an toàn                | Không crash server           |
| PK-63 | Kill app giữa prompt   | OS prompt đang hiển thị              | User force close rồi mở lại           | Không có session; quay về login                |                              |
| PK-64 | Offline sau OS success | OS auth success                      | Network bị tắt trước khi gửi          | UI báo lỗi kết nối + Retry                     | Không mất credential local   |
| PK-65 | Thay đổi biometric 🔐   | User thêm fingerprint mới            | User đăng nhập Passkey                | (Optional) Backend/OS flag -> chuyển high risk | Backlog policy               |
| PK-66 | Credential revoked 🔐   | Credential nằm trong revocation list | User đăng nhập                        | Backend trả revoked; gợi ý fallback SĐT        | Audit log                    |

### Nhóm H: UX & Thông điệp
| ID    | Title                   | Given              | When                      | Then                                                        | Notes                 |
| ----- | ----------------------- | ------------------ | ------------------------- | ----------------------------------------------------------- | --------------------- |
| PK-70 | Thông báo fail rõ ràng  | OS auth fail       | User thấy thông báo       | Nội dung: "Đăng nhập bằng Passkey không thành công" + Retry | Không jargon          |
| PK-71 | Thông báo hủy khác fail | User cancel prompt | App xử lý cancel          | Hiển thị: "Bạn đã hủy xác thực" (nhẹ)                       |                       |
| PK-72 | Loading state chuẩn     | Đang chờ backend   | User vừa hoàn tất OS auth | Spinner xuất hiện, nút disabled                             | ARIA role=progressbar |
| PK-73 | Accessibility button    | Screen reader bật  | Focus vào nút Passkey     | SR đọc label rõ + action hint                               |                       |

---
## 4. Traceability với Sequence Diagram
| Diagram Phase                     | Scenario Range |
| --------------------------------- | -------------- |
| Kiểm tra hỗ trợ Passkey           | PK-01..04      |
| Chọn luồng SĐT                    | PK-10..11      |
| Chọn Passkey & hiển thị prompt    | PK-20          |
| Xác thực OS (success/fail/cancel) | PK-21..26      |
| Gửi dữ liệu xác thực              | PK-30..35      |
| Risk evaluation (High/Low)        | PK-40..43      |
| Điều hướng & phiên                | PK-50..53      |
| Bảo mật nâng cao                  | PK-60..66      |
| UX & thông điệp                   | PK-70..73      |

---
## 5. Ghi chú thực thi
- Mock backend nên hỗ trợ ép trạng thái: `risk=high|low`, `error=invalid_signature`, `revoke=true`.
- Nên log `challengeId`, thời gian round-trip để theo dõi hiệu năng.
- Đảm bảo không log raw signature hoặc biometric data.
- Kịch bản bảo mật có thể đưa vào bộ kiểm thử định kỳ (regression) mỗi lần thay đổi logic xác thực.

## 6. Backlog / Future
- Flow đăng ký (enrollment) Passkey (chưa nằm trong scope test file này).
- Attestation format & policy chi tiết.
- Kiểm thử quốc tế hóa thông điệp (i18n) ngoài tiếng Việt.

---
Generated: 2025-09-12
