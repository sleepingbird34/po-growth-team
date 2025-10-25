# 2025

## September

<!-- Sep 1, 2025 -->
### Sep 1, 2025
#### PO tasks
- Add vô FigJam screenflow của Facebook khi Tạo Passkey, Đăng nhập bằng Passkey
    - Tạo Passkey
        - Tạo Passkey, KHÔNG có Passkey trong Google Password Manager
        - Tạo Passkey, CÓ Passkey trong Google Password Manager
    - Đăng nhập bằng Passkey 
        - Đăng nhập bằng Passkey, Có Passkey trong Google Password Manager
        - Đăng nhập bằng Passkey, KHÔNG có Passkey trong Google Password Manager  
    - Xóa Passkey
        - Xóa Passkey, Có Passkey trong Google Password Manager
        - Xóa Passkey, KHÔNG có Passkey trong Google Password Manager


#### Kindergarten tasks
- ✅ Giải thích vấn đề tại sao nhập char[3] mà vẫn chạy lệnh scanf() và printf() và in ra được.
    - [Link Meet](https://meet.google.com/cdu-kgzy-gzs)

#### PTSP tasks
- ✅ Trả lời bình luận của anh Hoai Nguyen tại post [Reaction UX – Tập 1: Momo & tính năng thông báo](https://www.linkedin.com/posts/hoai-nguyen-5a804012a_reaction-ux-t%E1%BA%ADp-1-momo-t%C3%ADnh-n%C4%83ng-th%C3%B4ng-activity-7367116040163483648-gn60)
    
    - ✅ [Giới thiệu MoMo cũng có chỗ tắt bớt thông báo trong app](https://www.linkedin.com/feed/update/urn:li:activity:7367116040163483648/?commentUrn=urn%3Ali%3Acomment%3A%28activity%3A7367116040163483648%2C7368138418855292928%29&dashCommentUrn=urn%3Ali%3Afsd_comment%3A%287368138418855292928%2Curn%3Ali%3Aactivity%3A7367116040163483648%29) trong post ở LinkedIn
    - ✅ [Comment để trình bày các vấn đề User gặp phải](https://chat.google.com/room/AAAAPhSDa4Q/IhKfVdAK7rQ/aPcO1B8pgo0?cls=10) vô group GrowthxBankxRisk~~

- Post video khách hàng quăng Loa MoMo vô sọt rác vô Happy User
    - ✅ Lưu lại Các thông tin cần thiết 
        - [Link video đã bị gỡ](https://www.tiktok.com/@huong_bac_2/video/7543509158583127303)
        - [Account TikTok](https://www.tiktok.com/@huong_bac_2/video/7543509158583127303
    )
        - [Record màn hình](https://photos.app.goo.gl/PGHgfBJQZokEyfb59)
    - ✅ [Raise vấn đề trong Happy User](https://chat.google.com/room/AAAAyETE-Lo/u45gBktN2oI/u45gBktN2oI?cls=10)

- ✅ Report vấn đề Bể font + lệch hình trong promotionhub  
Status: Solved
    - Mã phản ánh: #250901.0008784. 
    - Thời gian gửi: 20:50 - 01/09/2025

#### Side tasks
- Mua dán màn hình iPhone

#### Grooming chốt phương án (theo từng màn hình):
##### 1. Màn tùy chỉnh tài khoản:
###### 1.1. Luôn hiện hay hiện khi thỏa điều kiện item Passkey?

- [Hỏi team anh Cường] Item "Passkey" trong list "Cài đặt bảo mật" mình sẽ LUÔN hiện, hay check điều kiện thiết bị đủ điều kiện mới hiện.  
- Follow-up questions:
    - [Hỏi team anh Sơn] Để kiểm tra thiết bị đủ điều kiện sử dụng Passkey thì Android/iOS có sẵn hàm? Hay mình tự xây dựng?
        - Điều kiện sử dụng Passkey:
            - Android:
                - Android 9+
                - Google Play Services
                - Screen Lock: vân tay, khuôn mặt, mã PIN, hình vẽ
            - iOS:
                - iOS 16+
                - iCloud Keychain
                - Two-Factor Authentication for Apple account

###### 1.2. Giữ hay không giữ Badge trạng thái "Tạo/Chưa tạo" passkey
- [Hỏi team UX] Nếu bỏ badge thì có ảnh hưởng gì đến trải nghiệm của khách hàng?
    - If giữ: 
        - [Hỏi team anh Minh]: Bên team anh Minh có thể hỗ trợ MaxAPI để lấy trạng thái "Có/Chưa có" passkey không?

##### 2. Flow tạo mới passkey
- [team anh Cường và team UX] Nếu triển khai theo Flow hiện tại có gặp những khó khăn gì không?
    - Flow hiện tại:
        Nhấn entry point ở "Tùy chỉnh tài khoản" -> If chưa có Passkey thì Onboarding screen -> Các bước tạo -> If success thì Màn Danh sách Passkey
    - Flow alternative:
        - Nhấn entry point ở "Thùy chỉnh tài khoản" -> Màn Danh sách Passkey
            - If list rỗng thì hiện nút "Tạo Passkey" 
            - If list không rỗng thì hiện danh sách các passkey
- [Follow-up question] [Hỏi team anh Cường] Design có bị thiếu những thành phần gì cần bổ sung không?

##### 3. Bottom sheet xác thực user bằng Complex password / PIN trước khi tạo Passkey
- [team anh Sơn, UX]
    - Hiện tại chưa có Bottom sheet nhập Complex Password để xác thực người dùng, thì để xây thêm Bottom sheet Complex Password là tích hợp luôn vào Bottom sheet PIN hiện có (1 module, 2 tính năng) hay tách ra thành 2 module, 2 tính năng
    - Mình có sử dụng tiếp design hiện có của Bottom sheet PIN?

- [team BE, team anh Cường]
    - Theo module Bottom sheet nhập PIN hiên tại, thì nếu người dùng có bật "Sinh trắc học - Dùng thay cho mật khẩu" ở Tùy chỉnh tài khoản thì người dùng sẽ không cần phải nhập PIN để xác thực, mà dùng biometrics thiết bị (vân tay, khuôn mặt) để xác thực. Vậy mình có áp dụng tiếp logic đó khi Xác thực người dùng trước khi tạo Passkey không
    - Có áp dụng rule vừa nêu luôn cho Bottom sheet nhập Complex Password luôn không?

##### 4. Màn Log in bằng Passkey 
- [team anh Sơn, team BE]: 
    - Hiện tại là đăng nhập cross-device bằng QR chưa thể thực hiện được, vậy thì (1) Tìm hướng xử lý hay (2) Chặn luôn flow đó
        - If chặn luôn flow đó, thì có config khi gọi hàm để không hiện tùy chọn đó ra không?
    - Sau khi OS trả về kết quả đăng nhập passkey thành công, thì các bước để kiểm tra tài khoản này có thuộc blacklist thì đã có hàm sẵn để gọi chưa ạ?


##### 5. Danh sách stakeholders:
- dat.bui2@mservice.com.vn,
- hien.cao1@mservice.com.vn,
- nhat.nguyen12@mservice.com.vn,
- toan.le@mservice.com.vn,
- dat.le1@mservice.com.vn,
- mien.pham@mservice.com.vn,
- nguyen.nguyen26@mservice.com.vn,
- hoangson.pham@mservice.com.vn,
- han.nguyen2@mservice.com.vn,
- minh.nguyen3@mservice.com.vn,
- thanh.le9@mservice.com.vn,
- cuong.phan@mservice.com.vn,


<!-- Sep 2, 2025 -->

### Sep 2, 2025
#### PTSP tasks
- Raise vụ Lương Đỗ thanh toán tiền điện trên MoMo 
    - Có ai dập lửa vụ này không ạ  
    Video 337k view, 7114 tim, 549 comment  
    KOC lên video từ ngày 21/8 về việc tự dưng có một hóa đơn điện nhảy vào tài khoản của KOC, KOC  không để ý và bấm thanh toán.
    Sau kiểm tra lại thì đó là hóa đơn của người khác 😶 
    Liên hệ với MoMo thì MoMo kêu liên hệ với điện lực.
    Video hiện đang 337k view, 7114 tim, 549 comment rồi ạ. Số comment gây bất lợi cho MoMo đang nhiều ạ

    -> Vụ này có thể xảy ra được có thể là do:
    - Tính năng "Thêm bạn bè, người thân theo dõi hóa đơn" có thể thêm một người chưa là bạn bè với mình, chưa từng có giao dịch với mình vào theo dõi hóa đơn đó, nên có thể KOC trong trường hợp này đã bị
    
    Trường hợp này xảy ra khi
    - Mã số hóa đơn điện lực của người thanh toán và người được thanh toán giống nhau
    - Người được thanh toán biết được số điện thoại của người thanh toán hóa đơn.

    Một nhà hiền triết đã nói rằng "Trên đời này cái quái gì cũng có thể xảy ra" 

#### Side tasks
- ⚠️ Kêu Sister với Quốc Hưng bỏ theo dõi hóa đơn điện nước của 5 Hương.
- ~~Cài đặt Teamviewer lên PC để xem được nội dung trên iPhone~~
- Gửi email đến IT Helpdesk để xin cài đặt vân tay
- To-buy: 
    - Hasaki: Dầu gội Dove, kem xả, dưỡng da Hatomugi
    - AEON: kệ để dép, sữa chua, bánh bao, bánh giò, trứng

#### Vocabulary
- ECOM

<!-- Sep 3, 2025 -->

### Sep 3, 2025
#### PO tasks
- Tham gia meeting Weekly team Growth (dời sang sáng Wednesday vì sáng Tuesday là ngày lễ)
    - **Đổi lại UI vì UI hiện tại đang mix giữa Switch và Section (Bấm vào Arrow): Anh Tuệ và anh Hiển recommend thay đổi**  
    - Sau khi có UI mới từ dat.bui2
        - Trình bày lại với thanh.le9 và BE team về sự thay đổi và tham khảo về tính khả thi
- Đọc Thông tư 40
- Tham gia meeting [Growth] Review Onboarding flow
    - [Slide](https://docs.google.com/presentation/d/1ruCfifjlk8bFMIt_H8hziSoNWiB2pXfIQMESOMHAJqQ/edit?slide=id.g37aac40f723_0_10#slide=id.g37aac40f723_0_10) 
        - Slide 3 - Changelog
            - A/B - TT40 - Remove NFC + FM prompt at registration -> Có thể gây ra vấn đề bắt người dùng NFC + FM lúc họ đang thanh toán. RẤT BẤT TIỆN 🆘
            - Remove NFC + FM prompt at 1st Cashin -> Những user không có NFC (35% số lượng người dùng MoMo) thì lúc họ nạp tiền vô thì không bắt họ NFC, tới lúc họ dùng tiền thì bắt họ NFC thì họ lấy NFC đâu ra. Hiện có 1 luồng là họ có thể gọi lên CS, và CS liên hệ Risk để duyệt. RẤT BẤT TIỆN 🆘
            - Module iProov sắp tới sẽ áp dụng thay thế cho module eKYC in-house của MoMo
- Viết vào PRD: Nếu thiết bị hiện tại không có sẵn Passkey, phải cho phép người dùng bấm vào để hiện mã QR (của OS) để User dùng thiết bị có Passkey để quét mã (đây là cơ chế của Android và iOS có hỗ trợ )
- Hỏi Auth 2.0 - Internal là làm Bottom sheet nhập Complex Password thì ai phụ trách làm và làm trong bao lâu?
    - nguyen.nguyen26 trả lời là team Nguyên làm; làm trong 1 sprint
#### PTSP tasks
- Hỏi BE tại sao số 0373142902 không nhận được OTP khi đăng nhập trên thiết bị mới + đi luồng Quên mật khẩu. 
    - Lấy thông tin đã tổng hợp từ [thread này](https://chat.google.com/room/AAAAMuSrSCo/Yys3mjfPnP0/Yys3mjfPnP0?cls=10)

#### Side tasks
- To-buy:
    - ✅ Cây lăn bụi để lăn cái áo MoMo
    - Xửng hấp

<!-- Sep 4, 2025 -->

### Sep 4, 2025
#### PO tasks:
- Hỏi bên nguyen.nguyen26 về vụ bottom sheet là nó đang double người dùng Fingerprint 
- Hỏi anh Hiển: Tại sao phải nhận OTP bằng Số điện thoại mà không bổ sung thêm nhận OTP bằng 2FA / Email.
- Bug - luồng new - loating icon chào bạn mới, sau khi giao dịch xong thì cái icon đó vẫn còn.

- Ở màn Smart OTP lúc thanh toán thì không thể bấm Back được

<!-- Sep 5, 2025 -->

### Sep 5, 2025
#### PO tasks
- Liên hệ với thanh.le9 để grooming
- Liên hệ với nguyen.nguyen26 để grooming vụ bottom sheet.
- Edge case Passkey 
    Chuyện gì xảy ra nếu thiết bị của người dùng sử dụng khoá truy cập bị mất hoặc bị đánh cắp?
     - Người dùng sẽ mất quyền truy cập vào tài khoản của họ
     - Người dùng có thể thu hồi khoá truy cập của thiết bị bị mất, rồi tạo khoá truy cập mới bằng cách đăng nhập vào trình cung cấp khoá truy cập trên một thiết bị khác
     - Người dùng sẽ phải đặt lại mật khẩu Tài khoản Google của họ

 Vụ tắt Biometrics thiết bị (FaceID, Fingerprint) nếu 

- Các app trên 1 tỷ Users: Facebook, Whatsapp, TikTok, LinkedIn, 
Facebook
![alt text](passkey-assets/passkey-facebook.jpg)
GitHub
![alt text](./passkey-assets/passkey-github.png)
Binance
![alt text](./passkey-assets/passkey-binance.jpg)
WhatsApp
![alt text](passkey-assets/passkey-whatsapp.jpg)
TikTok

- Xin quyền để chỉnh sửa card trên app-x

<!-- Sep 6, 2025 -->

### Sep 6, 2025

MoMo Talent Tasks:
- Viết file progress của HR

PO tasks:
- Đọc Thông tư 40, 50, Nghị định 13, Quyết định 2345
- Prototype Tạo Passkey
- Liên hệ với bên Security Center để nói chuyện với stakeholder bên đó về việc gắn entry point để Tạo Passkey
- Check lại xem là Đạt có sửa lại vụ Tạo passkey thành công là có đá qua bên màn quản lý passkey luôn không
- Kiểm tra vụ đăng nhập cross device với nguyen.nguyen26
- Ghim lại mấy ngày sprint chạy ở các team Tech trên Calendar
- Kiểm tra lại app Grab có cho đăng nhập trên iPhone XS chưa, để xem thử "Thiết bị này" là gì.
- "Đây không phải tôi" nằm đó là đúng không vậy
- Liên hệ BE để hỏi về vụ blacklist
- Khi người dùng mất thiết bị có passkey thì phải làm sao
- Khi tạo passey thành công thì sẽ thông báo qua email cho người dùng biết

Side tasks:
- ~~Gọi cho mẹ hỏi mẹ chiều đi đâu, mấy giờ~~
- ~~Liên hệ với Techcombank về điều kiện nâng hạn mức thẻ~~
- Mua gạc tẩm cồn
- Lau máy quạt để bàn
- Khâu lại tóc
- Giặt gối để kê lưng
- Sạc tai nghe
- Sạc máy quạt để bàn
- Mua đựng thẻ
- Hỏi bên VNPAY để chuyển nhượng tài khoản

### Sep 7, 2025

#### PO tasks:
- OTP gửi tới khách hàng phải kèm thông tin thông báo để khách hàng nhận biết được mục đích của OTP;
- Time-based One-Time Password
- thông tin sinh trắc học thiết bị
- Liên minh châu Âu EU cũng quy định trong Chỉ thị về dịch vụ thanh toán mới (PSD2) vào năm 2019, phương thức gửi OTP qua SMS không đáp ứng được yêu cầu của EU. chữ ký số đảm bảo 3 tính chất là tính toàn vẹn, tính xác thực và tính chống chối bỏ.
- bảo vệ SIM bằng mã PIN hoặc hình thức xác thực OATH

#### Side tasks:
- Đem rau nấu mì


### Sep 8, 2025
#### PO Tasks
- Liên hệ với bên Security Center để nói chuyện với stakeholder bên đó về việc gắn entry point để Tạo Passkey
- Liên hệ BE để hỏi về vụ blacklist
- Kiểm tra lại app Grab có cho đăng nhập trên iPhone XS chưa, để xem thử "Thiết bị này" là gì.
- Ghim lại mấy ngày sprint chạy ở các team Tech trên Calendar
- [App platform] Kiểm tra vụ đăng nhập cross device với nguyen.nguyen26
    - Kiểm tra đăng nhập bằng Passkey trên XS được không
    - Kiểm tra đăng nhập cross device giữa XS và 13 Pro Max
- [UX] Check lại xem là Đạt có sửa lại vụ Tạo passkey thành công là có đá qua bên màn quản lý passkey luôn không 
- Xin quyền tạo card trên App X
- Lên lịch Review lại Sequence diagram & Screen flow

- [App platform] Bottom sheet cho Mật khẩu phức tạp

- điện thoại A có passkey, điện thoại B KHÔNG có passkey. điện thoại b muốn đăng nhập bằng passkey thì hiện ra một cái qr để cho điện thoại a quét. điện thoại a xác nhận bằng sinh trắc học thiết bị của điện thoại a -> if điện thoại a xác thực sinh trắc học thiết bị successfully, điện thoại b đăng nhập thành công. momo trên điện thoại a văng ra, hiện thông báo momo hiện đang đăng nhập trên thiết bị khác, nếu đó không phải là bạn, hãy liên hệ với momo ngay.


Ở màn hình login của grab
nếu detect thấy trên thiết bị có Passkey thì hiện luôn Modal dialog của OS để đăng nhập bằng passkey. 

Nếu không detect được passkey thì không 

nhiều thiết bị 
has_passkey, doesnot_have_passkey, synced Google / Apple account
android phone #1, passkey sync to Google Password Manager on Android phone #1, Android phone #2 does not have Passkey, Android phone #1 and Android phone #2 have difference Google account
android, android, Yes
android, ios, No 
ios, android, No
ios, ios, No
ios, ios, Yes

#### Side tasks
- Nghe thử tai nghe Sony ở showroom
- Hiện tại mình có cho phép đùng Passkey đang trên thiết bị A để đăng nhập trên thiết bị B không ạ
- https://chat.google.com/room/AAAAwXEs9mc/zV9wTDxpivM/zV9wTDxpivM?cls=10
- Cross device login
- Device Fingerprinting

### Sep 10, 2025

#### Tasks của Vinh
- FAQ: Bộ các câu hỏi người dùng thường gặp khi đăng Đăng nhập. ETA: 14/10.

#### Learned
- Principle of Least Privilege

### Sep 11, 2025

### Sep 17, 2025

#### PO tasks
- Cập nhật lại PRD
- Gửi email đến Legal
- Viết card cho bên anh Minh
- Hỏi anh Minh QC của anh Minh test luôn phần passkey được không
- Vấn đề kiểm tra quyền trợ năng Accessibility
- Hỏi Khánh mấy thông tin metrics làm sao để lấy

#### Side tasks
- mua nước rửa tay
- mua gạc tẩm cồn
- Mua miếng lót chuột
- Đặt lịch tiêm cúm vnvc
- cập nhật lại địa chỉ email hello@nguyenduynhat.com
  
#### Vocab
- entropy - passkey https://medium.com/androiddevelopers/bringing-seamless-authentication-to-your-apps-using-credential-manager-api-b3f0d09e0093
- Attestation and Assertion https://developer.mozilla.org/en-US/docs/Web/API/Web_Authentication_API/Attestation_and_Assertion
- device fingerprint: 5C:B4:F8:2E:88:11:D8:D4:90:61:49:F5:9F:C8:E7:FC (pair android and windows for wireless debugging)

### Sep 20, 2025
#### Learning
- VinCSS security key
- Singleton
- Facade layer
- MVVM
- Clean architecture
- Dependency Injection
- momo ibft

### Sep 25, 2025
#### PO Tasks
- "Press Home button to verify" ở trên cái UI Biometrics của OS là gì
- Viết Card PDFOUN-959
- Hoàn thành Bottom sheet flow chart https://www.figma.com/board/K6qKjxaXK1Bqswt1j8EnFu/Passkey---Draft?node-id=883-3711&t=i8fsl6mTrzcGiQsV-0

### Sep 26, 2025
#### PO Task
- Nhắn đạt về card
- Config text hiển thị trên UI của Biometrics
- 
#### Knowledge
- Relying party, attestation
- MCP

### Sep 28, 2025

#### PO tasks: 
- Soạn bộ câu hỏi FAQ https://safety.google/authentication/passkey/
- The Missing Link: Mobile Authentication for Secure Identity Binding: https://authenticatecon.com/event/authenticate-2025/

#### Knowledge
- Kotlin Multiplatform Mobile
- https://developers.google.com/identity/passkeys?authuser=1
- sign up with passkey: nhập số điện thoại, và sau đó chọn 1 phương thức xác thực cho passkey
- phải xuất hiện được trên đây: https://www.passkeys.com/websites-with-passkey-support-sites-directory
-  When logging in, the user verifies their identity with something they have (their device) and something they are (biometrics) acting as a multi-factor authentication method (MFA). https://www.passkeys.com/passwordless-authentication-solutions
-  sign up with passkey: nhập số điện thoại, và sau đó chọn 1 phương thức xác thực cho passkey 

#### Notes
- [BE] API Delete Passkey [Ready for UAT]
  - API Get list of Passkey [Đang gặp Issue, BE sẽ thông tin vào đầu tuần 29/10]
  - ⬇️
- [CoreX] Bottom sheet nhập Complex Password [chưa start 🥲]
  - ⬇️
- [CoreX] PasskeyManager [chưa start 🥲]
  - ⬇️
- [AppX] Integrate ở màn Tùy chỉnh tài khoản [pending - chờ CoreX]
- [ACS] Integrate màn Nhập Số điện thoại [pending - chờ CoreX]
  - ⬇️
- [CoreX] QC của CoreX test màn Nhập số điện thoại cho ACS [pending - chờ ACS] 

### Sep 29, 2025
#### PO Task
- Gửi thông báo đến BE để cập nhật nội dung email Cảnh báo bảo mật 
  - Thay hoàn toàn các chữ "Ví"
  - Cập nhật lại link cho các icon
  - Cập nhật địa chỉ công ty
  - Cập nhật link cho button "Mở ứng dụng"
  
#### Knowledge
- https://developer.android.com/identity/sign-in/restore-credentials?authuser=1
- https://developer.android.com/identity/sign-in?authuser=1
- https://developer.android.com/identity/sign-in/credential-manager?authuser=1#show-info

### Sep 30, 2025
#### PO Tasks
 
#### Knowledge
- https://developer.mozilla.org/en-US/docs/Web/API/Web_Authentication_API/Authenticator_data#attestedcredentialdata
- RSA256
- JWT 
- ISO 8061 format
- Gửi temp complex pass, Màn login chưa cho phép nhập PIN


## October
### Oct 1, 2025
#### PO Tasks

#### Knowledge
- CTAP 
- WebAuthn 
- FIDO2
- FIDO2 vs FIDO
- Trường hợp change device có sync và không sync Apple / Google Account
- VinCSS audit passkey
- DBA
- VinCSS FIDO2® Server
- https://fidoalliance.org/certification/functional-certification/functional-certification-servers/
- https://fidoalliance.org/android-now-fido2-certified-accelerating-global-migration-beyond-passwords/ 
- Public Key Cryptography
- Right to be Forgotten GDPR

### Oct 3, 2025
#### PO Tasks
#### Knowledge
- Use case diagram, State machine diagram, Sequence diagram
- https://w3c.github.io/webauthn/#dom-publickeycredentialcreationoptions-excludecredentials
- include <<include>> 
- extend <<extend>>
- association relationship
- generalization relationship
- Use case diagram, Activity diagram, State machine diagram, sequence diagram, Class diagram
- Rút tiền --> <<include>> Kiểm tra số dư 
- Tạo card cho ACS: https://atlassiansuite.mservice.com.vn:8443/browse/ACS-3425


### Oct 9, 2025
#### PO tasks
- [Passkey] Hoàn thiện Figma final gửi Risk ✅
- [Passkey] Hỏi về tính khả thi của Bottom sheet nhập Complex Password ✅
  - https://chat.google.com/room/AAQAbU4AVvY/YeTwbm-xi6Y/YeTwbm-xi6Y?cls=10
  - Tắt badge name của text field complex pass
  - Tăng font size lên headline/default_bold được không?
  - 👉 Khả thi.
  
#### Side tasks
- Học module Reforge ✅
- Đi mua snacks và gifts cho lớp Reforge ✅

### Oct 10, 2025
#### PO tasks

#### Learn
- Tạo namespace cho 2 môi trường
  - janus.mservice.io
  - janus-dev.mservice.io

### Oct 11, 2025
#### PO tasks
- [Passkey] Cập nhật thông tin PRD và thông báo cho CoreX
  - Phương thức Xóa Passkey
- [Passkey] Thêm một card cho BE 
  - Mask data số điện thoại
- [Passkey] Viết thêm vào PRD một section cho Risk
- [Passkey] Viết thêm vào PRD một section cho Legal
- [Passkey] Mỗi tài khoản MoMo chỉ được tạo 1 Passkey
  - Gửi thông tin vào group "[PROTECH] Passkey" thông tin về việc siết điều kiện "Mỗi tài khoản MoMo chỉ được tạo 1 Passkey" thì mới chỉ được ràng buộc bằng Toggle trên UI ở App. 
    - Trong bản Demo hiện tại thì mỗi lần đăng nhập thành công thì vẫn còn có thể tạo thêm 1 Passkey. Khi check bằng Postman thì có thể có luôn 1 list

### Oct 20, 2025
#### PO Tasks
- Gọi tìm hiểu vấn đề của khách hàng
  - https://chat.google.com/room/AAQA4r87TRo/53gnljpQ3X0/yLuBzLJdfJY?cls=10
  - 0345727511
  - Request ID: 1758283519638
  - Nội dung nhắn tin qua SMS:
    - Chào chị, Em là Nhất. Em ở bộ phận Phát triển sản phẩm của MoMo ạ. Khi xem lại phản hồi của khách hàng thì em thấy là vào ngày 19/9/2025 em thấy chị có gửi một yêu cầu hỗ trợ Quên mật khẩu. Em thấy trên ảnh chụp mà chị gửi thì tài khoản đã có bật đăng nhập bằng Vân tay thì em đang muốn biết lý do mà chị không dùng vân tay để đăng nhập mà lại gửi yêu cầu quên mật khẩu.
    - Nếu được thì em xin phép gọi điện cho chị để hỏi thêm thông tin. Cuộc gọi sẽ kéo dài khoảng 15 phút. Sau cuộc gọi em xin gửi 50000đ vào tài khoản của chị như một lời cảm ơn ạ.
    - Thời gian gọi dự kiến là 20h30 ngày 21/10/2025. Nếu được thì nhờ chị phản hồi lại là "OK" ạ. Hoặc nếu chị Không đồng ý cuộc gọi diễn ra hoặc cần thực hiện vào thời gian khác thì nhắn lại giúp em luôn nhé ạ.

### Oct 21, 2025
#### PO tasks
- Vẽ Sequence diagram cho Reverse SMS OTP
  - https://atlassiantool.mservice.com.vn:9443/display/PGT/Reverse+SMS+OTP
- Đi hỏi Miên vụ integrate VinCSS vào hệ thống 
  - App dùng SDK của VinCSS, App gọi Backend, Backend gọi Server của VinCSS.

#### Side tasks
- Phản ánh vấn đề khi cài đặt loa MoMo
  - Thread trao đổi ban đầu, sau đó chat riêng với anh dat.vo1: https://chat.google.com/room/AAAAyETE-Lo/pzQxuzsxm6A/1mv-Kn4425o?cls=10
    - Sau khi về cài đặt loa thì có 1 vấn đề sau ạ
      - Miếng decal chứa mã QR khi nhét vào không khớp hoàn toàn vào khung trống trên bảng nhựa 
        - -> làm cho 3 position markers (3 cái ô vuông đen đen) ở góc của mã QR bị khuyết 
        - -> dẫn đến app bank (TCB, VCB) không quét được mã QR của MoMo

#### Learned 
- HTTP Callback
- out-of-band vs in-band

### Oct 22, 2025
#### PO tasks
- Cập nhật slide New to MoMo
  - https://docs.google.com/presentation/d/12sRNYlsJITNFKBB7ByjHbXrEbb_VN0X_fHgAVehS0P4/edit?slide=id.g372111f2a00_2_198#slide=id.g372111f2a00_2_198
- 

#### Side tasks
- Gác thi và chấm thi giữa kỳ Nhập môn lập trình
- Gửi góp ý text trong hình bị sai chính tả
  - https://genk.vn/3-buoc-don-gian-de-nhan-tien-qua-so-dien-thoai-momo-20251021141027064.chn

#### Learned 
- User story
  - https://www.nngroup.com/articles/ux-user-stories/
- Problem statement
  - https://www.nngroup.com/articles/problem-statements/

### Oct 23, 2025
#### PO tasks
- Thêm event tracking cho Passkey
  - PRD
  - Card ACS
  - Card CoreX
- Nghe audio phỏng vấn khách hàng
  - https://chat.google.com/room/AAQA4r87TRo/8-nUvxf5e_8/8-nUvxf5e_8?cls=10
    - Kinh nghiệm học được để mở đầu câu chuyện là bắt đầu từ việc nói về thú cưng 🙂, xong hỏi về background vòng vòng rồi bẻ lái về những thứ liên quan tới MoMo
    - Demographics 
      - 1999
      - Nuôi chó
      - Buôn bán qua Facebook
      - Gốc Bình Định, Vợ gốc Hoa
    - Nhận tiền
      - Đa phần nhận tiền Ngân hàng
      - Vietcombank
        - Ngày xưa làm Circle K được tạo thẻ
      - TPBank
      - Techcombank
        - Cây nạp tiền mặt "ưu việt"
      - So sánh Vietcombank và Techcombank
        - Vietcombank không bị bắt phải đăng nhập lại khi chạy đa nhiệm, Techcombank mỗi lần ẩn xuống nền là phải đăng nhập lại
        - Cảm thấy an tâm hơn khi dùng Techcombank để giữ tiền 
        - Chị vợ bảo anh chồng tắt Face ID để phòng trường hợp điện thoại bị chiếm quyền kiểm soát thì khi giơ điện thoại lên cũng không bị tự động quét Face ID và bị mất tiền 
          - Đi ngoài đường nhập Password bị bất tiền
        - Để tài sản mỗi chỗ một ít
          - Tiền mặt, Tiền online, Vàng
        - Tiền nhỏ: tiền mặt
        - Tiền lớn: chuyển khoản
        - Sử dụng thẻ tín dụng và giới hạn chi tiêu của thẻ
        - Obvervation của user về hành vi của sinh viên khi xài MoMo
          - Ra đường không có mạng  
          - Có khuyến mãi 
        - Lý do "chưa" dùng MoMo
          - chưa thấy sự nổi trội đặc biệt từ MoMo so với các app ngân hàng
          - chỉ nhớ đến việc sử dụng MoMo khi được nhân viên ở các cửa hàng tiện lợi nhắc, vì dùng MoMo có ưu đãi, nhưng lúc tải thì sợ mọi người phía sau phải đợi lâu nên cũng không tải và thanh toán bằng tiền mặt hoặc chuyển khoản ngân hàng
        - Vợ của anh này dùng MoMo và giới thiệu cho mẹ của mẹ vợ của anh ấy dùng
          - Chị vợ dùng MoMo nhiều
          - Gặp lỗi khi rút tiền từ MoMo sang ngân hàng 
        - Em của anh này dùng MoMo vì chưa đủ tuổi dùng ngân hàng
        - Thời sinh viên không đăng ký MoMo vì sợ lộ thông tin ngân hàng và không có nhu cầu
        - Đã gặp vấn đề liên quan tới việc thông tin bị dùng cho một khoản vay của người khác nên giờ rất quan tâm đến việc bảo mật thông tin 
    - Đề xuất tính năng Trial trong vòng 3 ngày 
    - Chị vợ làm liên quan đến đất đai, luôn tắt thanh toán của thẻ, khi nào cần dùng mới mở ra 
    - Giao diện khó dùng do màu sắc, nhiều tính năng quá, tìm tính năng bị khó
    - Khó quét mã QR offline 
    - Thích cái loa MoMo

#### Side tasks
- Xin quyền truy cập Athena để dùng Mo Da Vinci
- Đọc lại UX Guideline
  - https://zeroheight.com/780fb2963/p/6921ed-de-hieu
- Tìm file UI Kit up-to-date
  - https://www.figma.com/design/BC7t97lROz7R6AZuPJ6pbf

#### Learn
- Onelink Fingerprinting (AC-2052)
  - https://web.dev/learn/privacy/fingerprinting
- Rollout plan App 5.0 
  - https://mail.google.com/mail/u/0/#inbox/FMfcgzQcqRBbCgRfXZBdtzljPZcVNxvc?projector=1
- Team MAS
- Confusion matrix
- App event tracking
  - event name: service_component_clicked = User action something
                service_component_displayed = Hiển thị something
  - param: 
    - service_name
    - screen_name
    - action: nhấn Tiếp tục, Tìm hiểu thêm
    - status: kết quả: SUCCESS, FAILED
    - error_code: mã lỗi BE trả về
    - phone: số điện thoại

### Oct 24, 2025
#### PO tasks
- Hỏi Đạt về việc gửi email khi Tạo / Xóa passkey
  - https://chat.google.com/room/AAQAbU4AVvY/CsT30trDg6Y/CsT30trDg6Y?cls=10
  - Status là được gửi email. Nội dung do PO soạn.
- Thêm event tracking cho Passkey
  - PRD
  - Card ACS
  - Card CoreX

#### Learned
- VNPay Customize keyboard
- Event Definition Language
  - https://atlassiantool.mservice.com.vn:9443/pages/viewpage.action?pageId=154968351
  - https://docs.google.com/document/d/1BrK64CBesXAzGp-VGCD97zym75goKoLqJ-oJdBfI68I/edit?tab=t.0

### Oct 25, 2025

#### Side tasks
- Đăng ký nhận bản tin CX
  - https://msp.mservice.com.vn/MomoPortal/MomoPortalCreateRequest?portalId=2&requestId=580

#### Learned
- Ý, tui cũng fan plantuml đây, tích hợp plantuml vào gitlab pages viết tài liệu bá chấy luôn nha https://voz.vn/t/uml-co-con-đuoc-su-dung.345568/page-2
- [Reverse OTP] Silent network authentication