# PPOS v2.37 — Vá lỗi kiểm kho đã chốt, mở Kiểm kho & Phiếu nhập trên điện thoại cho tài khoản Chủ, đồng bộ ô tìm hàng

Bản này gồm ba việc: **khóa chặt đợt kiểm kho đã chốt** để hồ sơ không lệch, **mở Kiểm kho và Phiếu nhập trên điện thoại cho tài khoản Chủ**, và **đồng bộ toàn bộ ô tìm hàng/tìm nhà cung cấp thành một kiểu danh sách gọn, hết treo khi gõ**. Nghiệp vụ bán hàng, chốt phiếu, tính tiền, trừ kho và công nợ giữ nguyên cơ chế như trước; phía phát triển đã kiểm chứng bằng bộ ca tự động (Đợt 128: 26/26, Đợt 129: 48/48, bộ đối chiếu số liệu Đợt 125: 72/72 khớp tuyệt đối).

## Đợt kiểm kho đã chốt được khóa chặt

- Trước đây, mở lại một đợt kiểm **đã chốt** vẫn sửa được số đếm trên màn hình chi tiết — số đã sửa được lưu vào hồ sơ đợt kiểm trong khi số tồn kho giữ nguyên theo lúc chốt, làm hồ sơ lệch lặng lẽ. Nay ô đếm ở đợt đã chốt bị **khóa cứng hai lớp**: chỉ xem, không gõ sửa được; thanh chọn hàng loạt cũng không còn ở đợt đã chốt.
- Tiêu đề và thẻ thông tin của đợt đã chốt hiện đúng **"Đã chốt"** kèm thời gian chốt, ngày giờ kiểm và người kiểm (trước đây luôn ghi "đang kiểm" kể cả đợt đã chốt xong).

## Tài khoản Chủ làm Kiểm kho & Phiếu nhập ngay trên điện thoại

- Trên điện thoại, tài khoản **Chủ** nay mở được **Kiểm kho** và **Phiếu nhập hàng**: vào mục **Thêm** có thẻ **"Quản lý kho (chỉ Chủ)"**. Tra cứu phiếu tạm và "Tiếp tục nhập" phiếu nhập dở ngay trên điện thoại cũng được.
- Tài khoản **nhân viên giữ nguyên tuyệt đối**: điện thoại của nhân viên chỉ để bán hàng, kể cả khi nhân viên được cấp quyền kho (quyền đó chỉ có tác dụng trên máy tính quầy). Phiếu trả nhà cung cấp vẫn làm trên máy tính như trước.

## Ô tìm–chọn đồng bộ một kiểu, hết treo

- Cả 5 ô tìm (tìm hàng ở màn Bán hàng, tìm hàng + tìm nhà cung cấp ở phiếu nhập, tìm nhà cung cấp ở phiếu trả, tìm hàng ở kiểm kho) nay dùng **chung một kiểu trình bày**: gõ là sổ xuống một **danh sách dạng hàng ngang** ngay dưới ô tìm — tên đậm, dòng phụ mã hàng/tồn kho/giá (hoặc số điện thoại với nhà cung cấp) — bấm cả hàng là chọn, hiện **tối đa 15 kết quả** kèm dòng nhắc thu hẹp khi còn nhiều. Trước đây mỗi màn một kiểu: ở kiểm kho kết quả hiện thành dải nút thô, ở phiếu nhập danh sách kéo dài đẩy cả trang, và kết quả tìm nhà cung cấp có lúc bị thanh menu dính che mất, bấm không trúng.
- **Sửa lỗi ô tìm có lúc bị treo, gõ không vào chữ** trên danh sách hàng dài (gốc lỗi lớn nhất ở màn Bán hàng: mỗi phím gõ trước đây vẽ lại toàn màn). Nay gõ phím nào chỉ cập nhật danh sách kết quả, chữ không mất, trỏ không nhảy; đo trên 1.724 mặt hàng, từ phím cuối tới lúc danh sách hiện chỉ khoảng 0,12 giây.
- Màn **Bán hàng**: ô tìm ở chế độ Bán nhanh sổ danh sách như các màn khác; nút **Chọn hàng** dạng lưới thẻ **giữ nguyên tuyệt đối** cho người dùng cảm ứng chọn tay, gõ tìm trong lưới vẫn lọc lưới như hiện tại.

## Cột phải phiếu nhập hàng gọn hơn

- Bỏ đoạn chữ hướng dẫn dài thừa ở cuối cột (đoạn này còn là gốc lỗi làm chữ bị **bóp thành cột hẹp, xuống dòng từng chữ một** trên màn hình quầy thật). Nút **Quay lại danh sách** nay nằm một dòng riêng, bề ngang đầy đủ. Các ô tiền và hai nút Lưu tạm / Nhập hàng giữ nguyên.

## Cách lên 2.37

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.

**Dữ liệu bán hàng của quán giữ nguyên tuyệt đối** — hàng hóa, hóa đơn, khách hàng, công nợ, nhân viên… không mất gì cả, không phải cài đặt hay thiết lập lại.

## Tải về

- **PPOS.exe** — bản Windows, bấm đúp chạy ngay, không cần cài đặt (cho khách mới hoặc máy ở bản cũ hơn 2.26). 72.433.080 byte · MD5 `650832f86f7ea11a3824c0613576e8da`
- **PPOS-app-v2.37.zip** — gói mã nguồn giao diện + máy chủ nội bộ (cho nhu cầu kỹ thuật). 1.369.733 byte · MD5 `a2edc8e319e14e03808eefcb541f34e9`
- **PPOS-web-update-v2.37.zip** + **update-manifest.json** — gói cập nhật và bản tin phiên bản đã ký số. 362.688 byte · MD5 `26a823639e1abaec2011965d1a7ea88c` · SHA-256 `bb91f815877f7a6826646c4cfc5e3429ecf4bafef27f77aee1c7b231257655e4`. Bản tin v2.37 là cập nhật trong app thông thường (không bắt buộc tải exe), áp cho máy vỏ 2.26 trở lên.
