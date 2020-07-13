## Multisite
**Check_MK** tận dụng sự trực quan của multisite web **GUI**(The graphical user interface) để hiển thị thông tin giám sát. Multisite dựa trên livestatus vì thế nó cực kỳ nhanh và nhanh và nhạy trong các cài đặt lớn.

Multisite mang đến nhiều tính năng như:
- Lượt xem xác định của người dùng.
- Hỗ trợ giám sát phân tán qua livestatus
- Tùy chỉnh sidebar với nội dung động
- Tự động hóa và dịch vụ Web (API)
- Bảng điều khiển (Dashboards) 
- Localization

**Views**

Multisite cho phép mỗi người dùng tùy chỉnh các chế độ xem dựng sẵn hoặc các chế độ xem dựng sẵn hoặc tạo các chế độ xem hoàn toàn mới. Điều này được thực hiện trong GUI bằng cách kết hợp linh hoạt các nguồn dữ liệu, bố cục, bộ lọc, sắp xếp, nhóm, vẽ theo cột và xem liên kết. Ý tưởng đằng sau là, các quản trị viên của hệ thống giám sát sẽ có thể tạo các chế độ xem tùy chỉnh cho người dùng hoặc khách hàng của họ, trong khi những người được trình bày một GUI càng đơn giản các tốt.

Các yếu tố của chế độ xem như bố cục, bộ lọc, v.v có thể được mở rộng thông qua Python bằng cách sử dụng khái niệm Plugin

**Distributed monitoring** (giám sát phân tán)-

Giám sát phân tán là cực kỳ hữu ích trong nhiều tình huống. **Check_MK** cho phép xem dữ liệu tập chung cũng như sao chép dữ liệu đến các trang web từ xa.