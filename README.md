Có, bạn có thể cài đặt `FirebaseAnalytics` thủ công bằng cách tải xuống gói cần thiết và đặt vào đúng thư mục mà CocoaPods yêu cầu. Dưới đây là các bước chi tiết:

---

### **Cách cài đặt FirebaseAnalytics thủ công**
#### **Bước 1: Tải tệp FirebaseAnalytics thủ công**
Do lỗi `curl (35) LibreSSL`, bạn có thể tải `FirebaseAnalytics` bằng trình duyệt hoặc một lệnh `curl` khác.

1. **Mở trình duyệt** và truy cập liên kết sau:
   - [FirebaseAnalytics-11.4.0.tar.gz](https://dl.google.com/firebase/ios/analytics/edf73aefd77661bd/FirebaseAnalytics-11.4.0.tar.gz)
   - Lưu tệp `.tar.gz` vào thư mục `Downloads`.

2. **Hoặc dùng `curl` với TLS 1.2 (nếu có)**:
   ```sh
   curl --tlsv1.2 -o ~/Downloads/FirebaseAnalytics-11.4.0.tar.gz https://dl.google.com/firebase/ios/analytics/edf73aefd77661bd/FirebaseAnalytics-11.4.0.tar.gz
   ```

---

#### **Bước 2: Đặt vào thư mục cache của CocoaPods**
Sau khi tải xong, bạn cần đặt tệp vào thư mục cache của CocoaPods:

1. **Tạo thư mục cache CocoaPods**:
   ```sh
   mkdir -p ~/Library/Caches/CocoaPods/Pods/Release/FirebaseAnalytics/11.4.0-abcdefg
   ```

   Lưu ý: `11.4.0-abcdefg` có thể thay đổi dựa vào phiên bản Firebase, hãy kiểm tra chính xác.

2. **Di chuyển tệp vào cache**:
   ```sh
   mv ~/Downloads/FirebaseAnalytics-11.4.0.tar.gz ~/Library/Caches/CocoaPods/Pods/Release/FirebaseAnalytics/11.4.0-abcdefg/FirebaseAnalytics-11.4.0.tar.gz
   ```

---

#### **Bước 3: Chạy lại `pod install`**
Sau khi đã đặt tệp vào thư mục cache, chạy lại lệnh:

```sh
pod install --verbose
```

---

### **Nếu vẫn lỗi, thử cách thêm FirebaseAnalytics vào project thủ công**
Nếu cách trên không được, bạn có thể thêm FirebaseAnalytics vào project iOS của Flutter thủ công:

1. **Mở `ios/Podfile` và thêm dòng sau vào trong `target`**:
   ```ruby
   pod 'Firebase/Analytics'
   ```
   
2. **Chạy lệnh sau để cài đặt lại pods**:
   ```sh
   cd ios
   pod install --repo-update
   ```

Nếu vẫn gặp lỗi, bạn có thể thử xóa hoàn toàn cache của CocoaPods trước khi chạy lại:

```sh
rm -rf ~/Library/Caches/CocoaPods
rm -rf Pods
rm -rf ios/Podfile.lock
pod install --verbose
```

---

### **Tóm tắt giải pháp**
1. **Tải FirebaseAnalytics thủ công** từ Google.
2. **Đặt tệp vào thư mục cache của CocoaPods**.
3. **Chạy lại `pod install`**.
4. Nếu vẫn lỗi, **thêm FirebaseAnalytics vào Podfile thủ công** và chạy `pod install --repo-update`.

Bạn thử cách trên xem có khắc phục được không nhé! 🚀
