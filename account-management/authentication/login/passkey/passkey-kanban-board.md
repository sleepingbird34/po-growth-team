# Passkey kanban board

## Mini-tasks

### [PO] Hỏi Miên về việc siết điều kiện tạo Passkey

  - due: 2025-10-13
  - tags: [Backend, CoreX]
  - defaultExpanded: false

### [PO][AC-3163] Bổ sung Acceptance criteria cho Bottom sheet trong PRD

  - due: 2025-10-13
  - tags: [CoreX]
  - defaultExpanded: false

### [PO] Link các card của Passkey đến Epic

  - due: 2025-10-15
  - tags: [PO]
  - priority: medium
  - defaultExpanded: false
    ```md
    Epic link: https://atlassiansuite.mservice.com.vn:8443/browse/AC-2796
    ```

### [PO][ACS-3368] Bổ sung English cho card

  - due: 2025-10-14
  - tags: [ACS]
  - defaultExpanded: false

### [PO][AC-3162] Bổ sung thêm section Xóa Passkey trong PRD chỗ CoreX

  - due: 2025-10-12
  - tags: [CoreX]
  - defaultExpanded: false

### [PO] Vẽ Sequence diagram

  - due: 2025-10-15
  - tags: [PO]
  - priority: medium
  - workload: Hard
  - defaultExpanded: false
  - steps:
      - [ ] Sequence diagram Tạo Passkey
      - [ ] Sequence diagram Xóa Passkey
      - [ ] Sequence diagram Đăng nhập bằng Passkey

### [PO][AC-3162] Bổ sung thêm thông tin về việc xác thực bằng Bottom sheet sau khi confirm Xóa Passkey

  - due: 2025-10-11
  - tags: [CoreX]
  - defaultExpanded: false
  - steps:
      - [ ] Viết trong PRD
      - [ ] Nhắn trong group, tag huan.do

### [PO][ACS-3368] Bổ sung Table of content for Dev

  - defaultExpanded: false

## To Do

### [ACS-3368] Thêm button ở màn Nhập số điện thoại

  - due: 2025-10-22
  - tags: [ACS, UX]
  - priority: high
  - defaultExpanded: false
  - steps:
      - [x] [PO] Tạo Card
      - [ ] Bổ sung ngôn ngữ English
      - [ ] [PO] Nghiệm thu
    ```md
    Card: https://atlassiansuite.mservice.com.vn:8443/browse/ACS-3368
    ```

### [AX-3837] Thêm element ở màn Tùy chỉnh tài khoản

  - due: 2025-10-25
  - tags: [AppX, UX]
  - priority: high
  - defaultExpanded: false
    ```md
    Card: https://atlassiansuite.mservice.com.vn:8443/browse/AX-3837
    ```

### [SCA-XXX] Kiểm tra sự tồn tại của Passkey trước khi cho phép tạo Passkey

  - due: 2025-10-24
  - tags: [Backend]
  - priority: high
  - defaultExpanded: false
  - steps:
      - [ ] [PO] Hỏi Miên trong group "[PROTECH] Passkey" về việc siết điều kiện tạo Passkey
      - [ ] [PO] Tạo card BE về việc siết điều kiện
      - [ ] Nghiệm thu
    ```md
    - Theo như anh Minh dẫn lại lời anh Hùng Huỳnh thì "mỗi tài khoản MoMo chỉ có 1 Passkey". Chỉ có thể quy định được "Một tài khoản MoMo nếu có một Passkey đang hoạt động thì không thể tạo thêm Passkey mới". Bởi vì có thể xảy ra việc sync Passkey giữa các điện thoại trên cùng 1 tài khoản Google / Apple. 
    - Hiện tại điều kiện trên chỉ siết ở Client trên UI mới dạng Toggle, chưa siết ở Backend, dẫn đến trên bản UAT, mỗi lần đăng nhập thành công sẽ có thêm một Passkey được tạo. 
    - Siết điều kiện lại ở BE: 
    - Mỗi lần có request tạo mới Passkey từ Client, Backend vào check Database
    - Nếu tài khoản MoMo đang có 1 Passkey tồn tại, sẽ không cho tạo mới Passkey
    - Và return lỗi về cho Client
    ```

### Viết FAQ cho CS

  - defaultExpanded: false

### [SCA-XXX] Mask thông tin cá nhân của người dùng

  - due: 2025-10-24
  - tags: [Backend]
  - priority: high
  - defaultExpanded: false
  - steps:
      - [ ] [PO] Tạo card cho Backend
      - [ ] [PO] Thông báo vào group chat, tag huan.do, minh.nguyen3
    ```md
    Theo Risk thì cần phải mask thông tin cá nhân của người dùng trước khi tạo Passkey với Authenticator
    ```

### [AC-3163] Bottom sheet Password

  - due: 2025-10-17
  - tags: [CoreX, UX]
  - priority: high
  - defaultExpanded: false
  - steps:
      - [x] [PO] Hỏi CoreX về tính khả thi khi reuse lại UI và Logic của Bottom sheet nhập PIN
      - [x] [PO] Tạo Card CoreX
      - [x] [PO] Tạo Card UX
      - [ ] [PO] Bổ sung thêm Acceptance Criteria cho Bottom sheet trong PRD
      - [ ] Nghiệm thu
    ```md
    - PRD: https://atlassiantool.mservice.com.vn:9443/pages/viewpage.action?pageId=198318712
    - Card CoreX: https://atlassiansuite.mservice.com.vn:8443/browse/AC-3163
    - Card UX: https://atlassiansuite.mservice.com.vn:8443/browse/PDFOUN-980
    - Chat: https://chat.google.com/room/AAQAbU4AVvY/YeTwbm-xi6Y/YeTwbm-xi6Y?cls=10
    ```

### [AC-3164] QC CoreX test card ACS-3368

  - due: 2025-10-22
  - tags: [CoreX]
  - priority: high
  - defaultExpanded: false

### Thêm bottom sheet confirm việc Xóa Passkey

  - defaultExpanded: false
    ```md
    https://atlassiansuite.mservice.com.vn:8443/browse/AX-3967
    ```

### [PDFOUN-980] Bottom sheet nhập Password

  - due: 2025-10-13
  - tags: [UX]
  - defaultExpanded: false

### [SCA-XXX] Thêm tính năng gửi email

  - defaultExpanded: false
    ```md
    Gửi email cho users khi 
    - Tạo passkey
    - Xóa passkey
    ```

### Bổ sung use case diagram, activity diagram, sequence diagram

  - defaultExpanded: false

## In progress

### [AC-3162] PasskeyManager

  - due: 2025-10-20
  - tags: [CoreX, Backend]
  - priority: high
  - defaultExpanded: false
  - steps:
      - [ ] [PO] Bổ sung thêm Xóa Passkey trong PRD
      - [ ] [PO] Bổ sung thêm thông tin về việc xác thực bằng Bottom sheet sau khi confirm Xóa
      - [ ] [PO] Nghiệm thu
    ```md
    Card: https://atlassiansuite.mservice.com.vn:8443/browse/AC-3162
    ```

### [PDFOUN] Bottom sheet nhập Password để xác thực

  - due: 2025-10-13
  - tags: [UX]
  - priority: high
  - defaultExpanded: false
  - steps:
      - [x] [PO] Tạo card
    ```md
    Card: https://atlassiansuite.mservice.com.vn:8443/browse/PDFOUN-980
    ```

### PRD

  - due: 2025-10-13
  - tags: [PO]
  - priority: high
  - workload: Normal
  - defaultExpanded: true
  - steps:
      - [x] [PO] Sequence diagram
      - [ ] [PO] Cập nhật lại hình sơ đồ
      - [ ] [PO] Sửa lại Table of Content

### Security review

  - due: 2025-10-30
  - tags: [Security]
  - defaultExpanded: false
  - steps:
      - [ ] [PO] Vẽ sequence diagram
      - [ ] [PO] Thêm sequence diagram vào PRD
      - [ ] [Security] Thực hiện review trên source code
      - [ ] [Security] Review trên hạ tầng
    ```md
    Thread email: https://mail.google.com/mail/u/0/#search/passkey/KtbxLwhCFZbpVPFjqfttbWNspwLJbzxjqB
    ```

### Legal review

  - due: 2025-10-17
  - tags: [Legal]
  - defaultExpanded: false
  - steps:
      - [ ] [PO] Phản hổi email chị Lan Anh về việc Passkey chính là hình thức xác thực FIDO
      - [ ] [PO] Bổ sung section cho Legal trong PRD

### Risk review

  - due: 2025-10-13
  - tags: [Risk]
  - defaultExpanded: false
  - steps:
      - [ ] [PO] Bổ sung section cho Risk trong PRD

## Review

## Done

### [SCA-546] Cơ chế Xóa Passkey

  - tags: [Backend]
  - defaultExpanded: false
  - steps:
      - [x] [PO] Tạo Card
      - [x] [PO] Nghiệm thu
    ```md
    Card: https://atlassiansuite.mservice.com.vn:8443/browse/SCA-546
    Email nghiệm thu: https://mail.google.com/mail/u/0/#inbox/FMfcgzQcpwwLnDtvPmNQhvqQWZBxkXNv
    ```

### [SCA-548] Get list of Passkeys

  - tags: [Backend]
  - defaultExpanded: false
  - steps:
      - [x] [PO] Tạo card
      - [x] [PO] Nghiệm thu
    ```md
    - Card Backend: https://atlassiansuite.mservice.com.vn:8443/browse/SCA-548
    - Email nghiệm thu: https://mail.google.com/mail/u/0/#inbox/FMfcgzQcpwssQBNGTMChPfhrHvbqbklh
    ```

### [PDFOUN-971] Màn Enter phone

  - tags: [UX]
  - defaultExpanded: false
    ```md
    Card: https://atlassiansuite.mservice.com.vn:8443/browse/PDFOUN-971
    ```

### [PDFOUN-959] Màn Tùy chỉnh tài khoản

  - tags: [UX]
  - defaultExpanded: false
    ```md
    Card: https://atlassiansuite.mservice.com.vn:8443/browse/PDFOUN-959
    ```

### [PO] Hỏi Miên trong group về việc mask thông tin

  - due: 2025-10-13
  - tags: [Backend, CoreX]
  - defaultExpanded: false
    ```md
    Đã hỏi trong meeting ngày Oct 14, 2025
    https://atlassiantool.mservice.com.vn:9443/display/PGT/Meeting+notes+Oct+14%2C+2025
    ```

