# UX exercise  NEO AI

## Sản phẩm: Vietnam Airlines  NEO AI Assistant

## 4 paths

### 1. AI đúng
- User hỏi hành lý xách tay nội địa hạng phổ thông  NEO trả lời 10kg + 1 phụ kiện nhỏ, kích thước 56x36x23cm
- User thấy thông tin rõ ràng, có số liệu cụ thể, có link nguồn chính thức để kiểm tra lại
- UI: câu trả lời có cấu trúc, có hyperlink, có câu soft-confirm "Thông tin này do NEO tổng hợp dựa trên quy trình hiện hành của Vietnam Airlines"

### 2. AI không chắc
- User hỏi về hành lý nhưng không nói rõ hành trình hoặc hạng vé  NEO hỏi ngược lại để lấy thêm context
- User hỏi ngoài scope như thời tiết  NEO từ chối trả lời và hiện nút "Gặp tư vấn viên" kèm hotline/email
- Vấn đề: khi user trả lời bổ sung ngắn gọn thì NEO phản hồi chậm, dễ mất context, không có typing indicator rõ; rating widget vẫn hiện dù vấn đề chưa được giải quyết

### 3. AI sai
- User hỏi "Chuyến bay VN123 Hà Nội đi Tokyo ngày 10/4/2026 khởi hành mấy giờ?"  NEO trả lời chuyến bay từ Đà Nẵng đi TP.HCM, sai hoàn toàn
- User chỉ phát hiện nếu đã biết thông tin mã chuyến bay đúng hoặc tự đi kiểm tra lại trên web
- Sửa: phải gõ lại câu hỏi hoặc tự thoát ra tra cứu thủ công / gọi hotline  ít nhất 3 bước
- Vấn đề: không có nút "Báo sai", không có confidence signal, không có disclaimer gắn với kết quả tra cứu cụ thể

### 4. User mất niềm tin
- Sau vài lần thấy NEO trả lời sai thông tin quan trọng như chuyến bay, user không còn tin kết quả tra cứu nữa
- Không có option "Chat với người thật" luôn hiển thị, fallback chỉ xuất hiện khi NEO tự nhận là không biết
- Không có fallback rõ ràng khi NEO trả lời sai nhưng vẫn tỏ ra tự tin

## Path yếu nhất: Path 3 + 4
- Khi AI sai, recovery flow mất quá nhiều bước và không có shortcut sửa lỗi
- Không có feedback loop rõ  user không thể báo sai và cũng không biết hệ thống có học từ correction hay không
- Không có exit/fallback persistent cho user mất niềm tin  hotline và nút gặp tư vấn viên chỉ xuất hiện theo điều kiện

## Gap marketing vs thực tế
- Marketing: "NEO là trợ lý ảo 24/7", "phản hồi nhanh, chính xác", "người đồng hành đáng tin cậy", có cá nhân hóa và hỗ trợ đa ngôn ngữ
- Thực tế: NEO trả lời tốt ở các câu hỏi phổ biến, nhưng với tình huống quan trọng như tra cứu chuyến bay vẫn có thể trả lời sai hoàn toàn; conversation context cũng còn rời rạc
- Gap lớn nhất: marketing nhấn mạnh độ chính xác và tin cậy, nhưng thực tế chưa có safeguard rõ khi AI sai  user dễ kỳ vọng gần như 100% đúng

## Sketch
(Ảnh đính kèm: `lab_mat_truoc.jpg`, `lab_mat_sau.jpg`)
- As-is: user hỏi  NEO trả lời  nếu đúng thì user tiếp tục, nếu sai thì phải tự phát hiện và tự sửa bằng cách hỏi lại hoặc ra ngoài tra cứu
- To-be: user hỏi  nếu confidence thấp hoặc dữ liệu quan trọng thì hiện trạng thái "Cần xác minh", kèm nút "Báo sai" + "Gặp tư vấn viên" + link nguồn chính thức
- To-be: khi user correction, hệ thống xác nhận "Đã ghi nhận phản hồi" để tạo cảm giác AI có học và giúp user yên tâm hơn
