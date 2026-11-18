# PPOS v2.33 — Ghi nợ cho mọi gói, khép vòng kiểm thử tổng thể

Bản này khép **vòng kiểm thử tổng thể** của đội kiểm thử độc lập bên ngoài (~330 ca kiểm thử + 74 ca bổ sung theo gói): vòng đầu kết luận chưa đạt với 16 lỗi, phía phát triển sửa toàn bộ (Đợt 122), đội chạy lại và chạy bổ sung bằng khóa thật — **kết luận cuối: ĐẠT PHÂN PHỐI**, đối chiếu 5 sổ (két, điểm, kho, thuế, hóa đơn) khớp tuyệt đối. Kèm theo là đợt vá chốt cuối (Đợt 123) cho các quan sát nghiệp vụ của đội.

## Điểm mới nổi bật

- **Gói Miễn phí nay ghi nợ – thu nợ được.** Trước đây ghi nợ là tính năng của gói Pro trở lên; nay quán dùng gói Miễn phí cũng bán ghi nợ và thu nợ cho mọi khách hàng bình thường. Chủ quán và nhân viên bán hàng đều thu nợ được (vai trò Chỉ xem thì không), và **mỗi lần thu nợ đều có phiếu và dòng lịch sử tra lại được** như các gói trả phí. Các tính năng khác của từng gói giữ nguyên.

## Những gì đã sửa và chuẩn hóa

- **In hóa đơn từ mẫu cũ không còn thiếu nội dung.** Mẫu in được chuyển đổi từ các bản PPOS đời cũ có trường hợp chỉ còn tiêu đề và chân trang — hóa đơn in ra thiếu toàn bộ dòng hàng và tổng tiền. Nay mẫu cũ được dựng lại đầy đủ khi chuyển đổi, kể cả những mẫu đã bị chuyển thiếu từ trước cũng được chữa lại khi mở phần mềm. Nhãn cách trả/cách hoàn tiền trên chứng từ đời cũ cũng hiển thị đúng, không còn chữ lạ.
- **Dữ liệu gốc hàng hóa được chốt an toàn.** Điện thoại của nhân viên bán hàng không còn đường nào sửa giá, đổi tên hay xóa hàng hóa qua kênh đồng bộ — chỉ chủ quán/quản lý hoặc người được cấp quyền hàng hóa mới sửa được. Việc trừ tồn kho khi bán hàng qua điện thoại không bị ảnh hưởng.
- **Thuế tạm tính bù trừ trong năm ở cả hai vế.** Quý bị lỗ được bù vào các quý lãi trong cùng năm — cả vế doanh thu lẫn vế thu nhập — nên số tạm tính sát với quyết toán năm, quán không nộp thừa như cách tính từng quý riêng lẻ trước đây.
- **Ngày phép và bảng lương đếm cùng một kiểu.** Ngày phép tính theo ngày làm việc (trừ ngày nghỉ tuần của quán) ở mọi nơi — quỹ phép, bảng công, bảng lương tháng không còn lệch nhau; **ngày lễ nằm trong kỳ nghỉ phép không bị trừ quỹ phép**. Kỳ lương đã khóa giữ nguyên số đã chốt.
- **Nhãn tỷ lệ thuế GTGT hiển thị đúng mức đang áp.** Khi đang áp mức giảm 20% theo quy định, Sổ thuế hiện đúng **0,8%** thay vì 1% như trước (số tiền thuế vốn đã tính đúng 0,8%, chỉ nhãn hiển thị được sửa cho khớp).
- **Cùng các chuẩn hóa nhỏ:** đăng nhập được ghi nhật ký đầy đủ ở cả máy quầy và điện thoại; nhập Excel có tiêu đề lạ sẽ dừng và hướng dẫn thay vì nhập sai lặng lẽ; báo cáo nhập liệt kê dòng bị bỏ kèm lý do; thông báo có chấm đỏ khi phiếu hỗ trợ được trả lời; giờ trong nhật ký thống nhất theo giờ máy quầy; dữ liệu chỉ được nhận khi đã ghi xuống đĩa thành công.

## Cách lên 2.33

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**. Gói cập nhật mang cả phần giao diện lẫn máy chủ nội bộ đã sửa.
- **Khách mới / máy đang ở bản cũ hơn:** tải file **`PPOS.exe`** bên dưới, đóng hẳn PPOS rồi mở file mới.

**Dữ liệu bán hàng của quán giữ nguyên tuyệt đối** — hàng hóa, hóa đơn, khách hàng, công nợ, nhân viên… không mất gì cả, không phải cài đặt hay thiết lập lại. Đội kiểm thử độc lập đã kiểm chứng đường nâng cấp giữ 100% số liệu.

## Tải về

- **PPOS.exe** — bản Windows, bấm đúp chạy ngay, không cần cài đặt (cho khách mới hoặc máy ở bản cũ hơn 2.26).
- **PPOS-app-v2.33.zip** — gói mã nguồn giao diện + máy chủ nội bộ (cho nhu cầu kỹ thuật).
- **PPOS-web-update-v2.33.zip** + **update-manifest.json** — gói cập nhật và bản tin phiên bản đã ký số. Bản tin v2.33 là cập nhật trong app thông thường (không bắt buộc tải exe), áp cho máy vỏ 2.26 trở lên.

Giá không đổi: **Pro vĩnh viễn 3.990.000đ · Business vĩnh viễn 4.990.000đ** — mua một lần, dùng trọn đời, mọi cập nhật giữ nguyên gói. Gói Miễn phí 0đ nay đã gồm ghi nợ – thu nợ.

© 2026 Nguyễn Tấn Phát — Phần mềm độc quyền, xem LICENSE trong repo này.
