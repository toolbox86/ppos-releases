# PPOS v2.39 — Chọn đơn vị ngay trên dòng đơn bán, nhập Excel KiotViet chuẩn hơn, phiếu nhập thẳng hàng

Bản này gồm ba đợt cải tiến đã được kiểm chứng tự động kỹ trước khi phát hành: **Đợt 133** (cột Đơn vị tính ở màn Bán hàng — 15/15 ca, gồm chốt đơn thật trừ kho đúng theo hệ số quy đổi), **Đợt 132** (bộ nhập Excel KiotViet + cơ chế mã đơn vị quy đổi — 33/33 ca trên file thật 576 dòng của quán) và **Đợt 131** (canh thẳng dòng hàng phiếu nhập/phiếu trả — 11/11 ca). Sau Đợt 133, phía phát triển còn chạy một **kiểm toán chuỗi riêng** cho hàng quy đổi đi trọn vòng đời (nhập hàng → bán → khách trả → trả nhà cung cấp → đối chiếu sổ kho): 16/16 ca khớp số tuyệt đối; đồng thời rà soát dứt điểm bộ kiểm tra trả hàng NCC cũ (110/110 ca sau khi cập nhật bộ kiểm tra theo mô hình thanh toán phiếu nhập của Đợt 127 — phần mềm không đổi).

## Bán hàng: cột Đơn vị tính ngay trên dòng đơn (Đợt 133)

- Trước đây, muốn bán theo đơn vị quy đổi (thùng) phải bấm nút nhỏ "+ THÙNG" cạnh kết quả tìm kiếm; bấm vào thân dòng thì ra đơn vị lẻ — cùng một dòng hàng, hai cách bấm cho hai đơn vị, rất dễ nhầm (đúng ảnh chụp trên máy quầy của quán).
- Nay bảng dòng hàng trong đơn có thêm cột **Đơn vị tính**: hàng có quy đổi hiện **ô chọn** (ví dụ `LỐC` / `THÙNG (×12)`), chọn đơn vị nào thì **giá tự nhảy theo đơn vị đó** (giá thùng lấy đúng giá quy đổi đã đặt, kể cả giá riêng của thùng), kho trừ đúng theo hệ số. Hàng không có quy đổi thì cột này chỉ hiện tên đơn vị như cũ. Đây là cách KiotViet đang làm.
- Nút "+ đơn vị quy đổi" ở kết quả tìm kiếm và ở lưới Chọn hàng đã bỏ — bấm hàng ở mọi đường đều thêm theo đơn vị lẻ, đổi đơn vị tại cột Đơn vị tính trong đơn. Nếu đơn đã có sẵn một dòng ở đơn vị đích, máy **tự gộp số lượng** vào dòng đó, không để hai dòng cùng đơn vị song song.
- **Quét mã/mã vạch của đơn vị quy đổi** ở quầy vẫn vào thẳng 1 đơn vị lớn như trước (xem Đợt 132).

## Nhập Excel KiotViet + mã đơn vị quy đổi (Đợt 132)

- Bộ nhập danh sách sản phẩm từ KiotViet được sửa theo đúng mô hình dữ liệu của KiotViet (dòng gốc + dòng quy đổi liên kết bằng cột "Mã ĐVT Cơ bản"):
  - Chỉ gắn quy đổi khi hệ số **lớn hơn 1**, và gắn kèm **giá bán riêng** của dòng quy đổi (ví dụ thùng Hanie 565.000 thay vì nhân giá lẻ), **mã riêng** và **mã vạch riêng** (nếu có) của dòng quy đổi.
  - Dòng hệ số **bằng 1** là hàng biến thể (ví dụ kem đánh răng 3 vị) — nay nhập thành **hàng riêng**, không còn bị nuốt mất.
  - Dòng hệ số **nhỏ hơn 1** (bán lẻ theo phân số) được **bỏ qua và liệt kê rõ** trong kết quả nhập; một hàng có nhiều dòng quy đổi thì giữ dòng đầu và cảnh báo các dòng còn lại.
- **Mã đơn vị quy đổi** có cơ chế riêng: form hàng hóa thêm ô **Mã đơn vị quy đổi** — máy tự sinh theo quy tắc *Mã hàng + "-" + chữ cái đầu của đơn vị* (bỏ dấu, trùng thì thêm số), chủ quán tự điền theo quy luật riêng cũng được, miễn không trùng mã hàng/mã quy đổi khác. Quét mã quy đổi ở quầy bán ra đúng dòng đơn vị lớn; xuất Excel ghi mã thật của quy đổi.
- Lưu ý dữ liệu cũ: nếu trước đây quán từng nhập file KiotViet bằng bản PPOS cũ và bị **trùng sản phẩm** (một mặt hàng thành hai dòng riêng), bản này không tự gộp dữ liệu cũ — hãy liên hệ hỗ trợ để được dọn dữ liệu an toàn (không cộng tồn kho của dòng trùng, vì đó là cùng một đống hàng diễn đạt khác đơn vị).

## Phiếu nhập & phiếu trả: dòng hàng thẳng hàng, có nhãn đơn vị (Đợt 131)

- Các ô trên dòng hàng của phiếu nhập và phiếu trả nhà cung cấp nay **cao bằng nhau, thẳng một hàng** (trước đây lệch nhau nhìn rối, đúng ảnh chụp máy quầy).
- Tiêu đề cột số lượng ở phiếu nhập tách rõ hai nhãn **Số lượng** và **Đơn vị tính**; ô chọn đơn vị bỏ chữ "theo", chỉ còn tên đơn vị (ví dụ `LỐC (×6)`).

## Cách lên 2.39

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.

**Dữ liệu bán hàng của quán giữ nguyên tuyệt đối** — hàng hóa, hóa đơn, khách hàng, công nợ, nhân viên… không mất gì cả, không phải cài đặt hay thiết lập lại.

## Tải về

- **PPOS.exe** — bản Windows, bấm đúp chạy ngay, không cần cài đặt (cho khách mới hoặc máy ở bản cũ hơn 2.26). 72.435.561 byte · MD5 `49dd62277aeaf962b08ef7c8203fb56d`
- **PPOS-app-v2.39.zip** — gói mã nguồn giao diện + máy chủ nội bộ (cho nhu cầu kỹ thuật). 1.373.738 byte · MD5 `4d65b52d8b566b63c61fe325ae5c3c4d`
- **PPOS-web-update-v2.39.zip** + **update-manifest.json** — gói cập nhật và bản tin phiên bản đã ký số. 366.614 byte · MD5 `c9b5bc55457e26782b00a2538470e5f6` · SHA-256 `053aa8b6ecd7d8c5d85aa3ce95a42609ce4f8a09e714a7df8c32c8bec3fefedd`. Bản tin v2.39 là cập nhật trong app thông thường (không bắt buộc tải exe), áp cho máy vỏ 2.26 trở lên.
