## Livestatus 
* Là một phần quan trọng trong Check_MK. Nó giúp Check_MK truy xuất dữ liệu một cách nhanh chóng
* Livestatus sẽ sử dụng Socket để lấy dữ liệu để trả lời truy vấn do đó tốc độ truy vấn của nó không còn phụ thuộc vào tốc độ I/O như là lưu dữ liệu trong File.
* Khi truy xuất dữ liệu bằng Command line thì Livestatus sẽ phân biệt chữ hoa chữ thường.
* Livestatus sẽ sử dụng Socket để check dữ liệu do đó công việc được phân đều cho các CPU
