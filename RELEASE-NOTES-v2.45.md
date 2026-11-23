# PPOS v2.45 — Nhãn ghi nợ đúng + nút Bán nợ + đồng bộ điện thoại chắc chắn hơn

Phát hành: 24/11/2026 · Đợt 149 + Đợt 150

## Có gì mới

- **Đơn ghi nợ hiện đúng nhãn:** danh sách hóa đơn (máy tính + điện thoại), chi tiết đơn và lịch sử mua hàng của khách nay hiện "Ghi nợ" (nợ toàn bộ) hoặc "Còn nợ ..." (nợ một phần) thay vì "Đã thu tiền" như trước. Công nợ tổng vẫn tính đúng như cũ.
- **Nút thanh toán đổi chữ theo cách trả:** chọn Ghi nợ thì nút thành "BÁN NỢ", trả một phần là "THU TIỀN + BÁN NỢ", trả đủ là "THU TIỀN" — nhìn nút là biết đơn này sẽ ghi nợ hay thu tiền, hết nhầm.
- **Đồng bộ điện thoại – máy quầy không còn im lặng khi hỏng:** nếu điện thoại chưa gửi được dữ liệu về máy quầy (mất Wi-Fi, máy quầy bận, bị chặn vì quyền/gói), máy hiện thanh cảnh báo đỏ ghi rõ lý do kèm nút "Gửi lại ngay", và tự thử gửi lại mỗi ~20 giây cho tới khi thành công. Trước đây một lần gửi hỏng là rơi vào im lặng — đơn bán trên điện thoại có thể kẹt mà không ai biết (sự cố thật tối 23/11/2026).

## Kiểm thử (bên dev)

- impl-dot149: 21/21 đạt — nhãn nợ 3 kiểu (nợ hết / nợ một phần / đã thu đủ) trên danh sách + chi tiết + lịch sử khách; chữ nút thanh toán theo cách trả; đơn nạp từ phần mềm cũ hiện đúng phần còn ghi nợ.
- impl-dot150: 8/8 đạt (máy chủ giả lập) — bị chặn 403 hiện đúng lời nhắn của máy quầy; mất mạng hiện "Không liên lạc được với máy tính quầy"; nhịp tự kiểm tra gửi lại thành công khi mạng trở lại; nút "Gửi lại ngay" hoạt động.
- Hồi quy: impl-dot148 6/6 · audit3-tax 34/34.

## Ghi chú kỹ thuật (cho đội QA)

- Đợt 149: helper `invOwed149(i)` = (status done) ? max(0, total − Σ pays ngoài 'debt' − paidDebt) : 0; nhãn qua `invDonePill149` / `invDoneTxt149` tại danh sách hóa đơn, chi tiết đơn và lịch sử mua của khách. Nút thu tiền dùng `payBtnTxt149` tính từ `debtPart149` của `splitPays`. Nút "Thu nợ đơn này" giữ nguyên cổng cũ (không áp cho đơn imported — đơn chuyển từ phần mềm cũ thu nợ theo khách).
- Đợt 150: `hubPushRun` ghi lý do thất bại vào `HUB.pushFail` (ưu tiên trường `msg` tiếng Việt máy chủ trả về) và hiện thanh cảnh báo bền `#hub-syncwarn`; `hubPollTick` khi còn `HUB.dirty` sẽ tự `hubPushNow()` mỗi nhịp thay vì bỏ qua. Phía máy chủ (server.js) không thay đổi ở bản này.
