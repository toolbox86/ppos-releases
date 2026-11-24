# PPOS v2.46 — Đồng bộ điện thoại không còn kẹt vì lệch sổ nhật ký + giữ an toàn đơn chưa đồng bộ

Phát hành: 24/11/2026 · Đợt 151

## Có gì mới

- **Máy quầy tự hòa sổ nhật ký khi lệch với điện thoại:** trước đây, khi sổ nhật ký (sổ ghi lại ai làm gì) giữa điện thoại và máy quầy lệch nhau — thường sau khi khôi phục dữ liệu hoặc bán lúc mất liên lạc — máy quầy chặn mọi lần gửi dữ liệu của điện thoại, đơn bán kẹt lại không lên được quầy. Nay máy quầy tự gộp hai sổ: giữ nguyên mọi dòng của quầy, thêm dòng mới của điện thoại, và báo cho chủ quán biết. Bán hàng không còn kẹt vì lệch sổ.
- **Đơn chưa kịp đồng bộ trên điện thoại được giữ an toàn:** khi điện thoại nạp lại dữ liệu từ máy quầy, các đơn chưa gửi được sẽ được cất vào bản lưu dự phòng (xem và gộp lại ở Cài đặt → Dữ liệu) thay vì biến mất khỏi máy như trước.

## Kiểm thử (bên dev)

- impl-dot151: 13/13 đạt (chạy trên máy chủ quầy thật + app thật) — sổ lệch/mất dòng: vẫn nhận ghi và gộp đủ; sửa dòng cũ: bản quầy thắng; sổ có dòng trùng mã: tự khử trùng, lần ghi sau sạch hẳn; ghi thêm bình thường: khớp y hệt; điện thoại có đơn chưa đồng bộ khi nhận bản quầy: đơn vào bản lưu dự phòng nguyên vẹn.
- Hồi quy: impl-dot150 8/8 · impl-dot149 21/21 · audit3-tax 34/34.

## Ghi chú kỹ thuật (cho đội QA)

- Phía máy chủ (server.js): cổng sổ nhật ký của Đợt 113 (QA4-03a) đổi từ trả 403 sang tự gộp — `only151` (dòng riêng của máy con, trần 2000) ++ sổ quầy đã khử trùng mã `oldDedup151` (trần tổng 8000); vẫn `addAlarm` khi phát hiện lệch. Các cổng khác (phiên, vai trò, gói, quyền nhân viên, danh mục hàng, trùng tên, guard, quản lý cuối) giữ nguyên.
- Phía app: `hubGuardLocal151(incoming)` chạy trước khi `hubRefresh`/`hubBoot` thay dữ liệu — nếu bản máy này có hóa đơn/phiếu trả mà bản quầy chưa có thì `conflictStash()` + toast. Bản lưu dự phòng dùng chung cơ chế với bản lưu xung đột 409, gộp lại được ở Cài đặt → Dữ liệu.
