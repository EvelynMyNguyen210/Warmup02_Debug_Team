# 3. Vì sao phương pháp phát hiện gian lận truyền thống không còn đủ hiệu quả
Trước khi machine learning được áp dụng rộng rãi, phần lớn ngân hàng sử dụng các **hệ thống dựa trên luật (rule-based systems)** để phát hiện giao dịch đáng ngờ. Các hệ thống này hoạt động bằng cách áp dụng những quy tắc được thiết lập sẵn bởi các chuyên gia phân tích.

Nếu một giao dịch vi phạm một trong các quy tắc đó, hệ thống sẽ gắn cờ giao dịch để kiểm tra thêm.

Một số quy tắc phổ biến trong các hệ thống truyền thống gồm:

- Giao dịch vượt quá một ngưỡng nhất định (ví dụ: trên 5.000 USD)
- Thanh toán được thực hiện từ quốc gia khác với vị trí thông thường của chủ thẻ
- Nhiều giao dịch liên tiếp xảy ra trong khoảng thời gian rất ngắn
  
Thoạt nhìn, cách tiếp cận này khá hợp lý. Tuy nhiên, trong thực tế nó gặp khó khăn khi phải đối phó với **những chiến thuật gian lận ngày càng thay đổi nhanh chóng.**

Hạn chế lớn nhất là **mô hình gian lận luôn biến đổi.** Những kẻ gian lận thường nhanh chóng điều chỉnh chiến thuật để vượt qua các quy tắc hiện có. Ví dụ, nếu hệ thống đánh dấu các giao dịch trên 5.000 USD là đáng ngờ, kẻ gian có thể chia nhỏ giao dịch thành nhiều khoản nhỏ hơn để tránh bị phát hiện. Vì các quy tắc này phải được thiết kế và cập nhật thủ công bởi chuyên gia, **hệ thống thường chỉ phản ứng sau khi các hình thức gian lận mới đã xuất hiện.**

Một vấn đề quan trọng khác là tỷ lệ **false positives cao**, tức là những giao dịch hợp lệ nhưng bị hệ thống nhầm là gian lận. Điều này gây bất tiện cho cả ngân hàng lẫn khách hàng. Chẳng hạn, khi một khách hàng đi du lịch nước ngoài và thực hiện thanh toán tại một quốc gia mới, hệ thống có thể hiểu nhầm đó là hoạt động bất thường và tạm khóa thẻ. Dù mục tiêu là bảo vệ tài khoản, những tình huống như vậy có thể ảnh hưởng đáng kể đến trải nghiệm người dùng.

Các nghiên cứu trong lĩnh vực phát hiện gian lận tài chính cũng chỉ ra rằng các hệ thống dựa trên luật cố định thường gặp khó khăn khi xử lý **khối lượng dữ liệu giao dịch lớn** và các mô hình gian lận phức tạp, nơi hành vi gian lận có thể rất tinh vi và khó mô tả bằng các ngưỡng cố định.

Chính vì những hạn chế này, nhiều tổ chức tài chính đang chuyển sang sử dụng **machine learning**, cho phép hệ thống học trực tiếp từ dữ liệu giao dịch, phát hiện các mẫu hành vi phức tạp và thích nghi tốt hơn với những chiến thuật gian lận mới.

Để chỉ ra sự khác biệt giữa rule-based systems và machine-learning thì bạn hãy nhìn vào bảng sau:

| Khía cạnh | Hệ thống phát hiện gian lận dựa trên luật (Rule-based) | Hệ thống phát hiện gian lận sử dụng Machine Learning |
|------|------|------|
| **Ra quyết định** | Dựa trên logic cố định “Nếu X thì Y”, quyết định rõ ràng nhưng thường cứng nhắc | Phân tích nhiều yếu tố để đưa ra quyết định linh hoạt dựa trên dữ liệu theo thời gian thực |
| **Khả năng thích ứng** | Các quy tắc phải được cập nhật thủ công khi xuất hiện chiến thuật gian lận mới | Liên tục học từ dữ liệu và tự điều chỉnh khi mô hình gian lận thay đổi |
| **Khả năng giải thích** | Dễ giải thích cho các bên liên quan vì quyết định thường gắn với một quy tắc cụ thể | Không phải lúc nào cũng trực quan, nhưng nhiều hệ thống có công cụ giúp giải thích quyết định của mô hình |
| **Độ chính xác và hiệu năng** | Hiệu quả với các mẫu gian lận đã biết nhưng dễ tạo ra nhiều cảnh báo nhầm (false positives) | Độ chính xác cao hơn, giảm số giao dịch hợp lệ bị từ chối và giảm bỏ sót gian lận |
| **Khả năng mở rộng** | Trở nên khó quản lý khi số lượng giao dịch và quy tắc tăng lên | Có thể mở rộng tốt và xử lý khối lượng dữ liệu lớn mà không cần tăng độ phức tạp của quy tắc |
| **Ảnh hưởng đến trải nghiệm khách hàng** | Các quy tắc quá chặt có thể khiến khách hàng hợp lệ bị chặn giao dịch, gây khó chịu | Cân bằng giữa bảo mật và trải nghiệm giao dịch mượt mà hơn cho khách hàng đáng tin cậy |
| **Mức độ sẵn sàng trước gian lận** | Mang tính phản ứng: thường chỉ xử lý sau khi mối đe dọa đã xuất hiện | Mang tính chủ động: có khả năng thích nghi với các chiến thuật gian lận mới |
<p align="center">
   <img src= style="margin: 0 auto; display: block;"><br/>
    <em>Bảng 3.1. So sánh giữa hệ thống phát hiện gian lận truyền thống dựa trên Rule-based và hệ thống sử dụng Machine Learning
  ; nguồn: <a href="https://www.signifyd.com/blog/rules-based-vs-machine-learning-fraud-protection/">Channing Lovett</a> </em>
 </p></em>
 </p>

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

# 7. Tương lai của AI: Khi "lá chắn" của ngân hàng trở nên thông minh hơn

Công nghệ không bao giờ đứng yên, và những kẻ lừa đảo không còn dùng mánh khóe thủ công nữa. Để ngăn chặn việc này, các ngân hàng đang đặt cược vào những lá chắn mới thông minh hơn. Tương lai không nằm ở việc chạy theo đuôi tội phạm, mà là những hệ thống AI có khả năng tự học, đoán trước rủi ro và hiểu dữ liệu ở một mức độ hoàn toàn mới.

## 7.1. Generative AI và Dữ liệu mô phỏng

Một trong những bài toán khó nhất khi xây dựng mô hình Machine Learning phát hiện gian lận là: dữ liệu gian lận thật sự thường rất hiếm. Trong thực tế, phần lớn giao dịch đều hợp lệ, còn những trường hợp gian lận chỉ chiếm một tỷ lệ rất nhỏ. Điều này khiến mô hình khó học được đầy đủ các dấu hiệu của hành vi lừa đảo.

Khi không có đủ ví dụ để học, hệ thống AI rất dễ bỏ sót những kiểu gian lận mới hoặc tinh vi hơn. Và đây chính là lúc Generative AI phát huy giá trị. Một trong những hướng tiếp cận nổi bật là sử dụng GANs (Generative Adversarial Networks) để tạo ra các tập dữ liệu mô phỏng có đặc điểm gần giống với dữ liệu gian lận thật. Thay vì phải chờ thêm các vụ gian lận xảy ra trong thực tế, chúng ta có thể chủ động tạo ra nhiều kịch bản gian lận khác nhau để huấn luyện mô hình.

Nhờ vậy, hệ thống phát hiện gian lận của ngân hàng có thể được tập luyện với hàng loạt tình huống giả lập, từ những chiêu trò phổ biến cho đến các gian lận phức tạp. Việc tiếp xúc với nhiều kịch bản như vậy giúp mô hình học được các tín hiệu bất thường tốt hơn, từ đó nâng cao khả năng phát hiện và thích ứng khi triển khai trong môi trường thực tế.

<p align="center">
    <img src="https://github.com/EvelynMyNguyen210/Warmup02_Blog1/blob/main/Collection_Blog2/7_1_Generative_AI.png" style="margin: 0 auto; display: block;"><br/>
    <em>Hình 7.1. Generative AI và Dữ liệu mô phỏng </em>
</p>

## 7.2 Federated Learning: Hợp tác giữa các tổ chức nhưng vẫn bảo vệ quyền riêng tư

Khi một chiêu trò lừa đảo trót lọt ở ngân hàng này, nó sẽ sớm xuất hiện ở ngân hàng khác. Tuy nhiên, việc các tổ chức tài chính chia sẻ dữ liệu thô của khách hàng cho nhau là vi phạm nghiêm trọng các quy định về quyền riêng tư.

Federated Learning (học tập liên kết) là lời giải hoàn hảo. Các ngân hàng giữ nguyên dữ liệu nhạy cảm ở hệ thống nội bộ, và chỉ chia sẻ các mẫu hành vi gian lận lên một mạng lưới chung. Từ đó cả mạng lưới cùng thông minh lên mà dữ liệu cá nhân của người dùng vẫn được bảo mật.

<p align="center">
    <img src="https://github.com/EvelynMyNguyen210/Warmup02_Blog1/blob/main/Collection_Blog2/7_2_Federated_Learning.png" style="margin: 0 auto; display: block;"><br/>
    <em>Hình 7.1. Federated Learning</em>
</p>

## 7.3 Sự kết hợp giữa con người và AI

Một trong những hiểu lầm lớn nhất về AI là nó xuất hiện để thay thế con người. Nhưng trong lĩnh vực phát hiện gian lận, sự thật lại hoàn toàn ngược lại. Xu hướng tương lai sẽ là những đội ngũ mà con người và AI cùng làm việc song song với nhau.

Việc phát hiện gian lận hiếm khi là chuyện trắng đen rõ ràng. AI có thể nhanh chóng phát hiện các hành vi đáng ngờ chỉ trong tích tắc, nhưng để kết luận đó có thực sự là gian lận hay không thì vẫn cần đến sự đánh giá của con người. Có những yếu tố như khác biệt văn hóa, bối cảnh lịch sử của khách hàng, hay những trường hợp đặc biệt mà không một thuật toán nào có thể hiểu hết nếu chỉ đứng một mình.

Đây là cách mà hai vai trò này bổ trợ cho nhau:

- AI xử lý ở quy mô lớn: lọc qua hàng triệu sự kiện và nhanh chóng làm nổi bật những trường hợp đáng để điều tra.

- Con người mang lại bối cảnh: không chỉ nhìn vào dữ liệu, mà còn hiểu được ý định, mối quan hệ và những tình huống ngoại lệ mà máy móc chưa hiểu hết.

- Khi kết hợp lại giúp cho hành động nhanh hơn: AI giúp giảm bớt các cảnh báo sai, để các chuyên viên phân tích có thêm thời gian tập trung vào những vụ việc phức tạp thay vì mất thời gian trong các cảnh báo lặp đi lặp lại.

Hãy hình dung AI như một trợ lý giúp phân loại nhanh nhất có thể dành cho các đội chống gian lận, nó ngay lập tức chỉ ra những trường hợp rủi ro, để các chuyên viên dồn sức vào đúng nơi cần thiết nhất.

Cách tiếp cận kết hợp này còn tạo ra một vòng lặp phản hồi liên tục: mỗi vụ gian lận được xác nhận giúp mô hình AI học tốt hơn, và mỗi lần báo động nhầm cũng dạy nó biết nên tránh điều gì trong tương lai. Theo thời gian, cả máy và con người đều trở nên chính xác và hiệu quả hơn.

*Cuộc chiến chống gian lận tài chính vốn dĩ là một cuộc rượt đuổi không hồi kết. Khi những kẻ lừa đảo ngày càng tinh vi, các ngân hàng không thể mãi phòng thủ bằng những bộ quy tắc cứng nhắc và cũ kỹ. Sự dịch chuyển sang Machine Learning không chỉ là một bước tiến công nghệ, mà đã trở thành vũ khí sống còn giúp các tổ chức tài chính chuyển từ thế bị động sang chủ động dự báo rủi ro. Tất nhiên, việc vận hành AI trong thực tế vẫn còn đó những bài toán khó về cân bằng dữ liệu hay kiểm soát tỷ lệ báo động giả. Thế nhưng, với sự xuất hiện của Generative AI mô phỏng dữ liệu, mạng lưới chia sẻ an toàn Federated Learning, bức tranh bảo mật đang sáng sủa hơn bao giờ hết. Quan trọng nhất, công nghệ tiến lên không phải để loại bỏ chúng ta. Trong tương lai, AI sẽ đóng vai trò là trợ thủ đắc lực, còn con người mới là người quyết định cuối cùng, cùng nhau xây dựng một hệ sinh thái thanh toán an toàn, mượt mà và đáng tin cậy.*

# Tài liệu tham khảo

* Dal Pozzolo, A., Caelen, O., Waterschoot, R. A., & Bontempi, G. (2015). *Learned lessons in credit card fraud detection from a practitioner perspective*. Expert Systems with Applications, 42(10), 4928-4941.
* Gama, J., Žliobaitė, I., Bifet, A., Pechenizkiy, M., & Bouchachia, A. (2014). *A survey on concept drift adaptation*. ACM Computing Surveys (CSUR), 46(4), 1-37.
* PayPal. (2021). *PayPal Holdings, Inc. 2021 Annual Report*. Retrieved from PayPal Investor Relations.
* Visa. (2023). *Visa Advanced Authorization: Real-time fraud risk scoring*. Retrieved from Visa Newsroom.
* Bolton, R. J., & Hand, D. J. (2002). Statistical fraud detection: A review. Statistical Science, 17(3), 235–255.
* Ngai, E. W. T., Hu, Y., Wong, Y. H., Chen, Y., & Sun, X. (2011). The application of data mining techniques in financial fraud detection. Decision Support Systems, 50(3), 559–569.
* Phua, C., Lee, V., Smith, K., & Gayler, R. (2010). A comprehensive survey of data mining-based fraud detection research. arXiv preprint arXiv:1009.6119.
* Okafor, G., Akhuemonkhan, E., Njoku, C., Gachui, E., Naibe, I., & Diala, A. K. (2025). The future of generative artificial intelligence (AI) in fraud detection analysis. International Journal of Management & Entrepreneurship Research, 7(4), 294–298. https://doi.org/10.51594/ijmer.v7i4.1875
* Fraud Detection Software. (2026, January 6). The future of AI in fraud detection: Trends & risks. https://frauddetectionsoftware.co/blog/future-ai-fraud-detection