# PPOS v2.50 — Gọn hai danh sách dài, TKN-CNKD sát mẫu giấy, sao lưu tự động giữ đúng số, nút mở thư mục sao lưu

Phát hành: 26/11/2026 · Đợt 156 + 157 + 158 + 159

## Có gì mới

- **Gập gọn hai danh sách dài (Đợt 156, theo Cách A chủ quán chọn):** "Lịch sử cập nhật" trong mục Bản quyền & Cập nhật và "Nhật ký hoạt động" trong chi tiết từng nhân viên trước đây liệt kê toàn bộ (14 bản cập nhật, hàng chục việc) làm màn hình rất dài. Nay mỗi danh sách chỉ hiện **3 dòng mới nhất**, phần còn lại nằm sau nút **"▾ Xem tất cả …"** / **"▾ Xem thêm … việc nữa"** — bấm mới mở ra, bấm **"▴ Thu gọn"** để gấp lại. Danh sách có từ 3 dòng trở xuống thì hiện như cũ, không có nút. Mỗi lần mở lại màn hình, danh sách tự trở về trạng thái gập.
- **Thông báo doanh thu 01/TKN-CNKD dựng lại sát file mẫu docx (Đợt 157):** đối chiếu trực tiếp với file mẫu chính thức (Thông tư 89/2026/TT-BTC) và sửa 6 điểm lệch của bản v2.49: (1) đầu mẫu — quốc hiệu và "Độc lập - Tự do - Hạnh phúc" căn giữa, "Mẫu số: 01/TKN-CNKD" nằm ở góc phải trên; (2) khối kỳ tính thuế [01]–[03] trình bày dạng bảng 2 cột như mẫu ([01a]/[01b]/[01c] xếp chồng trong một ô); (3) thông tin [04]–[07] về một dòng liền (nhãn + giá trị ngay sau); (4) Phần B (thuế TTĐB), Phần C (thuế tài nguyên / BVMT / phí BVMT khoáng sản) và Phần D (thuế GTGT/TNCN hàng nhập khẩu) nay là **bảng thật đúng cấu trúc mẫu** thay cho dòng chữ "không phát sinh" trước đây; (5) Phần E đủ từng dòng [49]–[51.3] kèm **bảng bù trừ [52]–[64]**; (6) khối ký: dòng "ngày… tháng… năm…" lên đầu cột phải, hai tiêu đề căn giữa từng cột, tên người đại diện nằm dưới cột phải; ghi chú đủ 4 ý nguyên văn (bổ sung ý [3.1]/[3.2] về đất đá bóc, đất đá thải và ý hệ số K theo Nghị định 27/2023/NĐ-CP). Các công thức [15]–[18]/[21] chuyển sang cột "Nhóm ngành nghề" như mẫu giấy, nhãn chỉ tiêu sạch.
- **Sao lưu tự động giữ đúng số bản đã đặt (Đợt 158, chủ quán chốt):** trước đây bản sao lưu vừa ghi không tính vào số giữ, nên đặt giữ 3 mà thư mục có 4 bản tự động. Nay bản vừa ghi **tính vào số giữ** — mỗi khi có bản tự động mới, các bản tự động cũ nhất bị xóa bớt cho đủ đúng số đã đặt. Bản sao lưu tay và bản an toàn trước mỗi lần khôi phục giữ nguyên cơ chế riêng (tối đa 30 bản), không bị xóa theo số này. Dòng ghi chú dưới ô "Số bản TỰ ĐỘNG giữ lại" trong phần mềm cũng đã viết lại cho khớp.
- **Nút "Mở thư mục chứa bản sao lưu" (Đợt 159):** trong thẻ "Sao lưu toàn bộ dữ liệu" có thêm nút **"📂 Mở thư mục chứa bản sao lưu"** ngay cạnh nút "Sao lưu ngay vào thư mục trên máy tính" — bấm là mở thẳng thư mục đang chứa các bản sao lưu trên máy tính quầy (đúng thư mục đang cấu hình, kể cả thư mục tùy chọn). Nút chỉ hiện trên máy tính quầy, giống nút sao lưu bên cạnh.

## Kiểm thử (bên dev)

- impl-dot156: 9/9 — lịch sử cập nhật 14 bản chỉ hiện 3 dòng + nút mở đủ 14; nhật ký 10 việc chỉ hiện 3 + nút mở đủ 10; danh sách ngắn (≤3) không có nút thừa.
- impl-dot157: 15/15 — form TKN đối chiếu cấu trúc docx mẫu (7 bảng); hồi quy impl-dot155 15/15 · impl-dot146 30/30 · impl-dot147 18/18 · audit3-tax 34/34.
- impl-dot158: 5/5 — hub thật: gieo 5 bản tự động cũ, đặt giữ 3, gói Business → sau khi hub ghi bản tự động hôm nay còn đúng 3 bản mới nhất; bản tay + bản an toàn còn nguyên; sao lưu tay thêm vẫn đúng 3 bản tự động.
- impl-dot159: 4/4 — endpoint mở thư mục trả 200 đúng thư mục cho máy quầy, bị chặn khi không phải máy quầy, hub vẫn sống sau khi mở; app có nút + handler đúng.
- Hồi quy: impl-dot152 21/21 · audit-sec-hub 21/21.
- Kiểm chứng trực quan: chụp màn hình app chạy từ hub thật ở chế độ máy quầy — nút "Mở thư mục chứa bản sao lưu" nằm đúng vị trí, bấm thử hiện xác nhận; ảnh đối chiếu form TKN với dữ liệu quán thật (doanh thu 2026 = 252.878.560đ).

## Ghi chú kỹ thuật (cho đội QA)

- Đợt 156 (chỉ app/index.html): helper chung `moreToggle156(btn, boxId, moreLabel)`; lịch sử cập nhật cắt tại `#upd-hist-more`, nhật ký nhân viên dựng dòng bằng `actOne156` và cắt tại `#us-acts-more`; trạng thái mở/gập không lưu.
- Đợt 157 (chỉ app/index.html): viết lại toàn bộ `tknForm155` theo cấu trúc 7 bảng của docx, các bảng B/C/D/E ánh xạ lên lưới 19 cột của Phần A bằng merge ô. Nới bộ máy form Đợt 145: thêm kind căn giữa không viền `ctr/ctrb/ctri` (HTML + style Excel) và hỗ trợ ô nhiều dòng (`\n` → `<br>` ở HTML; Excel đã có wrapText) — không đổi hành vi các form cũ.
- Đợt 158 (server.js): `pruneBackups` — danh sách bản tự động nay gồm cả file vừa ghi (tính vào số giữ, `autos.slice(k)` xóa phần vượt); riêng file vừa ghi không bị xóa ngay trong lượt của nó (chỉ còn ý nghĩa khi mtime bất thường — giữ an toàn SL-19, lượt ghi sau tự đưa về đúng số). Nhánh bản tay/an toàn không đổi (trần `BK_MANUAL_CAP = 30`).
- Đợt 159 (server.js + app/index.html): endpoint mới `POST /api/openbackupdir` — cổng `isHost` (không token → 401 ở lớp auth); mở thư mục sao lưu bằng `explorer.exe` / `open` / `xdg-open` theo hệ điều hành, spawn detached + `on("error")` chống sập hub + `unref`, trả `{ok, dir}`. Nút `#bk-open` cùng điều kiện hiển thị `HUB.on && HUB.host` với `#bk-now`.
