Về việc lấy chứng nhận FIDO - Functional Certification: Servers

Nếu mình muốn phương thức xác thực mà mình đang triển khai là Hình thức xác thực FIDO được công nhận trong Thông tư 50, thì mình phải thỏa mãn 3 điều
a. Private key
b. Public key
c. Chứng chỉ

Hiện tại Điểm a và Điểm b đã thỏa mãn. Điểm c là điểm cần lưu ý:


### Câu hỏi: 
MoMo có cần lấy chứng nhận **FIDO Functional Certification: Servers** khi khiển khai Passkey hay không?

### So sánh dễ hiểu:
"Hàng nhà làm, sạch 100%" vs "Sản phẩm đạt chứng nhận GlobalGap về an toàn thực phẩm, truy xuất nguồn gốc, bảo vệ môi trường và sức khỏe người lao động" 

### Chi tiết nội dung: 
- Legal: Thông tư 50 có đề cập việc lấy chứng nhận.
- Competitor analysis: Cake by VPBank có lấy chứng nhận (Cake cũng có phương thức đăng nhập bằng Passkey).
- Lợi ích mang lại
- Chi phí

#### 1. Thông tư 50 có đề cập việc lấy chứng nhận
Khoản 7, Điều 11 Thông tư 50 quy định về "Hình thức xác thực FIDO". Mà theo định nghĩa của fidoalliance.org/passkeys thì: 
"A passkey is a FIDO authentication credential based on FIDO standards". Vậy có thể kết luận là giải pháp Passkey mà MoMo đang triển khai chính là "Hình thức xác thực FIDO" trong thông tư và phải tuân theo quy định của Thông tư.

Trong đó Điểm c của Khoản 7, Điều 11 là điểm cần phải lưu ý: "**Giải pháp** do đơn vị **tự triển khai** hoặc sử dụng của bên thứ ba cung cấp phải được cấp chứng nhận của tổ chức được Liên minh FIDO (FIDO Alliance) công nhận."
- "Chứng nhận": 
  - Functional Certification: Servers" -> MoMo có thể lấy cái này
  - Functional Certification: Authenticators/Clients" -> Cái này không dành cho MoMo
    - Authenticator: Roaming authenticator (vd: Yubikey) hoặc Platform authenticator (vd: Apple Face ID, Windows Hello, Android Fingerprint)  
    - Client: Trong ngữ cảnh FIDO2 thì Client là OS (Android, iOS), Browser (Chrome, Safari). App MoMo là Relying Party, không phải là Client trong ngữ cảnh này.

#### 2. Cake by VPBank có lấy chứng nhận
- Năm 2023, Cake triển khai giải pháp đăng nhập bằng Passkey (Cake gọi giải pháp của họ là FIDO2). Nguồn: https://cake.vn/tin-tuc/hoat-dong/ngan-hang-so-cake-va-chuan-xac-thuc-khong-mat-khau-fido2
- Năm 2025, Cake lấy chứng nhận FIDO2 Server. Nguồn: https://cake.vn/tin-tuc/hoat-dong/cake-by-vpbank-dat-chung-nhan-bao-mat-fido2
- Cake hiện đang dùng badge của FIDO Alliance trên Splash screen và Home screen.

#### 3. Chi phí: 
Chứng nhận có khung giá riêng cho member và non-member của FIDO Alliance.
- Dò tìm trong danh sách https://fidoalliance.org/members, không có từ khóa "MoMo" hoặc "MService" hoặc "M_Service" hoặc "M Service". Vậy PO đang kết luận MoMo không phải là thành viên của FIDO Alliance. Vậy mức giá để lấy chứng chỉ "Server (Functional) Certification" áp dụng cho MoMo là $9,000 USD. Nguồn https://fidoalliance.org/certification/user-authentication-certification-registration-fees

#### 4. Lợi ích:
##### Cho User
- Việc MoMo được lấy chứng nhận sẽ là minh chứng cho việc MoMo tuân thủ được các practices phía server để đảm bảo giải pháp hoạt động ổn định, an toàn cho người dùng.  
    
##### Cho MoMo
- Tuân thủ Thông tư 
- Tránh được các rủi ro bảo mật tiềm ẩn
- Đảm bảo tính tương thích
- Tăng cường uy tín

In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole][1], and that means comfort.

[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"

<https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"

[1]: "User Authentication Certification Fees | FIDO Alliance", FIDO Alliance, Nov. 13, 2023. https://fidoalliance.org/certification/user-authentication-certification-registration-fees/ (accessed Oct. 16, 2025).
‌

--- 
Gửi chị Lan Anh
Dear chị Lan Anh,
Giải pháp Passkey mà MoMo đang phát triển 


Passkeys use a challenge-response authentication protocol that is based on asymmetric cryptography.

"Xác nhận giao dịch": là hình thức xác nhận bằng phương tiện điện tử để thể hiện sự chấp thuận của khách hàng đối với các thông điệp dữ liệu trong giao dịch điện tử.Z


https://www.passkeycentral.org/introduction-to-passkeys/passkey-security#overview