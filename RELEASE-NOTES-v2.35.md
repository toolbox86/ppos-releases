# PPOS v2.35 — Ba màn tạo phiếu đổi bố cục giống màn Bán hàng

Bản này chỉ thay đổi **bố cục hiển thị** của ba màn tạo phiếu — **nghiệp vụ giữ nguyên tuyệt đối**. Mọi cách tính tiền, trừ kho, trừ công nợ và chốt phiếu đều y như bản 2.34; phía phát triển đã kiểm chứng bằng bộ ca tự động lái trọn cả 3 luồng ở bản cũ và bản mới: mọi con số (tổng phiếu, tồn kho, lô, công nợ nhà cung cấp, chênh lệch kiểm kho) **khớp tuyệt đối** giữa hai bản.

## Bố cục mới

Cả ba màn chuyển sang khuôn 2 cột giống màn Bán hàng:

- **Bên trái — vùng làm việc:** ô tìm hàng/quét mã vạch và bảng các dòng của phiếu.
- **Bên phải — cột phiếu cố định:** thông tin phiếu, các con số tổng kết và **nút chốt phiếu luôn nhìn thấy** — không còn phải cuộn xuống cuối trang mới bấm được nút chốt như trước.

Áp dụng cho:

- **Tạo phiếu nhập hàng:** cột phải gồm Nhà cung cấp, Ngày nhập, cách Trả tiền, Ghi chú, Tổng tiền phiếu và ô Trả ngay, nút **Nhập vào kho**.
- **Kiểm kho (phiên đang kiểm):** cột phải gồm 3 con số của đợt — Đã đếm, Số hàng bị lệch, Lệch tiền — ô chỉ xem hàng lệch và nút **Chốt đợt kiểm**.
- **Tạo phiếu trả hàng cho nhà cung cấp:** cột phải gồm Nhà cung cấp, Cách chọn hàng trả, Phiếu nhập gốc, Lý do trả, cùng 3 con số Tổng tiền hàng trả / Sẽ trừ công nợ / Phần vượt nợ và nút **Tạo phiếu trả**.

Phiếu nháp đang nhập dở ở bản cũ mở lên bản này vẫn nhập tiếp bình thường. Trên màn hình hẹp, cột phải tự xếp xuống dưới, không vỡ trang.

## Cách lên 2.35

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.

**Dữ liệu bán hàng của quán giữ nguyên tuyệt đối** — hàng hóa, hóa đơn, khách hàng, công nợ, nhân viên… không mất gì cả, không phải cài đặt hay thiết lập lại.

## Tải về

- **PPOS.exe** — bản Windows, bấm đúp chạy ngay, không cần cài đặt (cho khách mới hoặc máy ở bản cũ hơn 2.26).
- **PPOS-app-v2.35.zip** — gói mã nguồn giao diện + máy chủ nội bộ (cho nhu cầu kỹ thuật).
- **PPOS-web-update-v2.35.zip** + **update-manifest.json** — gói cập nhật và bản tin phiên bản đã ký số. Bản tin v2.35 là cập nhật trong app thông thường (không bắt buộc tải exe), áp cho máy vỏ 2.26 trở lên.
