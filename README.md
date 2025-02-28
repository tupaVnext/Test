export HTTP_PROXY=http://127.0.0.1:1087

export HTTPS_PROXY=http://127.0.0.1:1087

export NO_PROXY=localhost,127.0.0.1,LOCALHOST

Cả hai đều trông giống như có điều gì đó làm hỏng kết nối trước khi nó được chuyển đổi thành websocket; nhưng vì có rất nhiều lý do có thể khiến điều này xảy ra và lỗi cũng khác nhau nên rất khó để nói.

Một số suy nghĩ về những điều có thể xảy ra sai sót:

Tường lửa/proxy không hỗ trợ đúng chuẩn web socket - có thể xác nhận bằng cách sử dụng trang web nào đó như https://websocketstest.com/ (theo như tôi biết, trang web đó kiểm tra qua HTTP có lẽ là tốt nhất, vì proxy/tường lửa kém có thể sẽ kiểm tra/làm hỏng các kết nối không được mã hóa).

Proxy đang chuyển tiếp lưu lượng đến localhost - điều này nghe có vẻ hơi điên rồ, nhưng một người dùng ở trên đã báo cáo rằng việc bỏ qua proxy cho localhost đã khắc phục được sự cố. Nếu chúng ta đang lắng nghe trên localhost và proxy không nằm trên máy, tôi không chắc nó có thể kết nối lại được không. Một cách có thể để kiểm tra điều này là chỉ cần tạo một .darttập lệnh Hello World và đặt một điểm dừng trong đó và gỡ lỗi - chúng ta sử dụng cùng một loại kết nối ổ cắm web đến localhost để gỡ lỗi so với VM chuẩn (điều này có thể loại bỏ bất kỳ sự cố cụ thể nào của flutter).

Cũng có thể có một sự phức tạp khi chuyển tiếp cổng đến thiết bị. Tôi không chắc nó hoạt động như thế nào với Trình giả lập, nhưng tôi tin rằng đối với một thiết bị thực, một cổng được chuyển tiếp từ máy chủ cục bộ đến thiết bị - nếu điều này cũng xảy ra với trình giả lập, thì có khả năng proxy/tường lửa cũng có thể xâm nhập vào đó. Tuy nhiên, có thể phức tạp hơn để xác nhận điều này, vì vậy tốt hơn là nên thử những thứ dễ kiểm tra hơn trước.
