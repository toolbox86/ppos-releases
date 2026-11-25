# PPOS v2.47 — Bán trên điện thoại khi mất liên lạc + máy quầy tự gộp đơn vào sổ chung

Phát hành: 24/11/2026 · Đợt 152

## Có gì mới

- **Bán trên điện thoại kể cả khi mất liên lạc với máy quầy:** trước đây, nếu điện thoại mất hẳn liên lạc TRƯỚC lúc bấm thu tiền (mất Wi-Fi, máy quầy chưa mở), đơn không được tạo ra — quán tưởng đã bán nhưng không có đơn nào được ghi. Nay điện thoại vẫn chốt đơn bình thường ngay tại máy, hiện thanh cảnh báo đỏ rõ ràng và tự gửi lên quầy khi có liên lạc lại.
- **Máy quầy tự gộp đơn của điện thoại vào sổ chung:** khi hai máy lệch nhịp (điện thoại có đơn chờ trong lúc quầy đã bán thêm), trước đây đơn của điện thoại bị cất vào bản lưu dự phòng chờ quản lý gộp tay, doanh thu thiếu và hai máy có thể trùng số hóa đơn. Nay máy quầy tự gộp các chứng từ mới của điện thoại (hóa đơn, phiếu trả, phiếu nhập, sổ kho, sổ điểm, thu nợ) vào sổ chung: doanh thu và tồn kho khớp ngay; trùng số hóa đơn thì máy quầy tự cấp số mới và ghi báo động cho chủ quán.
- **Quản lý gộp dữ liệu dự phòng ngay trên điện thoại:** mục Cài đặt nay mở cho tài khoản quản lý trên điện thoại (tài khoản khác vẫn chỉ bán hàng), kèm huy hiệu bền "⚠ N bản lưu chờ gộp" trên màn hình — còn dữ liệu chờ gộp là thấy ngay, không bị trôi như thông báo thoáng.
- **Thanh cảnh báo đồng bộ đáng tin hơn:** luôn hiện lý do của lần gửi hỏng mới nhất và tự tắt ngay khi mọi thứ đã đồng bộ xong.

## Kiểm thử (bên dev)

- impl-dot152: 21/21 đạt (máy chủ quầy thật + app thật) — lệch phiên bản có đơn mới: tự gộp đủ (số trùng HD1001→HD1002, tồn kho trừ theo sổ kho, nợ cộng theo chứng từ, có báo động); lệch phiên bản không có gì mới: vẫn trả 409 như cũ; cổng gói Free và vai trò Chỉ xem vẫn chặn ngay trên đường tự gộp; sổ nhật ký gửi lên có dòng trùng mã trong cùng lô: chỉ gộp một; mất liên lạc trước khi chốt: đơn vẫn được tạo + cảnh báo bền; banner hiện lý do mới nhất và tự tắt sau khi nạp bản mới; huy hiệu chờ gộp + quản lý mở được Cài đặt ở khung điện thoại 390px.
- Hồi quy: impl-dot151 13/13 · impl-dot150 8/8 · impl-dot149 21/21 · audit3-tax 34/34.

## Ghi chú kỹ thuật (cho đội QA)

- Phía máy chủ (server.js): hàm `autoMerge152` chạy tại điểm trả 409 cũ. Thứ tự: kiểm cổng phiên/vai trò/gói cho máy con (403 session/role/plan như đường ghi thường, chữ ký sai chỉ cảnh báo theo Đợt 98) → gộp vào bản sao của dữ liệu quầy → lưu + phát sóng + `addAlarm`, phản hồi 200 kèm `autoMerged {invoices, returns, receipts, renumbered[]}`. Không có chứng từ mới nào gộp được thì trả 409 như cũ. Luật gộp: khách khớp theo mã, trùng SĐT thì trỏ về hồ sơ quầy, khách mới thì thêm; hóa đơn/phiếu trả TH/trả NCC TN/phiếu nhập PN trùng số thì cấp số mới theo bộ đếm của quầy (số hóa đơn đệm 6 chữ số từ 10000); tồn kho áp theo dòng sổ kho (`stock += qty`), hàng có lô thì trừ lô FEFO; điểm tính lại từ sổ điểm như `refreshPoints`; nợ áp theo chứng từ (phần ghi nợ của hóa đơn, phiếu thu nợ/cấn trừ kèm `paidDebt` theo `allocs`). Sửa đổi lên bản ghi cũ: bản quầy thắng. Giới hạn: phiếu trả trên điện thoại cho hóa đơn của quầy không cập nhật ngược các trường của hóa đơn gốc (trạng thái/điểm đã thu hồi) — phần tiền nợ vẫn đúng qua phiếu thu đi kèm.
- Phía app: `hubTx` bắt lỗi mạng ở bước lấy khóa/hỏi phiên bản → `runLocal152` vẫn chạy hàm chốt đơn tại máy + `hubPushFailSet150` + tự gửi lại; tài khoản Chỉ xem bị chặn ngay tại `hubTx` với đúng thông điệp vai trò. `hubPushRun` gặp phản hồi `autoMerged` thì nạp bản đã gộp về, dữ liệu thuộc bảng chưa gộp tự động (chấm công, đơn từ, tạm ứng, kiểm kho) nếu sót lại sẽ được cất vào bản lưu dự phòng. `PHONE_MGR_OK` thêm `"settings"`; huy hiệu `stashBadge152` đếm từ `ppos_conflict_meta`. `hubRefresh` thành công thì tắt cảnh báo đồng bộ (vá BUG-246-04); `hubSyncWarn150` cập nhật lý do mới nhất (vá OBS-246-02); `conflictStash` bỏ qua lần cất trùng nội dung trong 3 giây (vá OBS-246-05) và nhận tham số `dbOverride`.
