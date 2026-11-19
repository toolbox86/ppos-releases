# PPOS v2.36 — Kiểm kho theo kiểu phiếu và phiếu nhập hàng có lưu tạm

Bản này làm hai việc ở khâu mua hàng và kiểm kho: **kiểm kho đổi sang kiểu phiếu tìm–chọn–đếm** như màn Bán hàng, và **phiếu nhập hàng có lưu tạm đúng nghĩa** kèm các ô tiền mới. Cách chốt phiếu, cách tính tiền, trừ kho và trừ công nợ ở bước cuối giữ nguyên cơ chế như trước; phía phát triển đã kiểm chứng bằng bộ ca tự động (Đợt 126: 18/18, Đợt 127: 22/22, bộ đối chiếu số liệu Đợt 125: 72/72 khớp tuyệt đối).

## Kiểm kho theo kiểu phiếu

- Mở đợt kiểm là **phiếu trống** — gõ tìm hoặc quét mã vạch rồi chọn từng mặt hàng vào phiếu mới đếm, không còn phải lướt qua danh sách hàng nghìn món. Hàng có cỡ/màu vào phiếu đủ từng dòng biến thể; mỗi dòng có nút ✕ để bỏ ra.
- **Cột bên phải hiện đầy đủ thông tin đợt kiểm:** tên cửa hàng, mã đợt kiểm, trạng thái phiếu, ngày giờ kiểm, người kiểm, tổng số lượng sản phẩm, tổng thực tế, số lượng lệch tăng, số lượng lệch giảm, lệch tiền (theo giá nhập) và số dòng đã đếm.
- Thêm **ô Ghi chú** cho đợt kiểm và nút **Lưu tạm**: đếm dở thì lưu lại rồi về danh sách, lúc khác mở đợt kiểm ra đếm tiếp — số đã đếm không mất.
- Đợt kiểm đang mở ở bản cũ mở lên bản này đếm tiếp bình thường; đợt đã chốt xem lại vẫn hiện đầy đủ như trước. Cách **Chốt đợt kiểm** và cách tính lệch giữ nguyên tuyệt đối.

## Phiếu nhập hàng đầy đủ hơn

- **Nút Lưu tạm đúng nghĩa:** phiếu đang nhập dở được lưu thành một **phiếu tạm có số phiếu (PN) hẳn hoi** trong danh sách phiếu nhập — tắt máy mở lại vẫn còn, bấm **Tiếp tục nhập** là nhập tiếp đúng trạng thái đã lưu; khi xong bấm **Nhập hàng** thì chính phiếu tạm đó chuyển thành phiếu nhập chính thức, không sinh phiếu trùng. Có thể lưu nhiều phiếu tạm cùng lúc. Phiếu tạm **chưa cộng tồn kho, chưa ghi công nợ**, không vào báo cáo và không hiện trong danh sách phiếu gốc khi làm phiếu trả.
- **Thêm các ô tiền ở cột bên phải:** Số hóa đơn đầu vào (số trên hóa đơn của nhà cung cấp), **Giảm giá từ nhà cung cấp**, **Chi phí nhập** (ví dụ phí ship nhà cung cấp tính vào hóa đơn). Phần mềm tự tính **Tổng tiền cần trả = Tổng tiền hàng − Giảm giá + Chi phí nhập**.
- **Ô Tiền thực tế trả** thay cho cách chọn "Trả ngay / Ghi nợ" trước đây: ô tự điền sẵn bằng Tổng tiền cần trả; trả thiếu bao nhiêu thì phần còn lại tự thành **công nợ** (có hạn trả theo kỳ hạn của nhà cung cấp như trước), kèm chọn **Phương thức thanh toán** (tiền mặt / chuyển khoản) lưu trên phiếu. Giảm giá và chi phí nhập chỉ tác động vào số tiền phải trả nhà cung cấp, **không đổi giá vốn** của từng món.

## Không còn chọn sẵn nhà cung cấp

- Cả **phiếu nhập hàng** và **phiếu trả hàng cho nhà cung cấp** mở lên đều **chưa có nhà cung cấp nào được chọn** — mỗi lần làm phiếu phải gõ tìm (theo tên hoặc số điện thoại) rồi chọn đúng nhà cung cấp, tránh nhập nhầm phiếu cho nhà cung cấp khác.
- Phiếu trả chưa chọn nhà cung cấp thì chưa chọn được phiếu nhập gốc và chưa lưu được phiếu.

## Cách lên 2.36

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.

**Dữ liệu bán hàng của quán giữ nguyên tuyệt đối** — hàng hóa, hóa đơn, khách hàng, công nợ, nhân viên… không mất gì cả, không phải cài đặt hay thiết lập lại.

## Tải về

- **PPOS.exe** — bản Windows, bấm đúp chạy ngay, không cần cài đặt (cho khách mới hoặc máy ở bản cũ hơn 2.26). 72.430.061 byte · MD5 `41b9a34420e3e5cf3a13e12e4b338dc3`
- **PPOS-app-v2.36.zip** — gói mã nguồn giao diện + máy chủ nội bộ (cho nhu cầu kỹ thuật). 1.365.725 byte · MD5 `24306c58162e150886fc28a8f79efcbf`
- **PPOS-web-update-v2.36.zip** + **update-manifest.json** — gói cập nhật và bản tin phiên bản đã ký số. 358.702 byte · MD5 `e0d743d83da352aaa448969bd21607e8` · SHA-256 `5a11499383f19431afbf80c9ca57b51278350a786962c4cd10aca250dee95497`. Bản tin v2.36 là cập nhật trong app thông thường (không bắt buộc tải exe), áp cho máy vỏ 2.26 trở lên.
