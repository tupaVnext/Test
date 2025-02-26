Lỗi này thường liên quan đến việc CocoaPods đang sử dụng proxy không hợp lệ (`https://127.0.0.1:3128`). Đây có thể là do:

1. **Proxy đã được thiết lập nhưng không hoạt động**
2. **Cấu hình `pod` sử dụng proxy sai**
3. **Mạng bị chặn hoặc DNS không thể truy cập vào `https://cdn.cocoapods.org/`**

---

### Cách khắc phục:

#### 🔹 **1. Kiểm tra và tắt proxy**
Chạy lệnh sau trong terminal:

```sh
env | grep -i proxy
```

Nếu thấy các dòng như:

```
http_proxy=http://127.0.0.1:3128
https_proxy=https://127.0.0.1:3128
```

Thử tắt proxy bằng cách chạy:

```sh
unset http_proxy
unset https_proxy
export http_proxy=""
export https_proxy=""
```

Hoặc thêm vào `~/.zshrc` hoặc `~/.bashrc`:

```sh
export http_proxy=""
export https_proxy=""
```

Sau đó, khởi động lại terminal và thử lại `pod install`.

---

#### 🔹 **2. Xóa cache của CocoaPods và cập nhật**
```sh
rm -rf ~/Library/Caches/CocoaPods
rm -rf ~/.cocoapods/repos
pod setup
pod repo update
```

Sau đó thử chạy lại:

```sh
cd ios
pod install --verbose
```

---

#### 🔹 **3. Chạy `pod install` mà không dùng CDN**
Nếu vẫn bị lỗi, thử bỏ qua CDN của CocoaPods:

```sh
cd ios
pod install --no-repo-update
```

Hoặc chạy:

```sh
pod install --verbose --sources=https://github.com/CocoaPods/Specs.git
```

---

#### 🔹 **4. Kiểm tra file cấu hình CocoaPods**
Mở file `~/.curlrc` và kiểm tra xem có dòng `proxy` nào không:

```sh
cat ~/.curlrc
```

Nếu có dòng như:

```
proxy = 127.0.0.1:3128
```

Hãy xóa nó bằng cách mở file:

```sh
nano ~/.curlrc
```

Xóa dòng `proxy = ...`, lưu lại (`Ctrl + X → Y → Enter`), rồi thử lại `pod install`.

---

Sau khi thử các cách trên, nếu vẫn gặp lỗi, em có thể gửi chi tiết lỗi để anh hỗ trợ tiếp nhé! 🚀
