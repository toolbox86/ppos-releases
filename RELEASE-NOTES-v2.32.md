# PPOS v2.32 — Sao lưu an toàn tuyệt đối, khôi phục chặt chẽ

Bản này khép vòng kiểm thử chuyên sâu **Sao lưu/Khôi phục** của một **đội kiểm thử độc lập bên ngoài**: vòng đầu phát hiện 21 lỗi, phía phát triển sửa toàn bộ (Đợt 119), vá thêm đường khởi động nối hub (Đợt 120) và các điểm chốt cuối (Đợt 121) — đội kiểm thử đã chạy lại toàn bộ và **chính thức gỡ điều kiện phát hành** (đủ 5/5 tiêu chí: 4 lỗi chặn + 4 lỗi mức cao đều đạt, nhóm sao lưu tự động chạy đủ, không hồi quy). Không thêm tính năng mới; đây là bản làm cho **sao lưu và khôi phục dữ liệu đáng tin tuyệt đối**.

## Những gì đã sửa

- **Ghi file sao lưu nguyên tử — hết file hỏng mang tên bản tốt.** Trước đây nếu mất điện hoặc đầy đĩa đúng lúc đang ghi, thư mục có thể còn một file cụt nhưng mang tên như bản sao lưu hợp lệ. Nay file chỉ xuất hiện khi đã ghi trọn vẹn; file tạm tồn dư được dọn khi phần mềm khởi động.
- **Bản sao lưu tự động là dữ liệu mới nhất trong ngày, không còn là ảnh chụp đầu ngày.** Bản tự động có ô riêng theo ngày và được làm mới mỗi 15 phút khi có thay đổi; sao lưu tay không còn chặn bản tự động cả ngày. Màn hình Sao lưu hiện rõ bản mới nhất chứa **dữ liệu tính đến mấy giờ**.
- **Điểm thưởng không bao giờ nhân đôi khi khôi phục.** Khôi phục một bản sao lưu đời cũ có sổ điểm từng làm điểm của khách bị cộng gấp đôi (đã kiểm chứng tới ~18 triệu đồng điểm ở dữ liệu lớn). Nay số điểm giữ đúng theo sổ thật ở mọi đường nạp và khôi phục — và chiều ngược lại, dữ liệu chưa có sổ điểm vẫn được chuyển đổi đúng.
- **Khôi phục dữ liệu bắt PIN quản lý + ghi nhật ký thay đổi tài khoản.** Trước đây ai mở được phần mềm cũng khôi phục được một file đã sửa tay, kể cả file làm thay đổi tài khoản/PIN. Nay khôi phục phải qua cổng PIN quản lý (sai 5 lần khóa 5 phút như mọi cổng PIN khác) và mọi thay đổi tài khoản đều vào nhật ký.
- **Bản cứu hộ cứu trọn quán lớn.** Giới hạn lưu trữ cũ (4 triệu ký tự) khiến quán nhiều dữ liệu cứu không hết. Nay bản cứu hộ chuyển sang kho lưu lớn — kiểm chứng cứu trọn một quán ~25 triệu ký tự dữ liệu.
- **Máy mới có lối khôi phục ngay từ đầu + điện thoại được báo khi quầy khôi phục.** Không còn cảnh máy mới cài phải tạo tài khoản tạm mới khôi phục được; khi máy quầy khôi phục dữ liệu, điện thoại đang nối được thông báo và nạp lại dữ liệu mới thay vì giữ phiên cũ lặng lẽ.
- **Mở phần mềm nối máy quầy không còn sập vì dữ liệu ca đời cũ.** Một bản ghi ca thiếu trường ở định dạng cũ từng làm phần mềm văng khi khởi động nối hub và báo sai thành lỗi kết nối. Nay dữ liệu được tự chữa ở mọi đường nạp, bản đã chữa được đẩy ngược lên máy quầy để mọi máy cùng sạch, và thông báo lỗi phân biệt rõ lỗi dữ liệu với lỗi kết nối.
- **Số bản giữ lại minh bạch.** Cơ chế dọn bản cũ luôn giữ lại bản vừa ghi trong lượt của nó (tối đa N bản + bản vừa ghi) — nhãn trong phần mềm và tài liệu nay ghi đúng câu chữ này thay vì "tối đa N".

## Cách lên 2.32

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**. Gói cập nhật mang cả phần giao diện lẫn máy chủ nội bộ đã sửa.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.

**Dữ liệu bán hàng của quán giữ nguyên tuyệt đối** — hàng hóa, hóa đơn, khách hàng, công nợ, nhân viên… không mất gì cả, không phải cài đặt hay thiết lập lại. Đội kiểm thử độc lập đã kiểm chứng đường nâng cấp giữ 100% số liệu, gồm cả kiểm tra số phiên bản ghi trong file sao lưu do bản mới tạo.

## Tải về

- **PPOS.exe** — bản Windows, bấm đúp chạy ngay, không cần cài đặt (cho khách mới hoặc máy ở bản cũ hơn 2.26).
- **PPOS-app-v2.32.zip** — gói mã nguồn giao diện + máy chủ nội bộ (cho nhu cầu kỹ thuật).
- **PPOS-web-update-v2.32.zip** + **update-manifest.json** — gói cập nhật và bản tin phiên bản đã ký số. Bản tin v2.32 là cập nhật trong app thông thường (không bắt buộc tải exe), áp cho máy vỏ 2.26 trở lên.

Giá không đổi: **Pro vĩnh viễn 3.990.000đ · Business vĩnh viễn 4.990.000đ** — mua một lần, dùng trọn đời, mọi cập nhật giữ nguyên gói.

© 2026 Nguyễn Tấn Phát — Phần mềm độc quyền, xem LICENSE trong repo này.
