Lỗi này thường liên quan đến vấn đề SSL khi kết nối với nguồn của CocoaPods. Dưới đây là một số cách khắc phục:

---

### 1. **Cập nhật CocoaPods**
Đầu tiên, hãy thử cập nhật CocoaPods lên phiên bản mới nhất:
```sh
sudo gem install cocoapods
pod repo update
```

Sau đó, chạy lại:
```sh
pod install --verbose
```

---

### 2. **Kiểm tra OpenSSL**
Kiểm tra xem OpenSSL có đang bị lỗi hoặc không được cập nhật không:
```sh
brew update
brew install openssl
brew link --force --overwrite openssl
```

---

### 3. **Sử dụng HTTPS thay vì TLSv1**
Có thể CocoaPods vẫn đang sử dụng giao thức cũ không hỗ trợ TLSv1. Hãy thử đổi URL của CocoaPods:
```sh
pod repo remove trunk
pod repo add trunk https://cdn.cocoapods.org/
pod install
```

Hoặc chuyển sang dùng nguồn GitHub:
```sh
pod repo remove master
pod repo add master https://github.com/CocoaPods/Specs.git
pod install
```

---

### 4. **Thử thêm nguồn Firebase thủ công**
Nếu vấn đề xảy ra chỉ với Firebase, bạn có thể thêm thủ công vào `Podfile`:
```ruby
source 'https://github.com/CocoaPods/Specs.git'
source 'https://cdn.cocoapods.org/'
```
Sau đó chạy lại:
```sh
pod install --verbose
```

---

### 5. **Xóa cache của CocoaPods**
Xóa cache để đảm bảo không có dữ liệu cũ gây lỗi:
```sh
rm -rf ~/Library/Caches/CocoaPods/
rm -rf Pods
rm -rf Podfile.lock
pod repo update
pod install
```

---

### 6. **Kiểm tra phiên bản macOS và Xcode**
Nếu bạn đang dùng phiên bản macOS hoặc Xcode quá cũ, có thể nó không hỗ trợ giao thức SSL mới. Thử cập nhật lên phiên bản mới nhất.

---

Nếu sau tất cả mà vẫn lỗi, gửi lại chi tiết log lỗi đầy đủ để em hỗ trợ kỹ hơn! 🚀
