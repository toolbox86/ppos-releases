# PPOS v2.38 — Số lượng và đơn vị cùng một hàng ở phiếu nhập, cột phải phiếu nhập & phiếu trả liền một khối

Bản này dọn lại **bố cục ba màn phiếu** (phiếu nhập hàng, phiếu trả nhà cung cấp, kiểm kho) theo đúng ảnh chụp trên máy quầy thật của quán: nhập liệu nhanh hơn, màn hình thoáng và đều nhau hơn. Toàn bộ nghiệp vụ — quy đổi đơn vị và tồn kho, tổng tiền phiếu, công nợ nhà cung cấp, lưu tạm và chốt phiếu — giữ nguyên cơ chế như trước; phía phát triển đã kiểm chứng bằng bộ ca tự động (Đợt 130: 15/15, gồm ca lưu tạm → tiếp tục nhập → chốt phiếu trọn vẹn với tồn kho và công nợ khớp số).

## Phiếu nhập hàng: số lượng và đơn vị nằm trên cùng một hàng

- Trước đây, ô nhập **số lượng** và ô chọn **đơn vị tính** ở mỗi dòng hàng phiếu nhập xếp chồng thành hai hàng, kèm dòng chữ nhỏ bị ngắt xuống dòng khó nhìn — dòng hàng bị cao và rối. Nay hai ô nằm **trên cùng một hàng ngang**, cột số lượng được nới rộng, dòng chữ nhỏ "Giá nhập tính theo đơn vị này" nằm gọn một dòng ngay dưới.
- Thao tác giữ nguyên tuyệt đối: đổi đơn vị vẫn quy đổi tồn kho theo hệ số đóng gói như cũ (ví dụ nhập 2 lốc × 6 thì tồn cộng 12), giá và tổng tiền không đổi.

## Cột thông tin bên phải liền một khối, thoáng hơn

- Ở **phiếu nhập hàng** và **phiếu trả nhà cung cấp**, cột thông tin bên phải trước đây tách thành hai thẻ rời nhau (thẻ tiền của phiếu trả còn có nền xám riêng). Nay gộp thành **một khối liền mạch duy nhất**, phân tách nhẹ bằng đường kẻ mờ; khoảng cách giữa các phần được giãn đều, thoáng hơn.
- Các nút **Lưu tạm / Nhập hàng / Tạo phiếu trả / Quay lại danh sách** giữ nguyên vị trí và cách bấm như cũ.
- Màn **kiểm kho** vốn đã là một khối — bản này chỉ chuẩn hoá khoảng cách cho đồng bộ với hai màn phiếu.

## Cách lên 2.38

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.

**Dữ liệu bán hàng của quán giữ nguyên tuyệt đối** — hàng hóa, hóa đơn, khách hàng, công nợ, nhân viên… không mất gì cả, không phải cài đặt hay thiết lập lại.

## Tải về

- **PPOS.exe** — bản Windows, bấm đúp chạy ngay, không cần cài đặt (cho khách mới hoặc máy ở bản cũ hơn 2.26). 72.434.011 byte · MD5 `ffd598a4df5448b501114bacc3729136`
- **PPOS-app-v2.38.zip** — gói mã nguồn giao diện + máy chủ nội bộ (cho nhu cầu kỹ thuật). 1.368.819 byte · MD5 `24099224a7046b514878149c1d242179`
- **PPOS-web-update-v2.38.zip** + **update-manifest.json** — gói cập nhật và bản tin phiên bản đã ký số. 362.842 byte · MD5 `f434a1fb87aa55e52d41e631fcd47c19` · SHA-256 `ecdfcc7afc9af6a7c30ae7c0701764a64f60dd1606f9454b819562c1488ba499`. Bản tin v2.38 là cập nhật trong app thông thường (không bắt buộc tải exe), áp cho máy vỏ 2.26 trở lên.
