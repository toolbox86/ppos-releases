# PPOS v2.51 — Vá bảo mật theo vòng kiểm thử độc lập (Đợt 160 + 161)

Bản này đóng các phát hiện của **vòng kiểm thử bảo mật v2.50** (QA Lead: ĐẠT CÓ ĐIỀU KIỆN).
Ghi chú chi tiết phục vụ đội kiểm thử đối chiếu khi retest; bản công khai rút gọn theo quy ước changelog.

## Đợt 160 — SEC-D-01 (S2, điều kiện đóng vòng số 1)
- Hub thêm cổng kiểm chứng từ tiền `moneyDocBad160`/`validateMoney160` (server.js): khi nhận ghi,
  hóa đơn / phiếu trả khách / phiếu trả NCC **mới hoặc có thay đổi** bị kiểm: qty từng dòng > 0;
  price/cost ≥ 0; total/refund ≥ 0 và ≤ tổng dòng hàng +1đ; các trường giảm giá/điểm/đã trả nợ ≥ 0;
  từng khoản thanh toán ≥ 0 và tổng thanh toán ≤ tổng chứng từ +1đ.
- Vi phạm → **422 `badamount`** + báo động trên máy quầy, dữ liệu máy chủ giữ nguyên.
  Áp cho cả đường ghi thường (mọi máy, kể cả máy quầy) và đường tự gộp khi lệch phiên bản
  (chứng từ mới sai → hủy cả lượt gộp). Dữ liệu cũ không thay đổi không bị kiểm lại.
- Luật đã đối chiếu 655 hóa đơn thật + 548 hóa đơn sao lưu cũ: 0 vi phạm.
- Tự kiểm: impl-dot160 20/20 (trước vá tái hiện đúng ca của đội: 200 + lưu thật).

## Đợt 161 — Các phát hiện còn lại (PO duyệt theo khuyến nghị; KHÔNG làm BitLocker theo quyết định của PO)
- **RISK-D9-01:** mã kiểm chứng ngắn của CA (16 ký tự đầu vân tay SHA-256) hiện ở màn ghép nối
  máy quầy (hubinfo thêm `caShort`) và trên trang cài chứng chỉ mới **`/ca`** cho điện thoại;
  QR tại quầy trỏ vào trang /ca thay vì tải thẳng file — đối chiếu khớp mới cài.
- **RISK-F1-01:** khóa TLS chuyển khỏi thư mục dữ liệu sang thư mục riêng `hub-tls` ngang hàng
  (shell truyền `tlsDir`; thiếu thì server tự suy từ thư mục cha của dataDir). Lần chạy đầu tự
  di trú nguyên bộ chứng chỉ cũ (giữ nguyên CA, điện thoại đã cài không phải cài lại).
- **SEC-F2-01:** phiên đăng nhập trong app chỉ có hiệu lực khi được cấp trong chính đợt chạy
  app đó sau khi nhập PIN đúng (mã ngẫu nhiên + hạn 12 giờ + dấu đợt chạy). Phiên lưu từ đợt
  chạy trước hoặc đặt sẵn trong localStorage không còn được nhận diện.
- **SEC-F3-01:** hộp thoại khôi phục sao lưu có cảnh báo riêng về bản quyền (gói/số mã hiện tại
  so với trong file) + tùy chọn "Giữ bản quyền hiện tại của máy này" (mặc định bật), ghi nhật ký
  theo lựa chọn.
- **OBS-A-02:** dữ liệu mẫu nhập nhà cung cấp đổi sang hư cấu. **OBS-A-03:** dọn chú thích chứa
  đường dẫn hồ sơ nội bộ khỏi mã nguồn phát hành. **OBS-D-01:** khóa chống dò PIN ở hub đếm thêm
  theo tài khoản (ngoài theo thiết bị). **OBS-D-03:** nút tải bản dự phòng (bản lưu chưa đồng bộ)
  phải nhập PIN quản lý như nút gộp.
- Không thay đổi: OBS-D-02 (giữ khóa ghép nối toàn cục), OBS-C (để đợt vỏ exe), OBS-A-01 (chờ xác nhận).

## Kiểm thử của dev
- impl-dot161: 19/19 · impl-dot160: 20/20 · audit-sec-hub: 21/21 · audit-sec-fp: 24/24
- impl-dot152: 21/21 · impl-dot153: 11/11 · impl-dot154: 12/12 · impl-dot156: 9/9 · impl-dot158: 5/5

## Gói phát hành
- `PPOS.exe` (bản cài Windows) · `PPOS-app-v2.51.zip` (9 file) · `PPOS-web-update-v2.51.zip`
  (OTA, min shell 2.26) · `update-manifest.json` — sha256 đối chiếu trên trang Release.
