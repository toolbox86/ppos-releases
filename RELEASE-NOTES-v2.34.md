# PPOS v2.34 — Vá kỹ tab Hàng hóa sau vòng kiểm thử chuyên sâu

Bản này là kết quả của **vòng kiểm thử chuyên sâu riêng tab Hàng hóa** do đội kiểm thử độc lập bên ngoài thực hiện trên v2.33 (28 ca trên bộ dữ liệu dựng đúng đặc điểm quán thật: 1.724 mặt hàng, trùng tên, quy đổi thùng, lô và hạn dùng). Đội kết luận ĐẠT CÓ ĐIỀU KIỆN với 4 lỗi và 16 quan sát nghiệp vụ; phía phát triển đã vá toàn bộ 4 lỗi và xử lý cả 16 quan sát theo cơ sở chủ sản phẩm đã chốt (Đợt 124), đội sẽ chạy vòng retest trên chính bản này.

**Đây là bản cập nhật trong app (OTA)** — không có file exe mới. Máy đang dùng bản 2.26 trở lên sẽ tự thấy thông báo phiên bản mới; khách mới tải exe v2.33 ở bản phát hành trước rồi mở app để cập nhật lên 2.34.

## Những gì đã sửa

- **Xuất danh sách hàng hóa trung thực đầy đủ.** Trước đây file xuất ghi cứng loại hàng và trạng thái bán, bỏ trống quy đổi/thuộc tính/tích điểm — xuất ra nhập lại ở máy khác sẽ làm sai dữ liệu lặng (dịch vụ thành hàng hóa bị trừ kho oan, hàng ngừng bán thành đang bán, mất quy đổi thùng). Nay cả hai đường xuất dùng chung một hàm dựng dòng đủ 21 cột; xuất → nhập lại giữ đúng mọi trường. Nút xuất cũng xuất theo đúng bộ lọc đang xem.
- **In tem mã vạch dùng được thật.** Trước đây tem chỉ in dãy số trang trí (không quét được), luôn in 60 hàng đầu bất kể đã chọn gì, mỗi hàng đúng 1 tem. Nay: in đúng hàng đã tick chọn, số tem theo tồn kho hoặc tự nhập, chọn khổ 35×22mm / 50×30mm / 80mm, mã vạch Code128 vẽ thật — quét lại bằng máy quét hoặc điện thoại ra đúng dãy số.
- **Bán hàng theo lô chuẩn ở mọi gói.** Khi bán, máy trừ lô hết hạn trước (FEFO) và chặn bán hàng đã hết hạn **ngay cả ở gói Miễn phí** đối với dữ liệu lô đã có — trước đây ở gói Miễn phí bán hàng theo lô làm tồn kho và tổng lô lệch nhau ngay từ đơn đầu tiên. Việc tạo và quản lý lô vẫn là tính năng của gói Pro trở lên như cũ. Hạn dùng hiển thị (tab Hàng hóa và banner ở màn Tổng quan) nay lấy theo **lô gần nhất còn hàng**, không còn theo phiếu nhập gần nhất.
- **Quyền xem hàng hóa tách khỏi quyền sửa.** Vai trò Chỉ xem và Người bán nay xem được danh sách hàng hóa để tra giá/tra tồn; đồng thời vá lỗ hổng: đường nhập Excel và các thao tác hàng loạt trước đây thiếu chốt quyền ở lớp xử lý — nay mọi đường ghi đều kiểm quyền catalog như nhau.
- **File mẫu Excel và nhập liệu.** Sửa dòng ví dụ quy đổi trong file mẫu (lệch 1 cột khiến người dùng điền theo ví dụ là hỏng); sheet Hướng dẫn ghi rõ: nhập lại cùng mã không đổi tồn kho, và hàng biến thể/số máy/lô tạo ở nút Thêm hàng. Báo cáo nhập bổ sung cảnh báo mã vạch trùng, dòng giá không phải số (đã nhập 0đ), mã trùng trong cùng file. Thêm hàng để trống mã thì máy **tự sinh mã SP…** để sau này nhập Excel cập nhật được.
- **Chuẩn hóa nhỏ.** Bộ lọc hạn tách riêng "Đã hết hạn" và "Sắp hết hạn"; ngưỡng "sắp hết" gán mặc định 5 cho hàng thiếu ngưỡng khi nhập; "nhóm ma" (nhóm không còn hàng) tự dọn khỏi gợi ý; thông báo chặn xóa hàng liệt kê mọi lý do; nhật ký sửa hàng ghi trường đã đổi và giá cũ → giá mới, nhật ký nhập Excel liệt kê mã đã thêm/cập nhật.

## Cách lên 2.34

- **Máy đang dùng bản 2.26 trở lên:** sẽ thấy thông báo **có phiên bản mới ngay trong phần mềm** — bấm **Cập nhật ngay** là xong, **không phải tải lại file cài đặt**.
- **Khách mới:** tải file **`PPOS.exe`** ở bản phát hành **v2.33**, mở phần mềm rồi bấm **Cập nhật ngay** khi máy báo có bản 2.34.

**Dữ liệu bán hàng của quán giữ nguyên tuyệt đối** — hàng hóa, hóa đơn, khách hàng, công nợ, nhân viên… không mất gì cả, không phải cài đặt hay thiết lập lại.

## Tải về

- **PPOS-app-v2.34.zip** — gói mã nguồn giao diện + máy chủ nội bộ (cho nhu cầu kỹ thuật).
- **PPOS-web-update-v2.34.zip** + **update-manifest.json** — gói cập nhật và bản tin phiên bản đã ký số. Bản tin v2.34 là cập nhật trong app thông thường (không bắt buộc tải exe), áp cho máy vỏ 2.26 trở lên.
- File cài đặt Windows **`PPOS.exe`** nằm ở bản phát hành **v2.33**.
