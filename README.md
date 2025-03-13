flutter config --jdk-dir "/Users/cuongdt/Library/Java/JavaVirtualMachines/corretto-17.0.13/Contents/Home"

export http_proxy=<YOUR_HTTP_PROXY>
export https_proxy=<YOUR_HTTPS_PROXY>

I think you forgott to set your newly install Xcode on Command-linetool path location. please check that on Xcode-->Preferences-->Locations-->Command line tool --> set your Xcode.


https://github.com/corretto/corretto-17/releases


`identifierForVendor` trên iOS có thể thay đổi trong một số trường hợp nhất định.  

### **Giải thích về `identifierForVendor`:**  
- Đây là một UUID (Universally Unique Identifier) được Apple cung cấp để nhận diện thiết bị cho một **vendor** (nhà phát triển ứng dụng).  
- UUID này là duy nhất cho tất cả các ứng dụng của cùng một vendor (tức là cùng một **bundle ID prefix**).  

### **Khi nào `identifierForVendor` thay đổi?**  
1. **Khi người dùng gỡ cài đặt tất cả các ứng dụng của vendor**  
   - Nếu người dùng gỡ tất cả các ứng dụng của cùng một vendor rồi cài lại, `identifierForVendor` sẽ thay đổi.  
   - Nếu vẫn còn ít nhất một ứng dụng của vendor trên máy, UUID này sẽ không đổi.  

2. **Khi thiết bị được reset về cài đặt gốc (factory reset)**  
   - Khi reset toàn bộ thiết bị, UUID này cũng sẽ thay đổi.  

### **Khi nào `identifierForVendor` không thay đổi?**  
- Khi cập nhật hệ điều hành iOS.  
- Khi khởi động lại máy.  
- Khi cập nhật ứng dụng.  

**Lưu ý:** Nếu em cần một UUID cố định hơn, có thể xem xét `Keychain` để lưu trữ UUID tùy chỉnh hoặc sử dụng `deviceCheck` API của Apple.


ID thiết bị Android có dạng `AE3A.240806.005` là một **build ID** của hệ điều hành Android, dùng để nhận diện phiên bản build cụ thể của hệ thống. Cấu trúc của nó thường tuân theo một quy tắc nhất định do Google đặt ra.  

### **Phân tích từng phần của `AE3A.240806.005`:**  
1. **`AE3A`** – Mã phân loại phiên bản Android (Platform Code)  
   - Đây là mã nội bộ do Google đặt để xác định dòng phiên bản của Android.  
   - Mỗi phiên bản Android có một mã khác nhau, ví dụ:  
     - `TQ3A` (Android 13 QPR3)  
     - `UD1A` (Android 14 Developer Preview)  
     - `AE3A` có thể là mã của một bản cập nhật Android 14 hoặc Android 15.  

2. **`240806`** – Ngày phát hành bản build  
   - Định dạng: **YYMMDD** (Năm-Tháng-Ngày)  
   - `240806` có nghĩa là bản build được tạo vào ngày **06/08/2024** (ngày 6 tháng 8 năm 2024).  

3. **`005`** – Số bản build (Build Version)  
   - Đây là số thứ tự của bản build cụ thể trong ngày.  
   - `005` có nghĩa là đây là bản build thứ 5 được phát hành vào ngày hôm đó.  

### **Tóm lại:**  
- `AE3A.240806.005` là một build ID của hệ điều hành Android.  
- Được phát hành vào ngày 6 tháng 8 năm 2024.  
- Là bản build thứ 5 của ngày hôm đó.  

Nếu em muốn kiểm tra build ID mới nhất của Android hoặc thiết bị cụ thể, có thể tham khảo trang chính thức của Google:  
🔗 [https://source.android.com/docs/setup/about/build-numbers](https://source.android.com/docs/setup/about/build-numbers)


✅ Build.ID được tạo khi Google hoặc nhà sản xuất thiết bị (OEM) biên dịch một phiên bản Android mới.
✅ Nó có thể thay đổi khi có bản cập nhật Android hoặc khi nhà sản xuất phát hành một phiên bản phần mềm mới cho thiết bị.
✅ Build.ID giúp phân biệt các phiên bản Android khác nhau trên cùng một dòng thiết bị.
