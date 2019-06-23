# App-Bundle
### Giới thiệu
Có rất nhiều điều thú vị được công bố tại I / O năm nay - trong đó có App bundles. Android App Bundles không chỉ cung cấp một định dạng upload mới cho các ứng dụng, mà nó sẽ ảnh hưởng đến cách chúng ta xây dựng và cấu trúc các ứng dụng của chúng ta theo một định dạng modules. Trong bài này, mình sẽ giới thiệu về Android App Bundles để áp dụng vào project của mình

### Sử dụng Android App Bundles có lợi gì?
- Kích thước ứng dụng nhỏ hơn

- Không còn phải quản lí nhiều file APK

- Dynamic Delivery (Module động) - Chỉ tải các tính năng trong ứng dụng của bạn khi người dùng cần chúng, tức là theo yêu cầu. Các tính năng này phải có mặt dưới dạng các mô-đun khác nhau trong dự án của ứng dụng của bạn.

- Tối ưu cho việc tích hợp Instant app - Người dùng có thể chạy ứng dụng của bạn ngay lập tức mà không phải cài đặt ứng dụng. Để tìm hiểu về instant app bạn có thểm xem tại đây



- Trước đây chúng ta phải tạo ra nhiều loại file Android Package (APK) để phù hợp với từng phiên bản API hay từng loại thiết bị khác nhau. Với Android App Bundles ta chỉ cần tải lên và tạo ra duy nhất với tất cả tài nguyên ứng dụng. Nghĩa là khi bạn sử dụng Android App Bundle(.aab) nó sẽ tạo ra nhiều loại apk được tối ưu hóa cho cấu hình của từng thiết bị cài đặt nó, vì vậy ta chỉ cần download source code và resource để chạy chúng, ví dụ ta không cần thêm ngôn ngữ khác khi mà ta đã để Tiếng Anh là ngôn ngữ mặc định của mình. Ta không còn phải tạo, quản lý nhiều APK để hỗ trợ các thiết bị khác nhau và người dùng nhận được các ứng dụng với dung lượng nhỏ hơn, được tối ưu hóa nhiều hơn.



- Ngoài ra, bạn có thể thêm các module tính năng động vào ứng dụng của mình và đưa chúng vào App Bundles. Các module này chứa các tính năng và nội dung mà bạn có thể quyết định không bao gồm khi người dùng tải xuống và cài đặt ứng dụng của bạn lần đầu tiên. Sử dụng Thư viện cốt lõi của Play , sau đó ứng dụng của bạn có thể yêu cầu tải xuống các module đó dưới dạng APK tính năng động và thông qua Dynamic Delivery, Google Play chỉ phân phát mã code và resoure cho modules đó cho thiết bị.

