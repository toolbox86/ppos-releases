# PPOS v2.40 — Bán hàng trên điện thoại: thẻ hàng trong đơn sắp lại theo cột Đơn vị tính

Bản này gồm một đợt cải tiến duy nhất: **Đợt 134** (thẻ dòng bán hàng trên điện thoại theo bảng 6 cột — kiểm chứng tự động 11/11 ca trên khung điện thoại 390px, kèm hồi quy desktop Đợt 133 đạt 15/15 và Đợt 129 đạt 48/48).

## Chuyện là thế này

Đợt 133 (bản 2.39) thêm cột **Đơn vị tính** vào bảng hàng trong đơn bán — trên máy tính quầy mọi thứ đúng chuẩn. Nhưng phần bố cục **thẻ hàng trên điện thoại** vẫn được chia ô theo bảng 5 cột cũ, nên từ bản 2.39, khi bán bằng điện thoại:

- Ô chọn đơn vị tính chiếm vị trí của ô số lượng, bị ép nhỏ;
- Ô số lượng và ô đơn giá bị xô lệch vị trí theo;
- **Thành tiền** bị đẩy lên góc phải trên cùng, sát tên hàng — dễ nhìn nhầm là đơn giá;
- **Nút bỏ món (✕)** không còn chỗ trong lưới — rơi xuống góc dưới-trái, một mình một hàng, khó thấy và dễ bấm nhầm.

Chức năng đổi đơn vị trên điện thoại vẫn chạy (dùng chung một hàm vẽ với máy tính), nhưng bố cục như vậy là chưa đạt — bản 2.40 sửa dứt điểm phần hiển thị này.

## Đã sửa (Đợt 134)

Thẻ hàng trong đơn trên điện thoại nay xếp thành 3 hàng rõ ràng:

- **Hàng 1:** tên hàng + số tồn kho — nút bỏ món ✕ về đúng **góc phải trên**;
- **Hàng 2:** **ô chọn Đơn vị tính** (được nâng cao bằng các ô chạm khác, chữ rõ) + bộ tăng/giảm **Số lượng**;
- **Hàng 3:** ô **Đơn giá** + **Thành tiền** in đậm bên phải.

Hàng không có quy đổi thì ô đơn vị hiện tên đơn vị dạng chữ như trên máy tính, bố cục thẻ không thay đổi. Chỉ sửa phần hiển thị trên điện thoại — **màn Bán hàng trên máy tính quầy giữ nguyên y hệt bản 2.39**, logic bán hàng, trừ kho và tính tiền không thay đổi.

## Cách lên 2.40

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**. Điện thoại bán hàng trong quán tự nhận giao diện mới sau khi máy quầy cập nhật.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.

**Dữ liệu bán hàng giữ nguyên tuyệt đối.**
