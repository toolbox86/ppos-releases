# PPOS v2.48 — Tìm kiếm thông minh kiểu KiotViet + gộp dữ liệu chờ đồng bộ 1 chạm

Phát hành: 25/11/2026 · Đợt 153 + Đợt 154

## Có gì mới

- **Tìm kiếm thông minh như KiotViet (Đợt 154):** trước đây ô tìm hàng và tìm khách phải gõ đúng nguyên cụm liền nhau mới ra kết quả (gõ "smarta vani 110" không ra "Sữa Smarta Grow Vani 110ml"). Nay máy tách từ khóa thành từng từ — từ nào cũng có mặt trong tên là hiện, không cần đúng thứ tự, không cần gõ liền, gõ không dấu vẫn ra. Ví dụ: "smarta vani 110" → Sữa Smarta Grow Vani 110ml; "trinh tuyet" → Chị Trinh Tuyết Phi. Áp dụng ở mọi ô tìm: tìm hàng và tìm khách ở màn bán hàng, ô khách trong khung thu tiền, các ô chọn hàng khi nhập hàng / trả hàng / kiểm kho, chọn nhà cung cấp, và các màn danh sách Hàng hóa / Khách hàng / Nhà cung cấp. Tìm theo mã vạch, mã hàng, số điện thoại giữ nguyên.
- **Ô chọn khách ở màn bán hàng tách riêng hẳn (Đợt 154):** trước đây bấm vào ô "Tìm khách hàng" ở màn bán là bật luôn khung Thu tiền. Nay ô khách là ô tìm–chọn độc lập như ô tìm hàng: bấm vào là hiện danh sách khách để tìm và chọn ngay tại chỗ (có sẵn hàng Khách lẻ, nút ✕ bỏ khách, nút ＋ thêm khách mới); khung Thu tiền chỉ mở khi bấm nút thanh toán.
- **Gộp dữ liệu chờ đồng bộ chỉ 1 chạm (Đợt 153):** khi điện thoại còn giữ bản lưu chờ gộp (huy hiệu cam "⚠ N bản lưu chờ gộp"), quản lý mở ngay trên máy đang cầm: Cài đặt → Sao lưu dữ liệu → bấm **"Gộp ngay vào sổ"** → nhập PIN quản lý là dữ liệu được cộng thẳng vào sổ hiện tại. Trước đây phải tải file dự phòng ra rồi chuyển sang máy khác để gộp. Bấm vào huy hiệu chờ gộp cũng đưa thẳng tới đúng mục này.
- **Vá lỗi huy hiệu chờ gộp treo (Đợt 153b):** huy hiệu có thể vẫn hiện dù dữ liệu đã gộp hết; nay đếm đúng và tự tắt khi không còn bản lưu nào.

## Kiểm thử (bên dev)

- impl-dot154: 12/12 đạt (app thật; gieo đúng ví dụ thực tế: hàng "Sữa Smarta Grow Vani 110ml", khách "Chị Trinh Tuyết Phi") — hàm khớp thông minh đúng/sai từ; tìm hàng ở lưới máy tính và panel điện thoại đều lọc đúng; tìm khách theo tên tách từ / số điện thoại / mã khách; bấm ô khách không mở khung thu tiền, chọn khách xong khung vẫn đóng; nút ✕ về Khách lẻ; nút thanh toán mới mở khung thu tiền.
- impl-dot153: 11/11 đạt — huy hiệu đưa quản lý tới đúng tab Sao lưu dữ liệu; Gộp ngay + PIN quản lý: đơn trong bản dự phòng vào sổ, bản dự phòng được gỡ, huy hiệu tắt; đường gộp bằng file vẫn đúng; người bán nhận đúng câu nhắc.
- Hồi quy: impl-dot152 21/21 · impl-dot151 13/13.

## Ghi chú kỹ thuật (cho đội QA)

- Đợt 154: hàm chung `smartHit154(hay, q)` — tách `noAcc(q)` thành các từ, mọi từ phải là chuỗi con của chuỗi đích đã bỏ dấu. Điểm áp dụng: `prodSearch`, `supSearch` (bộ pick-pop), `renderGrid`, ô khách khung thu tiền (`pay-cust`), `renderCustomers`, bộ lọc màn Hàng hóa, màn Nhà cung cấp. Phím Enter ở ô tìm hàng: đường "đúng 1 kết quả thì thêm luôn" chuyển sang `prodSearch`. Ô khách màn bán: phần tử div cũ thay bằng `<input id="pos-cust">` + `#pos-cust-x` + `#pos-cust-add`; panel pick-pop owner `poscust`; chỉ mục khách `custIdx154` cache theo `__pickVer`; chọn khách gọi `repriceOrder` + `renderLines` + `renderPay`; `updatePaybar` đồng bộ nhãn qua `syncPosCust154()` (không ghi đè khi ô đang được gõ). Đã xóa onclick cũ mở `#pospay` từ hàng khách; phím tắt F4 vào ô khách trong khung thu tiền không đổi.
- Đợt 153: lõi gộp tách thành `mergeDbCore153(d)` dùng chung cho đường gộp bằng file và nút mới `mergeLatestStash153()` (cổng quyền Cài đặt + PIN quản lý qua `askManagerPin`; đọc bản dự phòng gần nhất từ IndexedDB theo `ppos_conflict_meta` hoặc khóa localStorage kiểu cũ; gộp xong gỡ đúng bản đó + làm mới huy hiệu `stashBadge152()`). 153b: `stashBadge152` loại trừ khóa `ppos_conflict_meta` khi đếm dự phòng theo tiền tố `ppos_conflict_`. Toàn bộ câu chữ "Cài đặt → Dữ liệu" đổi thành "Cài đặt → Sao lưu dữ liệu" (12 vị trí). server.js không đổi ở cả hai đợt.
