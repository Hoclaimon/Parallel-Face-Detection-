Đề tài nhóm em thực hiện là tối ưu phát hiện khuôn mặt dựa trên thuật toán Cascade-Classifier (một cải tiến của thuật toán Viola-jones) bằng lập trình song song sử dụng GPU và so sánh hiệu năng với lập trình tuần tự.

Lý do chọn thuật toán Cascade-classifier:
-	Nhẹ và hiệu quả về mặt tài nguyên: thuật toán này sử dụng các bộ lọc haar-like để trích xuất các đặc trưng từ hình ảnh. Các bộ lọc này có thể được tính toán nhanh chóng và không đòi hỏi nhiều tài nguyên, khiến cho nó trở nên nhẹ và hiệu quả hơn về mặt tài nguyên, có thể hoạt động nhanh chóng ngay cả trên các thiết bị có cấu hình thấp.
-	Có thể hoạt động nhanh chóng: thuật toán sử dụng một phương pháp phân loại phân cấp để phát hiện khuôn mặt. Phương pháp này bắt đầu bằng một bộ lọc haar-like đơn giản và tiếp tục tinh chỉnh các bộ lọc cho đến khi phát hiện khuôn mặt. Điều này giúp thuật toán Cascade-classifier có thể phát hiện khuôn mặt nhanh chóng.
-	Tỉ lệ chính xác khá tốt: tỉ lệ chính xác phụ thuộc vào nhiều yếu tố, như: độ phức tạp của khuôn mặt, điều kiện ánh sáng, góc độ của khuôn mặt,... Thuật toán này thường đạt được tỉ lệ chính xác khoảng 90% đối với các khuôn mặt với điều kiện ánh sáng tốt và góc độ thuận lợi, đối với các trường hợp xấu thì có thể giảm xuống dưới 80%. Tuy nhiên, có thể cải thiện bằng cách sử dụng các bộ lọc haar-like phức tạp hơn có thể phát hiện được các đặc trừng tinh vi hơn trên khuôn mặt.

Mô tả:
-	Input: một tấm ảnh đầu vào, mô hình Haar Cascade Classifier đã train sẵn.
-	Output: trả ra tấm ảnh đầu vào có bounding box ở các khuôn mặt mà hệ thống nhận diện được.
  
Lý do cần lập trình song song để tối ưu:
-	Ứng dụng sẽ chạy chậm nếu lập trình tuần tự.
-	Nhu cầu xử lý dữ liệu lớn, ảnh có độ phân giải cao, video, streaming video trong thời gian thực.

## Cài đặt chương trình
1. Tạo 1 folder chứa môi trường ảo (venv) bằng câu lệnh : python -m venv <Tên folder bạn muốn>
2. cd đến folder đó 
3. gitclone 
4. Chạy câu lệnh : Script\activate.bat
5. cd đến folder project
6. pip install -r requierments.txt
## Chạy chương trình
1. python serial.py haarcascade_frontalface_alt.xml input1.jpg out_se_1.jpg (chạy code tuần tự)
2. python parallel.py haarcascade_frontalface_alt.xml input1.jpg out_pa_1.jpg (chạy code song song)
