
# 5. Thực tiễn triển khai trong ngành Ngân hàng và Tài chính

Việc áp dụng Học máy vào quy trình giám sát giao dịch đã chuyển dịch từ các thử nghiệm đơn lẻ thành một thành phần cốt lõi trong cơ sở hạ tầng an toàn tài chính.

* **Hệ thống xác thực nâng cao của Visa:** Đây là một trong những mạng lưới ứng dụng AI lớn nhất thế giới. Mỗi giao dịch qua Visa được đánh giá dựa trên hơn **500 thuộc tính** khác nhau chỉ trong vòng **1 miligiây**. Hệ thống phân tích hồ sơ rủi ro của đơn vị chấp nhận thẻ, lịch sử hành vi của chủ thẻ và các dấu hiệu bất thường về mặt địa lý. Theo báo cáo từ Visa (2023), công cụ này giúp ngăn chặn thất thoát tài chính ước tính khoảng **27 tỷ USD** mỗi năm.

* **Mô hình phân tích đa lớp của PayPal:** PayPal sử dụng phương pháp tiếp cận kết hợp giữa các thuật toán Học sâu và quy trình kiểm soát của con người. Bằng cách nhận diện các mẫu hành vi vi mô trong khối lượng giao dịch khổng lồ, PayPal duy trì tỷ lệ gian lận ở mức **0,3%** tổng giá trị giao dịch, thấp hơn đáng kể so với mức trung bình của ngành (PayPal, 2021).

* **Ứng dụng tại thị trường Việt Nam:** Trong bối cảnh thanh toán không dùng tiền mặt bùng nổ, các tổ chức tài chính đang tích hợp **Sinh trắc học hành vi**. Hệ thống ML không chỉ xác thực qua mã OTP mà còn phân tích cách người dùng tương tác với thiết bị (tốc độ gõ phím, thói quen cầm điện thoại, vị trí truy cập thường xuyên) để phát hiện sớm các hành vi chiếm đoạt tài khoản.

# 6. Những thách thức trong triển khai và vận hành thực tế

Dù mang lại hiệu quả vượt trội, việc vận hành các mô hình ML trong môi trường ngân hàng vẫn đối mặt với những rào cản kỹ thuật và pháp lý nghiêm ngặt.

## 6.1. Sự mất cân bằng dữ liệu nghiêm trọng
Trong thực tế, số lượng giao dịch gian lận thường chiếm tỷ lệ rất nhỏ, dưới **0,1%** tổng tập dữ liệu. Theo nghiên cứu của Dal Pozzolo và cộng sự (2015), sự mất cân bằng này khiến thuật toán dễ ưu tiên lớp đa số (giao dịch hợp lệ), dẫn đến độ chính xác tổng thể (Accuracy) rất cao nhưng khả năng phát hiện gian lận thực tế (Recall) lại rất thấp. Các kỹ sư dữ liệu phải áp dụng kỹ thuật như **SMOTE** hoặc điều chỉnh **Hàm mất mát** để tối ưu hóa khả năng nhận diện các mẫu thiểu số.

## 6.2. Kiểm soát tỷ lệ báo động giả
Một thách thức lớn trong nghiệp vụ là việc cân bằng giữa an ninh và trải nghiệm khách hàng. Nếu mô hình quá nhạy, tỷ lệ **Báo động giả** tăng cao sẽ dẫn đến việc chặn giao dịch hợp lệ của người dùng. Điều này không chỉ gây phiền hà mà còn ảnh hưởng trực tiếp đến uy tín của ngân hàng và lòng tin của khách hàng.

## 6.3. Sự thay đổi đặc tính dữ liệu theo thời gian
Các phương thức tấn công luôn biến đổi để tìm ra kẽ hở mới. Hiện tượng này được gọi là **Concept Drift** (Gama et al., 2014), khi các đặc tính thống kê của hành vi gian lận thay đổi, khiến mô hình đã huấn luyện bị giảm hiệu suất. Do đó, hệ thống yêu cầu quy trình giám sát (Monitoring) và tái huấn luyện (Retraining) liên tục để thích nghi với các xu hướng gian lận mới.


# Tài liệu tham khảo

* Dal Pozzolo, A., Caelen, O., Waterschoot, R. A., & Bontempi, G. (2015). *Learned lessons in credit card fraud detection from a practitioner perspective*. Expert Systems with Applications, 42(10), 4928-4941.
* Gama, J., Žliobaitė, I., Bifet, A., Pechenizkiy, M., & Bouchachia, A. (2014). *A survey on concept drift adaptation*. ACM Computing Surveys (CSUR), 46(4), 1-37.
* PayPal. (2021). *PayPal Holdings, Inc. 2021 Annual Report*. Retrieved from PayPal Investor Relations.
* Visa. (2023). *Visa Advanced Authorization: Real-time fraud risk scoring*. Retrieved from Visa Newsroom.