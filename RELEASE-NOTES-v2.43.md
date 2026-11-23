# PPOS v2.43 — Thuế & Kế toán hoàn thiện: tờ khai và sổ sách đúng mẫu nhà nước, thêm xuất PDF

Bản này gồm 4 đợt hoàn thiện khu Thuế & Kế toán: Đợt 144 (chốt XML theo file vàng HTKK), Đợt 145 (sổ kế toán dựng lại theo mẫu gốc Thông tư 152/2025), Đợt 146 (tờ khai 01/CNKD theo mẫu giấy + sửa bộ xuất Excel chung), Đợt 147 (nút Tải PDF + CSS in A4 + xóa ký tự thừa ở đầu trang). Kiểm chứng tự động: XML 10/10 · sổ mẫu gốc 43/43 · tờ khai mẫu giấy 30/30 · PDF 18/18 (gồm xuất PDF thật đo khổ trang) · hồi quy thuế: tờ khai 41/41 · nộp/khóa kỳ 25/25 · audit3 34/34.

## Đợt 144 — File XML 01/CNKD chốt theo file vàng HTKK

- Bộ sinh XML viết lại theo đúng một file XML thật do HTKK 5.5.4 kết xuất (mẫu Thông tư 40/2021, mã tờ khai 473, phiên bản XML 2.8.3): khung thẻ khớp file vàng 224/224, 14/14 giá trị then chốt đối chiếu tự động.
- Thuế GTGT trong file tính theo tỷ lệ gốc như HTKK tự tính (phần giảm 20% kê ở phụ lục giảm thuế); doanh thu tính TNCN đã trừ mức 1 tỷ lũy kế trong năm.
- Hồ sơ thuế thêm ô "Mã cơ quan thuế nơi nộp". Tên file tải xuống theo kiểu HTKK: `<MST>-01_CNKD_TT40-Q<quý><năm>-L00.xml`.
- Lưu ý: khi HTKK cập nhật mẫu Thông tư 50/2026, cần đối chiếu lại bằng một file vàng mới.

## Đợt 145 — Sổ kế toán dựng lại theo đúng biểu mẫu Thông tư 152/2025

- Cả 6 sổ S1a, S2a, S2b, S2c, S2d, S2e dựng lại theo file mẫu gốc (đối chiếu toàn văn Thông tư): đủ khối đầu "Mẫu số …-HKD", đúng từng cột, dòng tổng, khối ký — đồng nhất ở cả 3 đường ra: màn hình, Excel, in/PDF.
- S2d mở theo từng mặt hàng đủ 12 cột nhập/xuất/tồn; S2e tách tiền mặt và tiền gửi; dòng thuế TNCN ở S2c theo đúng công thức in trên mẫu (phần giảm 30% kê ở phụ lục riêng).

## Đợt 146 — Tờ khai 01/CNKD theo mẫu giấy + sửa bộ xuất Excel chung

- Xem trước, Excel và bản in của tờ khai 01/CNKD nay là form mẫu giấy đầy đủ: khối thông tin [01]–[27], Phần A 4 dòng ngành [28]–[31] + tổng [32] (thuế GTGT theo tỷ lệ gốc như HTKK), các dòng bắc cầu giảm thuế để ra số còn phải nộp và SỐ TIỀN THỰC NỘP của kỳ; Phần B/C; cam đoan và khối ký.
- Bộ xuất Excel chung của toàn app: cột tự giãn theo nội dung + số mang định dạng #,##0.## — hết lỗi hiện số kiểu 5.25E+08 và cắt chữ ở mọi file xuất (hàng hóa, khách hàng, hóa đơn, sổ sách, phụ lục).

## Đợt 147 — Nút "Tải PDF" cho tờ khai và sổ + sửa lỗi in ấn toàn app

- Thêm nút **Tải PDF** (nút chính) ở tờ khai và mọi sổ: đi qua hộp in của trình duyệt với khổ A4 khai sẵn (named @page), kèm hướng dẫn chọn "Lưu thành PDF" cho người không chuyên; sổ S2d 12 cột tự sang A4 nằm ngang. Nút In giấy dùng cùng đường nên bản in cũng đúng mẫu (trước đây in form thuế bị CSS in hóa đơn đè mất kẻ bảng và font chữ).
- **Vá lỗi toàn app:** một dấu `"` gõ thừa trong mã nguồn (sau thẻ </style> đầu tiên) bị trình duyệt đẩy thành ký tự đầu tiên của trang — khiến MỌI lần in qua vùng in của app (hóa đơn, tờ khai, sổ) lọt thêm một trang gần như trắng ở đầu, và trên màn hình có một dấu `"` nhỏ ở góc trên trái. Đã xóa tận gốc.

## Cách lên 2.43

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.
- Dữ liệu quán giữ nguyên tuyệt đối.
