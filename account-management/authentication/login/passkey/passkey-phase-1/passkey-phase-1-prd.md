
# Passkey - Phase 1

<table>
    <tr>
        <th>Target release</th>
        <td>31 Oct 2025</td>
    </tr>
    <tr>
        <th>Epic</th>
        <td>Tăng tỉ lệ Verify PW success</td>
    </tr>
    <tr>
        <th>Document status</th>
        <td>In Progress</td>
    </tr>
    <tr>
        <th>Document owner</th>
        <td>nhat.nguyen12</td>
    </tr>
    <tr>
        <th>Product Owner</th>
        <td>nhat.nguyen12</td>
    </tr>
    <tr>
        <th>Business Owner</th>
        <td>GMC Retention</td>
    </tr>
</table>


## 1. Overview



## 2. Problem Space
### 2.1 Background and strategic fit

<style>
  table td {
    vertical-align: top;
  }
</style>
<table>
    <tr>
        <td><b>Background</b></td>
        <td>Hiện tại, SĐT cùng với mật khẩu là phương thức xác thực cốt lõi trên nền tảng MoMo. Mặc dù quen thuộc,
            mô hình
            này đang tạo ra những rào cản đáng kể cho h và phát sinh chi phí vận hành cho MoMo, được thể
            hiện qua các
            số liệu hàng tháng: <br>
            <ul>
                <li><b>~1,5 triệu</b> người dùng nhập sai mật khẩu ít nhất một lần.</li>
                <li><b>~500,000</b> người dùng phải đi vào luồng "Quên mật khẩu".</li>
                <li><b>~100,000</b> người dùng phải đi vào luồng "Quên mật khẩu".</li>
            </ul>
            Tình trạng này không chỉ gây gián đoạn trải nghiệm mà còn trực tiếp tạo ra gánh nặng cho bộ phận hỗ trợ,
            với
            ~1,500 ticket yêu cầu hỗ trợ lấy lại mật khẩu được tạo ra mỗi tháng.
        </td>
    </tr>
    <tr>
        <td>
            <b>Objective</b>
        </td>
        <td>
            <b> Đối với Người dùng:</b>
            <ul>
                <li><b>Đăng nhập tiện lợi và nhanh chóng:</b>
                    Cho phép người dùng đăng nhập vào MoMo chỉ bằng một
                    chạm thông qua các phương thức xác thực sinh trắc học (Vân tay/Face ID) hoặc các phương thức mở
                    khóa điện thoại (mã PIN, hình vẽ) trên thiết bị của họ.</li>
                <li><b>An toàn:</b> Giảm rủi ro bị lừa đảo (phishing-resistant) và các rủi ro liên quan đến việc mất
                    SIM do Passkey được mã hóa và không bao giờ rời khỏi thiết bị người dùng.</li>
                <li><b>Giảm bớt phụ thuộc vào SIM/SĐT:</b> Người dùng vẫn có thể truy cập tài khoản MoMo an toàn
                    ngay cả khi mất điện thoại hoặc thay đổi SĐT, miễn là passkey của họ được đồng bộ qua tài khoản
                    đám mây (Apple Keychain/Google Password Manager).</li>
            </ul>
            <b>Đối với MoMo:</b>
            <ul>
                <li><b>Tăng tỷ lệ đăng nhập thành công:</b> Giảm tỷ lệ người dùng thất bại khi đăng nhập do quên mật
                    khẩu hoặc không nhận được OTP.</li>
                <li><b>Giảm thiểu rủi ro và chi phí vận hành:</b> Giảm số lượng yêu cầu hỗ trợ liên quan đến việc
                    mất quyền truy cập tài khoản, quên mật khẩu, từ đó giảm khối lượng công việc bộ phận Chăm sóc
                    khách hàng; Người dùng ít chọn Quên mật khẩu thì sẽ bớt được số lượng tin nhắn SMS gửi đi, từ đó
                    sẽ giảm thiểu được chi phí vận hành.</li>
                <li><b>Nâng cao uy tín thương hiệu:</b> Khẳng định vị thế tiên phong của MoMo trong việc áp dụng các
                    công nghệ bảo mật tiên tiến nhất, củng cố niềm tin của người dùng.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td><b>High-level solution</b></td>
        <td>Tích hợp phương thức <b>Đăng nhập bằng Passkey</b> vào ứng dụng MoMo, hoạt động song song với phương
            thức đăng
            nhập bằng SĐT hiện có.
        </td>
    </tr>
</table>

### 2.2 Feature Value Map

<style>
  table td {
    vertical-align: top;
  }

    table th {
    vertical-align: top;
  }
</style>
<table>
    <tr>
        <th>User problem</th>
        <td>Description - Mô tả</td>
        <td>
            User không thể login thành công vì một số lí do sau:
            <ul>
                <li><strong>Sai mật khẩu / Quên mật khẩu:</strong> Người dùng có thể nhập sai ký tự, hoặc hoàn toàn
                    không nhớ mật khẩu của ứng dụng, hoặc nhầm lẫn với mật khẩu của ứng dụng khác.</li>
                <li><strong>Không nhận được OTP khi vào luồng Quên mật khẩu:</strong> Do sóng điện thoại yếu, hộp
                    thư đến bị đầy, người dùng vô tình bấm chặn đầu số của MoMo, tin nhắn bị chuyển vào mục spam,
                    hoặc do các chính sách chặn tin nhắn rác từ nhà mạng.</li>
                <li><strong>Các lỗi hệ thống khi người dùng tạo mật khẩu đăng nhập mới:</strong> "Đã hết thời gian
                    xử lý. Vui lòng thực hiện lại", ...</li>
            </ul>
        </td>
    </tr>
    <tr>
        <th>Business problem</th>
        <td>Description - Mô tả</td>
        <td>
            Hiện tại trên platform MoMo đang có:
            <ul>
                <li><strong>~1.5tr</strong> user có ít nhất 1 lần ấn sai mật khẩu mỗi tháng</li>
                <li><strong>~0.5tr</strong> user vào luồng quên mật khẩu</li>
                <li><strong>~0.1tr</strong> user quên mật khẩu → không thể đăng nhập được MoMo (cùng tháng)</li>
                <li><strong>~1.5K</strong> raise ticket lấy lại mật khẩu mỗi tháng</li>
            </ul>
        </td>
    </tr>
    <tr>
        <th rowspan="2">Goals</th>
        <td>Qualitative - Định tính</td>
        <td>
            <ul>
                <li>Mang lại trải nghiệm đăng nhập <strong>liền mạch và hiện đại</strong>.</li>
                <li><strong>Cải thiện sự tin tưởng</strong> của người dùng vào hệ thống bảo mật của nền tảng.</li>
                <li>Xây dựng hình ảnh một công ty <strong>luôn đi đầu về công nghệ</strong>.</li>
                <li>Khiến người dùng cảm thấy <strong>an tâm hơn</strong> khi giao dịch trên ứng dụng.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>Quantitative - Định lượng</td>
        <td>
            Input metric
            <ul>
                <li>Tỷ lệ tạo Passkey (Passkey Creation Rate)</li>
                <li>Tỷ lệ sử dụng Passkey trong đăng nhập (Passkey Sign-in Rate)</li>
            </ul>
            <br>
            Output metric
            <ul>
                <li>%MAU</li>
            </ul>
        </td>
    </tr>
</table>

## 2.3. Epic & User Stories

### 2.3.1. Epic

Là một người dùng MoMo, tôi thường xuyên cảm thấy phiền phức khi phải nhớ và nhập mật khẩu. Đôi khi tôi quên mật khẩu và phải trải qua các bước khôi phục phức tạp, hoặc lo lắng về việc tài khoản của mình có thể bị đánh cắp. Tôi mong muốn có một cách đăng nhập vào MoMo vừa nhanh chóng, vừa đảm bảo an toàn tuyệt đối cho tài khoản của mình.

### 2.3.2. User stories

- Story #1: Kích hoạt phương thức đăng nhập mới

    - **As a** một user MoMo muốn có trải nghiệm đăng nhập tốt hơn,
    - **I want to** dễ dàng kích hoạt một phương thức đăng nhập không cần mật khẩu bằng chính vân tay/khuôn mặt của mình,
    - **So that** tôi có thể chuẩn bị cho việc đăng nhập nhanh chóng và an toàn trong những lần sau.

- Story #2: Đăng nhập bằng phương thức mới

    - **As a** một user đã kích hoạt phương thức đăng nhập không mật khẩu,
    - **I want to** có thể vào MoMo chỉ bằng một lần quét vân tay/khuôn mặt,
    - **So that**tôi có thể truy cập tài khoản của mình ngay lập tức mà không cần nhập liệu.

- Story #3: Tắt phương thức đăng nhập

    - **As a** một user đã kích hoạt phương thức đăng nhập không mật khẩu,
    - **I want to** có thể tắt nó trong trường hợp tôi không muốn dùng đến nó nữa,
    - **So that** tôi có thể quản lý được thiết bị nào có thể truy cập vào tài khoản MoMo của tôi.


## 3. Solution Space
### 3.1
### 3.2. Requirements
### 3.3. Design
### 3.4. Detail specification - App Core Service
### 3.5. Detail specification - CoreX
CoreX phụ trách triển khai 2 phần trong dự án:
- PasskeyManager
- Bottom sheet nhập Complex Password để xác thực user 
#### 3.5.1. PasskeyManager
- **Card:** AC-3162
- **Mô tả:** App cần một lớp `PasskeyManager` thực hiện tất cả các công việc liên quan đến Passkey như: Tạo Passkey, Xóa Passkey, Đăng nhập bằng Passkey,... .
Lý do vì Passkey sẽ được gọi ở nhiều màn hình khác nhau nên việc tạo ra lớp `PasskeyManager` giúp dễ bảo trì và nâng cấp, dễ dàng kiểm thử, giảm thiểu việc lặp lại code.

- **Ngữ cảnh dùng PasskeyManager này:**

    - Tạo/Xóa Passkey: User bấm Toggle ở màn Tùy chỉnh tài khoản nhằm mục đích Bật / Tắt Đăng nhập bằng Passkey. Lúc này ViewModel ở màn Tùy chỉnh tài khoản sẽ gọi các phương thức của `PasskeyManager` nhằm mục đích Tạo / Xóa Passkey.
    - Đăng nhập: User bấm "Tiếp tục với Passkey" ở màn Nhập số điện thoại. ViewModel ở màn Màn Nhập số điện thoại gọi đến phương thức của `PasskeyManager` để thực hiện quá trình Đăng nhập bằng Passkey.
    - Mời tạo Passkey: Trường hợp user chưa có Passkey và vừa đăng nhập thành công bằng PIN / Complex Password và vào đến màn hình Home, thông báo sẽ xuất hiện gợi ý user "Bật đăng nhập bằng Passkey". Nếu user bấm "Đồng ý" thì ViewModel gọi đến phương thức Tạo mới Passkey `PasskeyManager`.

- **PasskeyManager có các phương thức:**
    - Kiểm tra Khả năng sử dụng Passkey của thiết bị
    - Kiểm tra Tài khoản đã có Passkey chưa
    - Tạo mới Passkey
    - Đăng nhập bằng Passkey
    - Xóa Passkey


##### 3.5.1.1. Kiểm tra Khả năng sử dụng Passkey của thiết bị
- **Mô tả:** Giao tiếp với Backend để kiểm tra xem thiết bị có đủ điều kiện sử dụng Passkey không.
- **Ngữ cảnh sử dụng:** ViewModel ở màn Tùy chỉnh tài khoản 
- **Logic:**
    - Gọi API của OS để kiểm tra điều kiện
      - Bộ điều kiện (chỉ kiểm tra 1 điều kiện phiên bản OS):
          - **Phiên bản OS:** Android 9+ hoặc iOS 16+
              > *Lý do chính của việc loại bỏ yêu cầu kiểm tra Sinh trắc học của thiết bị trong bộ điều kiện này là để tăng số lượng user có thể tiếp cận tính năng đăng nhập Passkey. OS hiện tại không chỉ cho phép tạo và xác thực Passkey bằng vân tay hay khuôn mặt, mà còn hỗ trợ các phương thức mở khóa màn hình khác như mã PIN, hình vẽ (pattern), và mật khẩu của thiết bị. Việc gỡ bỏ giới hạn này đảm bảo rằng những user không có thiết bị hỗ trợ sinh trắc học vẫn có thể sử dụng Passkey, từ đó tăng độ phủ và tính tiện dụng của tính năng.*
    - **Return kết quả:** 
        - Thiết bị hỗ trợ.
        - Thiết bị không hỗ trợ.

- **Acceptance criteria:**
    - **AC-3162-AC1: Thiết bị hỗ trợ**
        - **Given** một thiết bị có phiên bản OS và phần cứng tương thích với việc tạo và sử dụng Passkey (iOS 16+, Android 9+).
        - **When** `PasskeyManager` thực hiện chức năng kiểm tra khả năng tương thích.
        - **Then** trả về mã kết quả là "**Thiết bị hỗ trợ**".

    - **AC-3162-AC2: Thiết bị không hỗ trợ**
        - **Given** một thiết bị có phiên bản OS không thỏa bộ điều kiện (ví dụ: iOS 15, Android 8).
        - **When** `PasskeyManager` thực hiện chức năng kiểm tra khả năng tương thích.
        - **Then** trả về kết quả là "**Thiết bị không hỗ trợ**".
  
##### 3.5.1.2. Kiểm tra Tài khoản đã có Passkey chưa
- **Mô tả:** Giao tiếp với Backend để kiểm tra xem tài khoản của user có Passkey nào không.
- **Ngữ cảnh sử dụng:** ViewModel ở màn Tùy chỉnh tài khoản kiểm tra tài khoản đã có Passkey hay không để quyết định Bật / Tắt Toggle Passkey.
- **Logic:**
    - Yêu cầu token của user đang đăng nhập.
    - Gọi đến endpoint [**GET_PASSKEY_MSG**](https://atlassiantool.mservice.com.vn:9443/display/BS/Passkey+V2#PasskeyV2-3.4.1.Getpasskey-GET_PASSKEY_MSG) của Backend, phương thức `GET`.
    - Xử lý kết quả trả về từ Backend:
        - Kết quả trả về là một danh sách chứa các Passkey Credential Passkey gắn với tài khoản đó.
          - Nếu danh sách `!= rỗng`: Tài khoản đang có Passkey.
          - Nếu danh sách `== rỗng`: Tài khoản chưa có Passkey.
    - **Return kết quả:**
        - Tài khoản Có Passkey.
        - Tài khoản không có Passkey.

- **Acceptance criteria:**
    - **AC-3162-AC3: Kiểm tra, tài khoản có Passkey**
        - **Given** một user đã đăng nhập với token hợp lệ.
        - **And** tài khoản đó có ít nhất một Passkey đã được lưu trên Backend.
        - **When** `PasskeyManager` gửi yêu cầu đến Backend để kiểm tra.
        - **And** Backend trả về một danh sách Passkey `!= rỗng`.
        - **Then** `PasskeyManager` trả về kết quả là "**Có Passkey**".

    - **AC-3162-AC4: Kiểm tra, tài khoản không có Passkey**
        - **Given** một user đã đăng nhập với `accessToken` hợp lệ.
        - **And** tài khoản không có Passkey nào.
        - **When** `PasskeyManager` gửi yêu cầu đến Backend để kiểm tra.
        - **And** Backend trả về một danh sách Passkey (`== rỗng`).
        - **Then** `PasskeyManager` trả về kết quả là "**Không có Passkey**".

##### 3.5.1.3. Tạo mới Passkey
- **Mô tả:** Điều phối toàn bộ quá trình tạo mới một Passkey cho 1 tài khoản MoMo. Luồng này bao gồm việc yêu cầu một challenge từ Backend, Xác thực User bằng PIN/Password, Hiển thị giao diện tạo Passkey của OS (Android/iOS), và Gửi lại thông tin credential đã được tạo về cho Backend để lưu trữ.

- **Logic:**
    - **Init:** ViewModel (tại màn Tùy chỉnh tài khoản) gọi hàm Tạo Passkey từ lớp PasskeyManager
    - **Xác thực User:** Xác thực lại User bằng PIN / Password.
        - Nếu User đăng nhập vào MoMo bằng PIN thì xác thực lại bằng PIN.
        - Nếu User đăng nhập vào MoMo bằng Password thì xác thực lại bằng Password.
    - **Get challenge từ Backend:** Nếu xác thực thành công thì `PasskeyManager` gọi đến endpoint **[INIT_REGISTER_PASSKEY_MSG](https://atlassiantool.mservice.com.vn:9443/display/BS/Passkey+V2#PasskeyV2-3.1.1.InitRegisterPasskey-INIT_REGISTER_PASSKEY_MSG)** của Backend, `POST` method, để lấy challenge.
    - **Gọi API của OS**: `PasskeyManager` sử dụng `challenge` nhận được từ Backend để gọi API của OS
    - **[OS] OS Hiển thị UI tạo Passkey :** UI của OS hiện ra để User thao tác Tạo Passkey. 
    - **[User] User xác thực việc tạo Passkey:** User xác thực việc tạo Passkey trên UI của OS (bằng vân tay, khuôn mặt, mã PIN, hình vẽ)
    - **Xử lý kết quả từ OS:**
        - **Thành công:** OS trả về một đối tượng credential chứa public key của Passkey mới và các thông tin đã được ký bằng challenge từ Backend.
        - **User hủy:** User đóng giao diện của OS.
        - **Lỗi:** Có lỗi xảy ra từ phía OS.
    - **Gửi Credential về Backend:** Nếu user tạo `Thành công`, `PasskeyManager` sẽ gửi đối tượng credential này đến endpoint **[VERIFY_REGISTER_PASSKEY_MSG](https://atlassiantool.mservice.com.vn:9443/display/BS/Passkey+V2#PasskeyV2-3.1.2.VerifyRegisterPasskey-VERIFY_REGISTER_PASSKEY_MSG)** của Backend để đăng ký và lưu trữ.
    - **Xử lý response từ Backend:** `PasskeyManager` xử lý kết quả từ Backend để xác nhận việc tạo Passkey đã hoàn tất.
    - **Return kết quả:**
        - Tạo Passkey thành công
        - User hủy tạo Passkey
        - Lỗi lấy challenge từ server
        - Lỗi khi gửi credential mới về cho Backend

- **Acceptance criteria:**
  - **AC-3162-AC5: Tạo Passkey thành công**
      - **Given** một user đã đăng nhập với `token` hợp lệ
      - **And** thiết bị đủ điều kiện tạo Passkey.
      - **When** user bắt đầu luồng tạo mới Passkey.
      - **And** user xác thực thành công với PIN / Password
      - **And** `PasskeyManager` get và nhận được challenge thành công từ Backend.
      - **And** UI Tạo Passkey của OS được hiển thị và user xác thực thành công (Vân tay, Khuôn mặt, PIN, hình vẽ).
      - **And** `PasskeyManager` gửi thông tin credential mới về cho Backend và Backend xác nhận lưu trữ thành công.
      - **Then** `PasskeyManager` trả về kết quả **"Tạo Passkey thành công"**.

  - **AC-3162-AC6: User hủy tạo Passkey**
      - **Given** một user đã đăng nhập và luồng tạo Passkey đã bắt đầu.
      - **And** `PasskeyManager` đã hiển thị thành công giao diện tạo Passkey của OS.
      - **When** user chủ động đóng hoặc nhấn nút "Hủy" trên giao diện đó.
      - **Then** `PasskeyManager` trả về kết quả **"User hủy tạo Passkey"**.

  - **AC-3162-AC7: Lỗi khi lấy challenge từ Backend**
      - **Given** một user đã đăng nhập.
      - **When** `PasskeyManager` gửi yêu cầu đến Backend để lấy challenge cho việc tạo Passkey.
      - **And** Backend trả về một lỗi (ví dụ: `500 Internal Server Error`, `401 Unauthorized`).
      - **Then** `PasskeyManager` dừng luồng và trả về kết quả **"Lỗi lấy challenge từ server"**.
      - **And** không hiển thị giao diện tạo Passkey của OS.

  - **AC-3162-AC8: Lỗi khi gửi credential mới về cho Backend**
      - **Given** user đã xác thực thành công trên giao diện của OS.
      - **When** `PasskeyManager` gửi thông tin credential vừa được tạo về cho Backend để đăng ký.
      - **And** Backend trả về một lỗi (ví dụ: challenge không hợp lệ, credential đã tồn tại).
      - **Then** `PasskeyManager` trả về kết quả **"Lỗi khi gửi credential mới về cho Backend"**.

##### 3.5.1.4. Đăng nhập bằng Passkey
- **Mô tả:** Thực hiện quy trình đăng nhập vào tài khoản của user bằng Passkey. Luồng này được kích hoạt khi user bấm "Tiếp tục với Passkey" ở màn hình Nhập số điện thoại.

- **Logic:**
    - **Init:** ViewModel (tại màn Nhập số điện thoại) gọi hàm Đăng nhập bằng Passkey từ `PasskeyManager`.
    - **Get challenge từ Backend:** `PasskeyManager` gọi endpoint [**INIT_USER_PASSKEY_MSG**](https://atlassiantool.mservice.com.vn:9443/display/BS/Passkey+V2#PasskeyV2-3.2.1.Initlogin-INIT_USER_PASSKEY_MSG) của Backend, `POST` method, để lấy challenge.
    - **Gọi API của OS:** `PasskeyManager` sử dụng challenge nhận được để gọi API của OS.
    - **[OS] OS Hiển thị UI chọn Passkey:** OS hiển thị UI để User thao tác chọn Passkey dùng để đăng nhập. Có thể xảy ra các trường hợp:
        - Có 1 Passkey.
        - Có nhiều Passkey hiển thị dạng danh sách (1 căn cước có thể tạo tối đa 3 tài khoản MoMo, mỗi tài khoản có 1 Passkey).
        - Không có Passkey. Dùng mã QR (trên bản demo dùng thiết bị khác để quét QR passkey, sau khi quét sẽ không có gì xảy ra).
    - **[User] User xác thực việc đăng nhập với Passkey:** User xác thực đăng nhập với Passkey trên UI của OS (vân tay, khuôn mặt, mã PIN, hình vẽ).
    - Sau khi xác thực thành công, OS trả về đối tượng assertion (chứa challenge đã được ký) cho `PasskeyManager`.
    - **Gửi Credential về Backend:** `PasskeyManager` gọi endpoint [**VERIFY_USER_PASSKEY_MSG**](https://atlassiantool.mservice.com.vn:9443/display/BS/Passkey+V2#PasskeyV2-3.2.2.Verifylogin-VERIFY_USER_PASSKEY_MSG) của Backend để xác thực.
    - **[Backend] Backend kiểm tra:** Nếu hợp lệ, Backend tạo phiên đăng nhập mới và trả về thông tin session (accessToken, refreshToken).
    - **Xử lý response từ Backend:** `PasskeyManager` xử lý kết quả từ Backend.
    - **Return kết quả:**
        - Đăng nhập thành công: trả về accessToken và refreshToken.
        - Đăng nhập thất bại: do lỗi xác thực từ Backend hoặc lỗi hệ thống.
        - User hủy bỏ đăng nhập: quá trình đăng nhập trên giao diện của OS.

- **Acceptance criteria:**
    - **AC-3162-AC9: Đăng nhập bằng Passkey thành công**
        - **Given** một user có Passkey hợp lệ đã được lưu trên thiết bị hoặc tài khoản đám mây (iCloud Keychain, Google Password Manager).
        - **And** user bắt đầu luồng đăng nhập bằng Passkey.
        - **When** `PasskeyManager` nhận được challenge hợp lệ từ Backend.
        - **And** user chọn Passkey và xác thực thành công trên giao diện hệ thống.
        - **And** `PasskeyManager` gửi thông tin xác thực (assertion) tới Backend.
        - **And** Backend xác thực thành công và trả về thông tin phiên đăng nhập (session).
        - **Then** `PasskeyManager` trả về kết quả là "**Đăng nhập thành công**" cùng với accessToken và refreshToken.

    - **AC-3162-AC10: User hủy bỏ quá trình đăng nhập**
        - **Given** user bắt đầu luồng đăng nhập bằng Passkey.
        - **When** OS hiển thị giao diện yêu cầu chọn Passkey và xác thực.
        - **And** user bấm nút hủy hoặc thoát khỏi giao diện đó.
        - **Then** `PasskeyManager` nhận được tín hiệu hủy từ API OS và trả về kết quả là "**User hủy bỏ đăng nhập**".

    - **AC-3162-AC11: Đăng nhập thất bại do xác thực không thành công ở Backend**
        - **Given** user đã hoàn tất việc xác thực trên thiết bị.
        - **When** `PasskeyManager` gửi thông tin xác thực (assertion) tới Backend.
        - **And** Backend không thể xác thực được (ví dụ: chữ ký không hợp lệ, challenge sai).
        - **Then** `PasskeyManager` trả về kết quả là **Đăng nhập thất bại**.

##### 3.5.1.5. Xóa Passkey
- **Mô tả:** Điều phối toàn bộ quá trình xóa một Passkey đã được liên kết với tài khoản MoMo. Luồng này bao gồm việc xác thực lại User bằng PIN/Password và gửi yêu cầu xóa Passkey tương ứng về cho Backend.
- **Logic:**
    - ViewModel (tại màn Tùy chỉnh tài khoản) gọi hàm `Xóa Passkey` từ lớp `PasskeyManager`, truyền vào accessToken của Passkey cần xóa.
    - Nhận confirm trên UI Bottom sheet Xác nhận: Bottom sheet có 2 button "Xác nhận", "Hủy" để User thực hiện xác nhận hoặc hủy việc xóa Passkey.
        - Nếu User bấm "Xác nhận", tiếp tục luồng Xóa Passkey.
        - Nếu User bấm "Hủy", kết thúc luồng xóa Passkey và trả về kết quả **"User hủy xóa Passkey"**.
    - **Xác thực User:** Xác thực lại User bằng PIN / Password.
        - Nếu User đăng nhập vào MoMo bằng PIN thì xác thực lại bằng PIN.
        - Nếu User đăng nhập vào MoMo bằng Password thì xác thực lại bằng Password.
    - **Gửi yêu cầu xóa đến Backend:** Nếu xác thực thành công, `PasskeyManager` gọi đến endpoint [**DISABLE_PASSKEY_MSG**](https://atlassiantool.mservice.com.vn:9443/display/BS/Passkey+V2#PasskeyV2-3.3.1.Disablepasskey-DISABLE_PASSKEY_MSG) của Backend, `POST` method, để yêu cầu xóa Passkey với accessToken tương ứng.
    - **Xử lý response từ Backend:** `PasskeyManager` xử lý kết quả từ Backend để xác nhận việc xóa Passkey đã hoàn tất.
    - **Return kết quả:**
        - Xóa Passkey thành công.
        - User hủy (tại Bottom sheet confirm "Bạn muốn Tắt đăng nhập bằng Passkey" hoặc tại Bottom sheet nhập PIN/Password).
        - Lỗi khi gửi yêu cầu xóa về Backend.

* **Acceptance criteria:**
    * **AC-3163-AC12: Xóa Passkey thành công**
        - **Given** một user đã đăng nhập với `token` hợp lệ và có một Passkey đã được tạo.
        - **When** user bắt đầu luồng xóa Passkey.
        - **And** xác thực thành công với PIN / Password.
        - **And** `PasskeyManager` gửi yêu cầu xóa Passkey với accessToken hợp lệ đến Backend.
        - **And** Backend xác nhận xóa thành công.
        - **Then** `PasskeyManager` trả về kết quả **"Xóa Passkey thành công"**.

    * **AC-3163-AC13: User hủy thao tác xóa Passkey**
        - **Given** User đã đăng nhập và luồng xóa Passkey đã bắt đầu.
        - **When** User được yêu cầu xác thực bằng PIN / Password và User chủ động đóng hoặc nhấn nút "Hủy".
        - **Then** `PasskeyManager` trả về kết quả **"User hủy xóa Passkey"**.

    * **AC-3163-AC14: Lỗi khi gửi yêu cầu xóa đến Backend**
        - **Given** User đã xác thực thành công.
        - **When** `PasskeyManager` gửi yêu cầu đến Backend để xóa Passkey.
        - **And** Backend trả về một lỗi (ví dụ: `500 Internal Server Error`, `404 Not Found`).
        - **Then** `PasskeyManager` dừng luồng và trả về kết quả **"Lỗi khi gửi yêu cầu xóa Passkey đến Backend"**.

#### 3.5.2. Bottom sheet nhập Complex Password
- **Card:**
- **Figma để lấy design properties:** https://www.figma.com/design/OMxlNPkqhO4O0AKxDNp7od/Growth-Authentication?node-id=28922-57730&t=XOjAIlo7yn88ePPv-4
- **FigJam để xem flow tổng thể của Passkey:** https://www.figma.com/board/VJfczOKKTRnkRv5d2ityBe/-Passkey--Screen-flow?node-id=141-235&t=ro53elltt31FupdH-4
- **Tóm tắt:** Bottom sheet nhập Complex Password (sau đây sẽ gọi tắt là Password) sẽ reuse lại UI và Logic của Bottom sheet nhập PIN. Tuy nhiên sẽ có 2 điểm thay đổi:
    - Thay đổi text field thành text field nhập Password. Trong text field có 2 điểm sẽ cần customize:
        - Tắt badge name
        - Sử dụng fontWeight: bold
    - Thêm Icon Button vào Bottom sheet để khi User nhập xong Password sẽ nhấn vào Icon Button để thực hiện việc đăng nhập.
- **Mô tả:** App cần một cơ chế xác thực User trước khi cho phép thực hiện thao tác Tạo Passkey. Đây là cơ chế áp dụng cho trường hợp User đăng nhập bằng Password . Cơ chế này ưu tiên sử dụng Sinh trắc học (Biometrics) của thiết bị và sử dụng việc nhập bằng tay Password làm phương án thay thế.
- **Ngữ cảnh sử dụng:** Toggle ở màn "Tùy chỉnh tài khoản" đang ở trạng thái Off. User nhấn vào Toggle nhằm mục đích Bật đăng nhập bằng Passkey (hệ thống bên dưới sẽ thực hiện tạo mới Passkey). Lúc này cần có cơ chế xác thực User.
- **Logic:**
    - **Kiểm tra điều kiện:**
        - Thiết bị có hỗ trợ Biometrics (FaceID, Vân tay).
        - User đã bật tính năng xác thực bằng Sinh trắc học.
    - **Phân luồng:**
        - Nếu User bật Biometrics: Hiển thị giao diện xác thực Biometrics của OS (Quét khuôn mặt, Quét vân tay) với trạng thái overlay trên Bottom sheet nhập Password.
        - Nếu User không bật Biometrics: Hiển thị Bottom sheet và bàn phím ảo để nhập Password.
    - **Fallback cho Biometrics:** hỗ trợ fallback là Bottom sheet để user nhập Complex Password trong trường hợp Gặp lỗi với Biometrics hoặc User chủ động rời việc xác thực với Biometrics, ví dụ như các trường hợp sau: 
        - Bấm Cancel trên UI của Biometrics.
        - Bấm nút Back điều hướng của OS.
        - Vượt quá số lần lỗi khi xác thực với Biometrics.
    - **Xử lý sai mật khẩu:**
        - Lần 1: Hiển thị "Mật khẩu không chính xác, bạn còn 2 lần thử".
        - Lần 2: Hiển thị "Mật khẩu không chính xác, bạn còn 1 lần thử".
        - Lần 3: Hiển thị pop-up "Bạn đã nhập sai mật khẩu 3 lần. Vì lý do bảo mật hệ thống sẽ tự động đăng xuất" và thực hiện đăng xuất.
    - **Return kết quả:**
        - Xác thực thành công: Trả về kết quả `SUCCESS`.
        - Thất bại (nhập sai 3 lần): Trả về kết quả `FAILURE_MAX_ATTEMPTS` và đăng xuất user.
        - User hủy: Trả về kết quả `USER_CANCELLED`.
- **Acceptance criteria:**  
    ***Luồng xác thực thành công***
    - **AC-3163-AC1: Xác thực thành công bằng Sinh trắc học (Biometrics) - Happy path**
        - **Given** một user đã đăng nhập bằng Password.
        - **And** thiết bị của user có hỗ trợ Biometrics (Khuôn mặt / Vân tay).
        - **And** user đã bật toggle "Dùng để thay thế mã PIN xác thực" trong màn "Tùy chỉnh tài khoản".
        - **When** user nhấn vào toggle để bật đăng nhập bằng Passkey ở màn "Tùy chỉnh tài khoản".
        - **Then** hệ thống hiển thị UI Biometrics (Quét khuôn mặt / Vân tay) để user thao tác.
        - **And** user xác thực thành công qua giao diện Biometrics của OS.
        - **Then** giao diện xác thực của OS đóng lại.
        - **And** cơ chế xác thực trả về kết quả "**Xác thực thành công**".

    - **AC-3163-AC2: Xác thực thành công bằng Password (Do không bật Biometrics)**
        - **Given** một user đã đăng nhập bằng Password.
        - **And** user chưa bật toggle "Dùng để thay thế mã PIN xác thực" (kể cả khi thiết bị có hỗ trợ Biometrics).
        - **When** user nhấn vào Toggle nhằm mục đích Bật đăng nhập bằng Passkey.
        - **Then** hệ thống hiển thị Bottom sheet yêu cầu nhập Password.
        - **When** user nhập đúng Password và nhấn xác nhận.
        - **Then** Bottom sheet đóng lại.
        - **And** cơ chế xác thực trả về kết quả "**Xác thực thành công**".

    - **AC-3163-AC3: Xác thực thành công bằng Password (Sau khi hủy Biometrics)**
        - **Given** user được yêu cầu xác thực bằng Biometrics.
        - **When** user chủ động hủy giao diện Biometrics (Nhấn "Cancel"; Nhất nút Back của OS; hoặc Xác thực bằng Biometrics thất bại quá số lần cho phép).
        - **Then** hệ thống hiển thị Bottom sheet nhập Password.
        - **When** user nhập đúng Password và nhấn xác nhận.
        - **Then** Bottom sheet đóng lại.
        - **And** cơ chế xác thực trả về kết quả "**Xác thực thành công**".
    
    - **AC-3163-AC4: Xác thực thành công bằng Password (Thiết bị không có Biometrics)**
        - **Given** một user đã đăng nhập bằng Password.
        - **And** thiết bị của user không hỗ trợ Biometrics (không có FaceID / Vân tay).
        - **When** user nhấn vào Toggle nhằm mục đích Bật đăng nhập bằng Passkey.
        - **Then** hệ thống hiển thị Bottom sheet yêu cầu nhập Password.
        - **When** user nhập đúng Password và nhấn xác nhận.
        - **Then** Bottom sheet đóng lại.
        - **And** cơ chế xác thực trả về kết quả **"Xác thực thành công"**.
 

### 3.6. Detail specification - AppX
#### 3.6.1. Thêm Element chứa Toggle để người dùng "Bật / Tắt đăng nhập bằng Passkey"
- **Card:**
- **Figma để lấy design properties:** https://www.figma.com/design/OMxlNPkqhO4O0AKxDNp7od/Growth-Authentication?node-id=28922-50873&t=GdHrKvJEeh6MIiVe-4
- **FigJam để xem flow tổng thể của Passkey:** https://www.figma.com/board/VJfczOKKTRnkRv5d2ityBe/-Passkey--Screen-flow?node-id=141-235&t=ro53elltt31FupdH-4
- **Mô tả**: Cần có cơ chế giúp User có thể:
  - Bật đăng nhập bằng Passkey (luồng bên dưới Tạo mới Passkey), 
  - Tắt đăng nhập bằng Passkey (Luồng bên dưới Xóa Passkey)
  - Tìm hiểu thêm thông tin từ "Tìm hiểu thêm".
- AppX sẽ dùng các phương thức từ PasskeyManager (do CoreX phụ trách):
  - Kiểm tra Khả năng sử dụng Passkey của thiết bị
  - Kiểm tra Tài khoản đã có Passkey chưa
  - Tạo mới Passkey
  - Xóa Passkey

##### 3.6.1.1. Element chứa Toggle để người dùng "Bật / Tắt đăng nhập bằng Passkey"



### 3.7 Detail specification - Backend
#### 3.7.1. Cơ chế Xóa Passkey

- **Card:** Sub-task [SCA-546](https://atlassiansuite.mservice.com.vn:8443/browse/SCA-546)  
- **Mô tả:** Backend cần cung cấp cơ chế xóa vĩnh viễn tất cả các Passkey credential đã được liên kết với tài khoản của người dùng.  
- **Ngữ cảnh sử dụng:** Toggle đang trạng thái On. User nhấn vào Toggle nhằm mục đích Tắt đăng nhập bằng Passkey. Bottom sheet confirm hiện ra. Sau khi User nhấn confirm trên bottom sheet, App sẽ request đến Backend để xóa các Passkey credential gắn với tài khoản đó.  

- **Yêu cầu phía Backend:**
    - Xây dựng một (01) API endpoint để xử lý yêu cầu Xóa Passkey.
    - **Method:** `POST`
    - **Endpoint:** do Backend quy định
    - **Logic:** Endpoint này xác thực người dùng hợp lệ dựa trên `accessToken` và xóa tất cả các Passkey credential tương ứng với người dùng đó.
        - **Xác thực người dùng:** Xác thực người dùng hợp lệ dựa trên `accessToken` được gửi trong header của request.
        - **Xóa record:** Xóa tất cả các Passkey credential record trong CSDL có liên quan đến người dùng này.
        - **Ghi log (optional):** Ghi log hành động Xóa Passkey để phục vụ cho việc kiểm soát sau này.
        - **Phản hồi thành công:**
            - Xóa thành công, hoặc
            - Xóa nhưng không có record nào để xóa.

- **Acceptance criteria**
    - **SCA-546-AC1:** Xóa thành công tất cả các passkey của người dùng có `accessToken` hợp lệ
        - Given một người dùng đã đăng nhập thành công bằng `accessToken` hợp lệ  
        - And người dùng đó có ít nhất một Passkey đã được lưu trong hệ thống  
        - When ứng dụng gửi một yêu cầu `POST` đến endpoint  
        - Then tất cả các Passkey credential record của người dùng đó phải bị xóa vĩnh viễn khỏi cơ sở dữ liệu.
    - **SCA-546-AC2:** Trường hợp người dùng có `accessToken` hợp lệ nhưng không có Passkey nào
        - Given một người dùng đã đăng nhập thành công bằng `accessToken` hợp lệ  
        - And người dùng không có Passkey nào  
        - When ứng dụng gửi một yêu cầu `POST` đến endpoint  
        - Then hệ thống đảm bảo không có thay đổi nào trong cơ sở dữ liệu.

#### 3.7.2. Cơ chế Lấy Danh sách Passkey

- **Card:** Subtask [SCA-548](https://atlassiansuite.mservice.com.vn:8443/browse/SCA-548)  
- **Mô tả:** Backend cần cung cấp cơ chế để truy vấn và trả về danh sách tất cả các Passkey credential đã được liên kết với tài khoản của người dùng.  

- **Ngữ cảnh sử dụng:**
    - Ngữ cảnh #1: User nhấn vào màn "Tùy chỉnh tài khoản". App request đến Backend để lấy về list of Passkeys nhằm mục đích kiểm tra tài khoản MoMo này có Passkey hay chưa:
        - Nếu list of Passkey != null, Toggle chuyển sang trạng thái On;
        - Nếu list of Passkey == null, Toggle giữ trạng thái Off.
    - Ngữ cảnh #2: Toggle đang ở trạng thái On. User nhấn vào Toggle nhằm mục đích Tắt đăng nhập bằng Passkey. App request đến Backend để lấy về danh sách Passkey nhằm mục đích hiển thị trên UI Bottom sheet confirm trước khi xóa.

- **Yêu cầu phía Backend:**
    - Xây dựng một (01) API endpoint để xử lý yêu cầu Lấy danh sách Passkey
    - **Method:** `GET`
    - **Endpoint:** do Backend quy định
    - **Logic:** Endpoint này phải xác thực người dùng hợp lệ dựa trên `accessToken` và truy vấn cơ sở dữ liệu để lấy tất cả các Passkey credential tương ứng với người dùng đó:
        - **Xác thực người dùng:** Xác thực người dùng hợp lệ dựa trên `accessToken` được gửi trong header của request.
        - **Truy vấn Cơ sở dữ liệu:** Nếu `accessToken` hợp lệ, thực hiện truy vấn cơ sở dữ liệu để lấy tất cả các Passkey credential record tương ứng.
        - **Ghi log (Optional):** Ghi log hành động Truy vấn danh sách Passkey để phục vụ cho việc kiểm soát sau này.
        - **Phản hồi thành công:** Nếu truy vấn thành công, trả về danh sách:
            - Nếu người dùng có Passkey, danh sách này sẽ chứa các object Passkey. Mỗi object chứa các thông tin như timestamp tạo passkey.
            - Nếu người không có Passkey nào, danh sách này rỗng ([]).

- **Acceptance criteria**
    - **SCA-548-AC1:** Lấy thành công danh sách Passkey của một người dùng đã đăng ký Passkey
        - Given một người dùng đã đăng nhập thành công bằng `accessToken` hợp lệ  
        - And người dùng đó có ít nhất một Passkey đã được lưu trong cơ sở dữ liệu  
        - When ứng dụng gửi một yêu cầu `GET` đến endpoint lấy danh sách Passkey  
        - Then trả về danh sách các object Passkey không rỗng.
    - **SCA-548-AC2:** Lấy thành công danh sách rỗng ([]) khi người dùng chưa đăng ký Passkey nào
        - Given một người dùng đã đăng nhập thành công bằng `accessToken` hợp lệ  
        - And người dùng đó không có bất kỳ Passkey nào được lưu trong cơ sở dữ liệu  
        - When ứng dụng gửi một yêu cầu `GET` đến endpoint lấy danh sách Passkey  
        - Then trả về danh sách rỗng ([]).



## 4. Data tracking
| Trigger | Event name | Param | Param value |
| ------- | ---------- | ----- | ----------- |
|         |            |       |             |

- Số lượng Bấm vào Toggle để tạo Passkey 
- Số lượng Tạo Passkey thành công 

- Số lượng chọn Passkey là phương thức đăng nhập
- Số lượng đăng nhập thành công khi chọn Passkey là phương thức đăng nhập


## 5. Tài liệu tham khảo
- https://developer.android.com/design/ui/mobile/guides/patterns/passkeys
- https://medium.com/androiddevelopers/bringing-seamless-authentication-to-your-apps-using-credential-manager-api-b3f0d09e0093
- https://www.passkeycentral.org
- https://vincss.net/vi/bao-cao-nguoi-dung-viet-nam-cam-thay-the-nao-khi-xac-thuc-tren-cac-ung-dung-ngan-hang
- https://passkeys.dev
- https://github.com/line/line-fido2-server