# PPOS v2.41 — Cài mới phải đăng ký tài khoản PPOS trước khi vào bán hàng

Bản này gồm một đợt thay đổi duy nhất: **Đợt 135** — cổng đăng ký bắt buộc khi cài mới, ghi nhận mã máy phía máy chủ bản quyền và công cụ quản trị khách hàng (kiểm chứng tự động: bộ kiểm cổng đăng ký 20/20 ca; hồi quy khôi phục sao lưu 60/60, thiết lập lần đầu + máy chủ trong quán 33/33 sau khi cập nhật theo thiết kế mới, bản quyền 81 đạt — chỉ còn 4 ca trượt vì khóa kiểm thử hết hạn theo ngày, đã biết từ trước).

## Pipeline khách mới từ bản này

1. Khách tải `PPOS.exe`, mở lên → gặp màn hình **đăng ký tài khoản PPOS**: tên đăng nhập, mật khẩu, tên quán, họ tên chủ quán, số điện thoại. Bước này **cần internet**.
2. Máy chủ bản quyền ghi nhận ngay khách mới kèm **mã máy và vân tay máy** — trang quản trị thống kê được tổng khách đã đăng ký và khách đang dùng gói Free.
3. Đăng ký xong **bắt buộc đăng nhập lại** bằng tài khoản vừa tạo (phần mềm cố ý không tự đăng nhập sau khi đăng ký).
4. Đăng nhập xong mới vào thiết lập lần đầu: tên quán, họ tên và số điện thoại **được điền sẵn từ tài khoản**, chủ shop đặt mã PIN như trước.
5. Từ lần mở sau, chỉ cần nhập **mã PIN** là vào bán hàng.

Không có internet ở lần mở đầu tiên: **chặn cứng** — phần mềm hiện màn hình chờ kết nối kèm nút Thử lại; chưa đăng ký được thì chưa vào được app. Trên màn hình cổng cũng có sẵn lối **đăng nhập** (cho khách cài lại máy / đổi máy đã có tài khoản) và lối **khôi phục file sao lưu** (khách mang dữ liệu cũ sang máy mới); quên mật khẩu có dòng nhắc nhắn Zalo hỗ trợ.

## Không ảnh hưởng máy đang dùng

- Máy **đã có người dùng** (đã qua thiết lập lần đầu) **không gặp cổng này** — cập nhật lên 2.41 vẫn vào thẳng bằng mã PIN như cũ, không phải đăng ký lại.
- Cổng chỉ xuất hiện ở **máy quầy khi cài mới tinh**; điện thoại bán hàng trong quán không qua cổng.
- Dữ liệu bán hàng, kho, công nợ, nhân viên... giữ nguyên tuyệt đối.

## Phía máy chủ + trang quản trị (đã lên sóng riêng ngày 21/11/2026)

- Hồ sơ khách hàng ghi thêm **mã máy** ở cả ba thời điểm: đăng ký, đăng nhập, điểm danh (check-in).
- Trang quản trị, mục Khách hàng: hàng thẻ thống kê (tổng khách đã đăng ký / đang dùng gói Free / đã có gói trả phí / đăng ký mới 7 ngày / 30 ngày), mã máy hiện trong danh sách và chi tiết khách, thêm nút **Đặt lại mật khẩu** — đặt lại xong, mọi phiên đăng nhập cũ của khách đó bị thu hồi ngay.

## Cách lên 2.41

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.

**Dữ liệu bán hàng giữ nguyên tuyệt đối.**
