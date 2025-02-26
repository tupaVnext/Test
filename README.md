Để cài đặt CocoaPods phiên bản **1.15.2** bằng Homebrew, bạn có thể làm theo các bước sau:

---

### **1. Kiểm tra CocoaPods hiện tại**
Trước tiên, kiểm tra xem bạn đã có CocoaPods hay chưa bằng lệnh:

```sh
pod --version
```

Nếu đã có và muốn thay đổi phiên bản, bạn cần gỡ bỏ bản cũ trước.

---

### **2. Gỡ bỏ CocoaPods cũ (nếu cần)**
Nếu bạn đã cài đặt CocoaPods trước đó và muốn cài đặt lại đúng phiên bản **1.15.2**, hãy chạy:

```sh
brew uninstall cocoapods
```

---

### **3. Cài đặt CocoaPods phiên bản 1.15.2**
Vì Homebrew không hỗ trợ cài đặt một phiên bản cụ thể của CocoaPods trực tiếp, bạn cần sử dụng **gem** thay vì `brew install cocoapods`:

```sh
sudo gem install cocoapods -v 1.15.2
```

Sau đó kiểm tra lại:

```sh
pod --version
```

---

### **4. (Tùy chọn) Sử dụng CocoaPods với `rbenv` hoặc `chruby`**
Nếu bạn sử dụng Ruby qua **rbenv** hoặc **chruby**, có thể cần cài đặt CocoaPods trong môi trường Ruby của bạn:

```sh
gem install cocoapods -v 1.15.2
```

Sau đó kiểm tra đường dẫn của CocoaPods:

```sh
which pod
```

Nếu đường dẫn không đúng (vẫn trỏ đến phiên bản cũ), bạn có thể cần restart terminal hoặc chạy:

```sh
rehash
```

---

### **5. (Tùy chọn) Sử dụng Bundler để quản lý phiên bản CocoaPods**
Nếu bạn làm việc với nhiều dự án và muốn đảm bảo sử dụng đúng phiên bản CocoaPods cho từng dự án, bạn có thể dùng **Bundler**:

```sh
gem install bundler
bundle init
```

Sau đó chỉnh sửa `Gemfile`:

```ruby
source 'https://rubygems.org'
gem 'cocoapods', '1.15.2'
```

Cài đặt CocoaPods qua Bundler:

```sh
bundle install
```

Chạy CocoaPods qua Bundler:

```sh
bundle exec pod --version
```

---

### **Tóm tắt**
1. **Gỡ bản cũ** (nếu có): `brew uninstall cocoapods`
2. **Cài bản 1.15.2 qua gem**: `sudo gem install cocoapods -v 1.15.2`
3. **Kiểm tra lại phiên bản**: `pod --version`
4. **(Tùy chọn) Dùng Bundler** để cố định phiên bản trong từng dự án.

---

Bạn thử cách này xem có ổn không nhé! 🚀
