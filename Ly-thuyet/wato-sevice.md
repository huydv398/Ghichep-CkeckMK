# Hiểu và cấu hình dịch vụ

## 1. Giới thiệu

Service thực chất là "substance-nội dung" của một hệ thống giám sát. Mỗi cái đại diện cho một mắt xích quan trọng trong hệ thống giám sát CNTT phức tạp của bạn. Tính hữu ích hoàn toàn tăng hay giảm tùy thuộc vào mức độ chính xác và hữu ích của các dịch vụ đã được cấu hình. Cuối cùng, Việc giám sát nên thông báo một cách đáng tin cậy bất khi nào một vấn đề trở nên rõ ràng ở đâu đó, nhưng chắc chắn cũng nên giảm thiểu các thông báo sai hoặc không các tác dụng.

CheckMK chứng tỏ sức mạnh lớn nhất của nó khi cấu hình service- Nó sở hữu một hệ thống không thể so sánh và vô cùng mạnh mẽ phát hiện tự động và cấu hình các service cảnh báo. Với CheckMK, không cần xác định từng dịch vụ thông qua các mẫu và phân tán riêng lẻ. CheckMK có thẻ tự đọng và đáng tin cậy phát hiện danh sách các dịch vụ được theo dõi. Nó đảm bảo những thay đổi hàng ngày trong một trung tâm xử lý luôn được bảo vệ kịp thời và không có dịch vụ quan trọng nào không được giám sát.

Cách thức hoạt động: Kiểm tra tham số/ các ngưỡng cảnh báo cho các dịch vụ riêng lẻ - được cấu hình độc lập thông qua các rule. 

## 2. Host service in WATO 
### 2.1 Kết hợp một máy chủ mới

Khi thêm một máy chủ mới trong WATO, bước tiếp theo là gọi ra danh sách các dịch vụ. Với hành động này, việc phát hiện dịch vụ trong lần đầu tiên cho máy chủ. 