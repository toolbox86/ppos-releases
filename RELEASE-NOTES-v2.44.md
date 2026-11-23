# PPOS v2.44 — Số hóa đơn nối tiếp dãy cũ + danh sách hóa đơn mới nhất lên đầu

Phát hành: 23/11/2026 · Đợt 148

## Có gì mới

- **Số hóa đơn tự nối tiếp dãy số của phần mềm cũ:** khi nạp dữ liệu bán hàng từ phần mềm trước (KiotViet, VietSalePro...), PPOS tự nhận biết hóa đơn mới nhất đang có trong sổ và xuất đơn mới với số kế tiếp liền dãy, đủ 6 chữ số (ví dụ đang có HD020080 thì đơn mới là HD020081) — không trùng số, không nhảy số, chủ quán không cần chỉnh tay. Cơ chế tự động hoàn toàn: app tự quét số lớn nhất mỗi lần mở/khôi phục dữ liệu và nâng bộ đếm theo.
- **Danh sách hóa đơn đã bán hiện đơn mới nhất lên trên đầu** (theo ngày giờ bán) — vừa bán xong mở ra là thấy ngay.

## Kiểm thử (bên dev)

- impl-dot148: 6/6 đạt — bộ đếm tự nâng 19989 → 20080 theo hóa đơn HD020080 trong sổ; bán thật ra HD020081, HD020082; 3 dòng đầu danh sách đúng thứ tự mới → cũ; số nhỏ giữ dạng cũ (counter 1005 → HD1006); không lỗi trang.
- Hồi quy: impl-dot147 18/18 · audit3-tax 34/34.

## Ghi chú kỹ thuật (cho đội QA)

- Helper `invNumFmt148(n)`: "HD" + (n ≥ 10000 ? đệm 6 chữ số : giữ nguyên) — áp ở checkout và ở đường đánh số lại khi gộp dữ liệu trùng số. Số < 10000 giữ nguyên định dạng cũ.
- `renderInvoices` → `draw()`: danh sách đã lọc được `.sort(cmpInvNew148)` (ngày + giờ giảm dần, hòa thì số hóa đơn lớn hơn trước) — chỉ sắp bản sao hiển thị, không thay đổi thứ tự lưu trữ.
- PO đã chốt: giữ cơ chế bộ đếm tự động im lặng, KHÔNG thêm hộp thoại xác nhận khi bộ đếm tự nâng.
