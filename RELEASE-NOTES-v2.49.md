# PPOS v2.49 — Thông báo doanh thu 01/TKN-CNKD đúng mẫu mới Thông tư 89/2026/TT-BTC

Phát hành: 26/11/2026 · Đợt 155

## Có gì mới

- **Thông báo doanh thu năm dựng lại đúng mẫu chính thức (Đợt 155):** trước đây file "Thông báo doanh thu — Mẫu 01/TKN-CNKD" phần mềm xuất ra chỉ là bảng tóm tắt tự chế (mã / nhóm ngành / doanh thu) với mã chỉ tiêu kiểu cũ — không đúng mẫu cơ quan thuế ban hành. Nay toàn bộ biểu mẫu được dựng lại theo đúng **Mẫu số 01/TKN-CNKD kèm theo Thông tư 89/2026/TT-BTC ngày 30/6/2026**: quốc hiệu, dòng mẫu số, 6 ô đối tượng áp dụng (ô "doanh thu năm từ 1 tỷ đồng trở xuống" tích sẵn), kỳ tính thuế năm, và Phần A đủ 19 cột như mẫu giấy (thuế GTGT, thuế TNCN, số tiền nộp ngân sách, khấu trừ, nộp thêm, nộp thừa), đủ tiếp Phần B–E, đoạn cam đoan, khối ký tên và ghi chú của mẫu.
- **Nhóm ngành nghề ghi theo số (1)–(6) như mẫu mới:** dòng [08] — mỗi nhóm ngành có doanh thu nằm trên một dòng riêng, ghi số nhóm ngành ở cột nhóm ngành nghề, số tiền ở cột Tổng doanh thu; dòng Tổng cộng [13] mang tổng doanh thu ở [13.1] và in sẵn các mã [13.2]–[13.15] như mẫu giấy. Bỏ hẳn mã chữ kiểu cũ (08a, 08b…).
- **Đúng quy định "chỉ thông báo doanh thu":** theo ghi chú của mẫu, hộ có doanh thu năm từ 1 tỷ đồng trở xuống chỉ thực hiện thông báo doanh thu, không khai số thuế GTGT/TNCN phải nộp — phần mềm tự để trống toàn bộ các cột thuế, chỉ điền doanh thu theo nhóm ngành và tổng cộng.
- **Xem trước, Excel, PDF cùng một mẫu:** biểu mẫu dùng chung bộ máy trình bày với tờ khai 01/CNKD và các sổ kế toán — bản xem trên màn hình, file Excel tải về và bản in/PDF đều ra đúng một mẫu chuẩn. Số liệu doanh thu theo nhóm ngành giữ nguyên cách tính như trước, chỉ thay đổi mẫu trình bày.

## Kiểm thử (bên dev)

- impl-dot155: 15/15 đạt — mô hình dữ liệu nhóm ngành theo số mới (hàng hóa = (1) 200tr, dịch vụ = (2) 20tr, tổng 220tr); form đủ đầu mẫu (quốc hiệu, TT 89/2026, ô đối tượng đã tích, kỳ [01a] năm, tên hộ, mã số thuế); đúng 2 dòng [08] với số nhóm và tiền đúng cột, mọi cột thuế trống; dòng [13] đúng tổng và đủ mã [13.2]–[13.15]; đủ Phần B/C/D/E + cam đoan + khối ký + ghi chú; xem trước gắn đúng form; xuất Excel đúng tên sheet theo mã mẫu và có ô tổng doanh thu.
- Hồi quy: audit3-tax 34/34 · impl-dot146 30/30 · impl-dot147 18/18.
- Kiểm chứng trực quan: chụp màn hình app với dữ liệu quán thật (doanh thu 2026 = 252.878.560đ) — dòng [08] nhóm (1) và tổng [13.1] hiển thị đúng; đã cân lại bề rộng cột cho form 19 cột.

## Ghi chú kỹ thuật (cho đội QA)

- Đợt 155: thay `TAX_TKN_CODE` (mã chữ 08a–08g) bằng `TAX_TKN_IND155 = {goods:1, service:2, rent:3, prod:4, digital:5, other:6}`; `taxDeclTKN(year)` trả rows `{ind, num, rev}` — doanh thu vẫn từ `taxByIndustryDetail` như cũ. Thêm `tknForm155(year)` dựng form 19 cột bằng bộ máy Đợt 145 (`taxFormNew145`/`taxFormRow145`), mã mẫu "01/TKN-CNKD". Nhánh "tkn" của `declPreviewHtml` gắn `declCurrent.form` → nút Excel đi `exportExcelForm145`, PDF/In đi `taxPrintForm147` (trước đây là bảng 3 cột qua `exportExcel` thường).
- Đợt 155b/c/d (trình bày): bề rộng cột form TKN: Chỉ tiêu 44, cột Tổng doanh thu 13; `taxFormHtml145` thêm lớp `tf145w` cho form từ 15 cột trở lên (table-layout:fixed + font-size .82rem) để trình duyệt tôn trọng tỷ lệ cột — form hẹp (sổ TT152, 01/CNKD) không thay đổi. server.js không đổi ở đợt này.
