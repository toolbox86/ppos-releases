# Chính sách bảo mật của PPOS

*Cập nhật lần cuối: 15/11/2026 — bản rút gọn đăng kèm trang phát hành. Bản đầy đủ: https://ppos-landing.vercel.app/chinh-sach-bao-mat*

## Cam kết cốt lõi

**PPOS không thu thập và không nhận dữ liệu kinh doanh của quán.** Hàng hóa, khách hàng của quán, hóa đơn, doanh số, tồn kho, công nợ, điểm thưởng, chấm công và lương chỉ nằm trên máy tính quầy của quán và các điện thoại bán chung trong mạng Wi-Fi nội bộ của quán. Đội PPOS không có hệ thống nào chứa dữ liệu bán hàng của quán và không xem được dữ liệu đó.

Dữ liệu của quán chỉ rời máy khi **chính bạn** chủ động xuất file sao lưu, gửi hóa đơn cho khách, hoặc gửi file cho bộ phận hỗ trợ để được giúp.

## PPOS kết nối internet khi nào, gửi gì

| Khi nào | Gửi dữ liệu gì | Mục đích |
|---|---|---|
| Đối chiếu bản quyền — tự động, tối đa 1 lần/ngày, chỉ ở máy quầy | Mã bản quyền của quán, dấu hiệu nhận dạng máy tính quầy (mã máy), tên quán, phiên bản phần mềm | Chống dùng chung mã giữa nhiều quán; thu hồi mã bị lộ |
| Kiểm tra phiên bản mới — tự động khi mở phần mềm và mỗi 24 giờ, chỉ ở máy quầy | Không gửi dữ liệu nào của quán — chỉ tải về bản tin phiên bản và gói cập nhật đã ký số từ trang phát hành | Thông báo và cài bản mới an toàn |
| Tài khoản PPOS & mua gói — chỉ khi bạn tự đăng ký/đăng nhập/đặt mua trong mục Bản quyền | Đúng những gì bạn điền: tên đăng nhập, tên quán, tên chủ quán, số điện thoại, thông tin đơn mua gói; mật khẩu chỉ lưu dạng băm | Cấp mã, kích hoạt gói, hỗ trợ |
| Mở liên kết ngoài — chỉ khi bạn bấm | Tùy thao tác: Zalo/Facebook hỗ trợ, xem bảng giá, ảnh mã VietQR khi mua gói (số tiền + mã đơn), gửi hóa đơn qua Zalo | Theo đúng thao tác của bạn |

Ngoài các trường hợp trên, phần mềm không gửi dữ liệu đi đâu khác: không quảng cáo theo dõi, không công cụ phân tích hành vi, không chia sẻ dữ liệu cho bên thứ ba vì mục đích thương mại.

## Sao lưu dữ liệu

Mọi file sao lưu (tự động mỗi ngày hoặc sao lưu thủ công) chỉ nằm trong thư mục trên máy tính quầy của quán. PPOS không tự gửi file sao lưu đi bất cứ đâu.

## Dữ liệu tài khoản/bản quyền lưu ở đâu

Hệ thống cấp mã và tài khoản PPOS đặt máy chủ tại Nhật Bản (nền tảng Supabase), kết nối mã hóa HTTPS, mật khẩu lưu dạng băm một chiều. Chỉ dữ liệu bản quyền và tài khoản (dữ liệu cơ bản, không nhạy cảm) được lưu tại đó — dữ liệu kinh doanh không rời máy của quán.

## Quyền của bạn & liên hệ

Bạn có quyền được biết, truy cập, chỉnh sửa, yêu cầu xóa dữ liệu tài khoản/bản quyền của mình và rút lại đồng ý theo Luật Bảo vệ dữ liệu cá nhân. Liên hệ: **phatnt056@gmail.com** · Zalo **0986 495 913** (Thứ 2 – Thứ 7, 8:00 – 20:00).

Bên chịu trách nhiệm: Nguyễn Tấn Phát (hộ kinh doanh) — người phát triển và phân phối PPOS.
