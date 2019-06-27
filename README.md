# App-Bundle
### Giới thiệu
Có rất nhiều điều thú vị được công bố tại I / O năm nay - trong đó có App bundles. Android App Bundles không chỉ cung cấp một định dạng upload mới cho các ứng dụng, mà nó sẽ ảnh hưởng đến cách chúng ta xây dựng và cấu trúc các ứng dụng của chúng ta theo một định dạng modules. Trong bài này, mình sẽ giới thiệu về Android App Bundles để áp dụng vào project của mình

### Sử dụng Android App Bundles có lợi gì?

- Khi phát hành ứng dụng bằng định dạng Android App Bundle, bạn có thể giảm kích thước ứng dụng, đơn giản hóa bản phát hành và phân phối các tính năng theo yêu cầu. Nhờ có các lợi ích bổ sung này mà Android App Bundle đã trở thành định dạng phát hành được đề xuất trên Google Play.
- Kích thước ứng dụng nhỏ hơn

- Không còn phải quản lí nhiều file APK

- Dynamic Delivery (Module động) - Chỉ tải các tính năng trong ứng dụng của bạn khi người dùng cần chúng, tức là theo yêu cầu. Các tính năng này phải có mặt dưới dạng các mô-đun khác nhau trong dự án của ứng dụng của bạn.

- Tối ưu cho việc tích hợp Instant app - Người dùng có thể chạy ứng dụng của bạn ngay lập tức mà không phải cài đặt ứng dụng. Để tìm hiểu về instant app bạn có thểm xem tại đây



- Trước đây chúng ta phải tạo ra nhiều loại file Android Package (APK) để phù hợp với từng phiên bản API hay từng loại thiết bị khác nhau. Với Android App Bundles ta chỉ cần tải lên và tạo ra duy nhất với tất cả tài nguyên ứng dụng. Nghĩa là khi bạn sử dụng Android App Bundle(.aab) nó sẽ tạo ra nhiều loại apk được tối ưu hóa cho cấu hình của từng thiết bị cài đặt nó, vì vậy ta chỉ cần download source code và resource để chạy chúng, ví dụ ta không cần thêm ngôn ngữ khác khi mà ta đã để Tiếng Anh là ngôn ngữ mặc định của mình. Ta không còn phải tạo, quản lý nhiều APK để hỗ trợ các thiết bị khác nhau và người dùng nhận được các ứng dụng với dung lượng nhỏ hơn, được tối ưu hóa nhiều hơn.

- Ngoài ra, bạn có thể thêm các module tính năng động vào ứng dụng của mình và đưa chúng vào App Bundles. Các module này chứa các tính năng và nội dung mà bạn có thể quyết định không bao gồm khi người dùng tải xuống và cài đặt ứng dụng của bạn lần đầu tiên. Sử dụng Thư viện cốt lõi của Play , sau đó ứng dụng của bạn có thể yêu cầu tải xuống các module đó dưới dạng APK tính năng động và thông qua Dynamic Delivery, Google Play chỉ phân phát mã code và resoure cho modules đó cho thiết bị.

#### Cách hoạt động của app bundle
- App bundle dùng mô hình phân phối mới có tên là Dynamic Delivery của Google Play để tạo và phân phối các APK được tối ưu hóa cho từng cấu hình thiết bị. Bằng cách xóa mã và tài nguyên không sử dụng cho các thiết bị khác, mô hình phân phối này mang lại một ứng dụng có kích thước nhỏ hơn, hiệu quả hơn để người dùng cài đặt.

#### Lợi ích của việc sử dụng app bundle 
- Với app bundle, bạn chỉ cần tạo, ký và tải một cấu phần phần mềm duy nhất lên để hỗ trợ APK tối ưu hóa cho nhiều cấu hình thiết bị khác nhau. Sau đó, Google Play sẽ quản lý và phân phối APK của ứng dụng cho bạn. Nhờ vậy, bạn không cần phải quản lý mã phiên bản cho từng kết hợp giao diện nhị phân ứng dụng (ABI), mật độ màn hình và ngôn ngữ mà mình muốn hỗ trợ. Ngoài ra, khi sử dụng app bundle, bạn có thể hưởng lợi từ những cải tiến liên tục được thêm vào quy trình phân phối.

- So với APK, app bundle có những ưu điểm sau:

- Có kích thước tải xuống và dung lượng trên đĩa nhỏ hơn
- Có thể sử dụng thư viện gốc chưa nén (Android 6.0 trở lên) lưu trữ trên APK thay vì thiết bị của người dùng, nhờ đó có thể giảm kích thước tải xuống, dung lượng trên đĩa và thời gian cài đặt
- Phân phối cho người dùng các cấu hình và chức năng mà họ cần khi họ yêu cầu chứ không phải trong quá trình cài đặt
- Đơn giản hóa việc quản lý bản dựng và bản phát hành bằng cách loại bỏ nhu cầu tạo và phát hành nhiều APK
- Khi bạn tải app bundle lên Play Console, Google Play sẽ gửi một tệp nhị phân được tối ưu hóa cho thiết bị.

### 3. Trong Android App Bundles (.aab) có gì?
- APK là thứ ta có thể phân phối trực tiếp cho thiết bị của người dùng, trong khi đó, App Bundles là định dạng xuất bản không thể được cài đặt trên thiết bị của chính nó. Mặc dù chúng có điểm giống nhau, nhưng aab có chứa một số nội dung mà ta sẽ không tìm thấy trong các tệp APK. Ví dụ: các tệp dữ liệu meta trong các gói được sử dụng bằng cách sử dụng công cụ để tạo APK sẽ được phân phối cho người dùng, những tệp này sau đó không được bao gồm trong các APK. Một tệp abb điển hình có thể chứa:

- manifest.xml - Giống như bạn sẽ thấy trong các APK của mình, có tệp kê khai hiện diện trên mỗi gói ứng dụng. Tuy nhiên, không giống như các APK này không được lưu trữ ở định dạng nhị phân - nó được biên dịch thành định dạng đệm giao thức giúp dễ dàng chuyển đổi công cụ khi cần.
- res / assets / libs - Tất cả tài nguyên, nội dung và thư viện gốc đều được lưu trữ giống như trong APK. Sự khác biệt duy nhất ở đây là bất kỳ tệp tài nguyên nào cũng sẽ được lưu trữ trong định dạng bộ đệm giao thức làm điểm cuối cùng.
resources.pb - Tương tự như tệp resource.arac có thể tìm thấy bên trong tệp APK hiện tại , file resources.pb là một bảng tài nguyên nêu rõ các tài nguyên và chi tiết cụ thể để nhắm mục tiêu có trong ứng dụng. Phần extention .pb là do định dạng đệm giao thức được sử dụng bởi công cụ để chuyển đổi gói ứng dụng trước khi được chuyển đổi thành định dạng nhị phân được sử dụng trong APK.
- assets.pb - Đây là bảng tương đương với một resource cho các ứng dụng và sẽ chỉ xuất hiện nếu bạn đang sử dụng resource trong ứng dụng của mình.
- native.pb - Đây là resource cho các native library và sẽ chỉ có nếu bạn đang sử dụng các native lib trong ứng dụng của mình.

### 4. Dynamic Delivery (phân phối động)

- Một thành phần cơ bản của Phân phối động là cơ chế phân tách APK có sẵn trên Android 5.0 (API = 21) trở lên. APK phân tách rất giống với APK thông thường — chúng bao gồm bytecode DEX được biên dịch, tài nguyên và tệp manifest Android. Tuy nhiên, nền tảng Android có thể xử lý nhiều APK phân tách được cài đặt dưới dạng một ứng dụng. Với các APK phân tách, Google Play có thể chia nhỏ ứng dụng lớn thành các gói nhỏ hơn, riêng biệt được cài đặt trên thiết bị của người dùng theo yêu cầu .

- Slip APK được chia thành 3 loại:

- Base APK : APK này chứa code và resource mà tất cả các APK phân tách khác có thể truy cập và cung cấp chức năng cơ bản cho ứng dụng của bạn. Khi người dùng download ứng dụng của bạn chắc chắn có file APK này

- Configuration APKs: Mỗi APK trong số này bao gồm native libraries và resource cho từng cấu hình device cụ thể, nó sẽ tối ưu hóa nội dung APK theo dựa theo :

1. Ngôn ngữ
2. Mật độ màn hình
3. Kiến trúc CPU
- Khi bạn build abb, theo mặc định, tất cả các phần tách sẽ được tạo, nhưng trong build.gradle, ta có thể khai báo những phần tách nào sẽ được tạo:

          bundle {
              language {
                  // Specifies that the app bundle should not support
                  // configuration APKs for language resources. These
                  // resources are instead packaged with each base and
                  // dynamic feature APK.
                  enableSplit = false
              }
              density {
                  // This property is set to true by default.
                  enableSplit = true
              }
              abi {
                  // This property is set to true by default.
                  enableSplit = true
              }
          }
          
- Ban đầu, các thuộc tính này sẽ được đặt thành true. Tuy nhiên, đặt một thành false có nghĩa là nó không hỗ trợ phân tách phần đó trong APK config, có nghĩa là nó sẽ được đóng gói trong Base APK hoặc Dynamic-Feature APK

- Dynamic feature APKs: Mỗi APK này chứa code và resource không bắt buộc khi ứng dụng của bạn được cài đặt lần đầu, nhưng có thể được tải xuống và cài đặt sau.

### 4.1 Dynamic feature module (Module tính năng động)
- Dynamic feature module cho phép bạn tách các tính năng và tài nguyên nhất định khỏi module cơ sở của ứng dụng và đưa chúng vào aab. Thông qua Dynamic Delivery, sau này người dùng có thể tải xuống và cài đặt các thành phần đó theo yêu cầu sau khi họ đã cài đặt APK cơ sở của ứng dụng của bạn.
- Ví dụ, một ứng dụng nhắn tin văn bản bao gồm chức năng chụp và gửi tin nhắn hình ảnh, nhưng chỉ một phần nhỏ người dùng gửi tin nhắn hình ảnh. Có thể có ý nghĩa khi đưa tin nhắn hình ảnh làm nó thành Dynamic feture module có thể tải xuống. Bằng cách đó, tải xuống ứng dụng ban đầu nhỏ hơn cho tất cả người dùng và chỉ những người dùng gửi tin nhắn hình ảnh đó mới cần tải xuống thành phần bổ sung đó.

- Lưu ý rằng loại module hóa này đòi hỏi nhiều effort để có thể tái cấu trúc lại ứng dụng, vì vậy, nên xem xét cẩn thận những tính năng nào của ứng dụng sẽ mang lại lợi ích nhiều nhất cho người dùng. Android App Bundles cung cấp một số tùy chọn bổ sung giúp bạn chuyển đổi ứng dụng của mình theo hướng hỗ trợ đầy đủ các tính năng theo yêu cầu.

### 4.2 Tạo Dynamic feature module
- Để tạo Dynamic feture module ta sử dụng Android Studio 3.2 hoặc cao hơn Mở tệp manifest ta thấy :

        <manifest xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:dist="http://schemas.android.com/apk/distribution"
          package="com.ntd.samples.dynamicfeatures.ondemand.assets"
          split="assets">

          <dist:module
              dist:onDemand="true"
              dist:title="@string/title_dynamic_feature">
              <dist:fusing dist:include="true" />
          </dist:module>

      </manifest>
      
-  onDemand  : Nếu thuộc tính được đặt thành true thì module sẽ có sẵn để tải xuống theo yêu cầu. Khi được đặt thành false, tính năng động sẽ được tải xuống khi người dùng tải xuống lần đầu tiên và cài đặt ứng dụng.
- title  : Title sẽ được sử dụng để xác định module khi người dùng xác nhận tải về module. Đoạn string này nên được lưu trữ trong resource của ứng dụng để nó có thể được nhận cho các phần khác nhau mà ứng dụng của bạn hỗ trợ.
- fusing : Đặt thuộc tính này thành true sẽ có nghĩa là các thiết bị cũ hơn (4.4 trở xuống) sẽ có thể nhận các tính năng động này dưới dạng multi-APK. Để sử dụng chức năng này, bạn phải bật thuộc tính onDemand.

### Làm sao để dowload Dynamic Feature Module trong thời gian chay?
- Thêm Play Core Library vào build.gradle

              dependencies {
          implementation 'com.google.android.play:core:1.3.4'
      }
- Để tải xuống và quản lí Dynamic Feature trong thời gian chạy, sử dụng lớp SplitInstallManager

          val splitInstallManager = SplitInstallManagerFactory.create(this)
          
- Tạo Request dowload: 

              val request = SplitInstallRequest
        .newBuilder()
        .addModule("someDynamicModule")
        .build()
        
- Install module với request

          splitInstallManager.startInstall(request).addOnSuccessListener {
            
        }
        
- Lắng nghe trạng thái của request 

          val stateListener = SplitInstallStateUpdatedListener { state ->
          when (state.status()) {
              PENDING -> { }
              DOWNLOADING -> { }
              DOWNLOADED -> { }
              INSTALLED -> { }
              INSTALLING -> { }
              REQUIRES_USER_CONFIRMATION -> { }
              FAILED -> { }
              CANCELING -> { }
              CANCELED -> { }
          }
      }
      splitInstallManager.registerListener(stateListener)
      
- Khi không dùng đến Dynamic Module đó nữa ta có thể uninstall chúng : 
      
        splitInstallManager
        .deferredUninstall(Arrays.asList("dynamicModuleUninstall"))
        
### Test app với bundler tool 
- Vì khi sử dụng App - bundle, ta ko thể lấy luôn file apk của chúng mà phải sử dụng bundle tool để gen ra apks file
- Link repository:  https://github.com/google/bundletool/releases
- Để chuyển từ .abb -> apks dùng lệnh

                    bundletool build-apks --bundle=<path to .aab> --output=<out.apks>
                    
- Sau đó giải nén .apk thành apk
                    
                    
                    mkdir apks
                    
### Dynamic Module với từng API
### API <20 : Không support download apks trong khi dùng app, Google Play sẽ tạo ra  apk duy nhất đó là multi-apk, nó sẽ tối ưu hóa cho thiết bị đó, nó tương tự như multi apk hồi xưa vậy.
- Tuy nhiên nó bao gồm tất cả các ngôn ngữ mà ứng dụng của bạn hỗ trợ. Ví dụ, điều này cho phép người dùng thay đổi cài đặt ngôn ngữ ưa thích của ứng dụng mà không phải tải xuống nhiều APK khác nhau.
- Nhiều APK không có khả năng tải xuống các mô-đun tính năng động theo yêu cầu. Để bao gồm một mô-đun động trong APK này, bạn phải tắt Theo yêu cầu hoặc bật Fuses khi tạo mô-đun tính năng động. 

- Với dynamic delivery ta không cần phải built, sigin, upload và quản lí multi apk mà ứng dụng của bạn hỗ trợ. Bạn vẫn chỉ xây dựng và tải lên một gói ứng dụng duy nhất cho toàn bộ ứng dụng của mình và Google Play sẽ lo phần còn lại cho bạn. Vì vậy, cho dù bạn có kế hoạch hỗ trợ các thiết bị chạy Android 4.4 trở xuống hay không, Dynamic Delivery cung cấp cơ chế phục vụ linh hoạt cho cả developer và user dùng app
### Api >= 21 : Cho phép download dynamic modudle khi dùng app 
### Modularize app
- Là quá trình tách các thành phần logic của app thành các module riêng biệt.
- Việc này cần có sự cân nhắc và mất nhiều thời gian, nhưng nó có một số lợi ích sau:
1. Phát triển song song: bằng việc tách các thành phần logic của ứng dụng thành các module, các nhóm hoặc cá nhân có thể sở hữu 1 module để phát triển ít gây conflic hơn, tránh gây gián đoạn.  Ngoài ra, nếu bạn có logic mà sử dụng trong các phần khác nhau của ứng dụng, bạn có thể sử dụng các mô-đun thư viện để thúc đẩy việc tái sử dụng và đóng gói code
2. Cải thiện thời gian build app: Hệ thống built grade sẽ tối ưu hơn về hiệu năng khi ứng dụng đc tổ chức dưới dạng module. Ví dụ, bạn bật chế độ parallel project execution để thực hiện multi-core processor, hệ thống built nhiều module cùng một lúc để giảm thời gian built 
3. Customize feature delivery : Việc module hóa các tính năng ứng dụng của bạn như các module tính năng động là một yêu cầu để tận dụng các tùy chọn phân phối tùy chỉnh Dynamic Delivery, như theo yêu cầu, có điều kiện và phân phối ngay lập tức. Tạo các tính năng động theo yêu cầu đòi hỏi nhiều nỗ lực hơn và có thể tái cấu trúc ứng dụng của bạn. Vì vậy, hãy cân nhắc cẩn thận những tính năng nào trong ứng dụng của bạn sẽ được hưởng lợi nhiều nhất từ ​​việc được mô đun hóa thành các tính năng động và hưởng lợi từ các tùy chọn phân phối tùy chỉnh.
### Sử dụng dynamic feature module để phân phối module 
- Một lợi ích duy nhất của Phân phối động là khả năng tùy chỉnh cách thức và thời điểm các tính năng khác nhau của ứng dụng của bạn được tải xuống trên các thiết bị chạy Android 5.0 trở lên. Ví dụ: để giảm kích thước tải xuống ban đầu của ứng dụng, bạn có thể định cấu hình một số tính năng nhất định để được tải xuống khi cần theo yêu cầu hoặc chỉ bởi các thiết bị hỗ trợ một số khả năng nhất định, chẳng hạn như khả năng chụp ảnh hoặc hỗ trợ các tính năng thực tế tăng cường.
- Mặc dù bạn nhận được các bản tải xuống được tối ưu hóa cao theo mặc định khi bạn tải lên ứng dụng của mình dưới dạng gói ứng dụng, các tùy chọn phân phối tính năng nâng cao và tùy chỉnh hơn yêu cầu cấu hình bổ sung và mô đun hóa các tính năng ứng dụng của bạn bằng mô-đun tính năng động. Nghĩa là, các mô-đun tính năng động cung cấp các khối xây dựng để tạo các tính năng mô-đun mà bạn có thể định cấu hình cho từng khối được tải xuống khi cần.
#### Delivery Option 
1. At-install delivery : Theo mặc định, các module tính năng động không cấu hình bất kỳ tùy chọn phân phối nào được mô tả ở trên được tải xuống khi cài đặt ứng dụng. Đây là một hành vi quan trọng bởi vì nó có nghĩa là bạn có thể áp dụng các tùy chọn phân phối nâng cao dần dần. Ví dụ: bạn có thể hưởng lợi từ việc module hóa các tính năng ứng dụng của bạn và chỉ cho phép phân phối theo yêu cầu sau khi bạn thực hiện đầy đủ các yêu cầu tải xuống bằng thư viện Play Core. 
Ngoài ra, ứng dụng của bạn có thể yêu cầu gỡ cài đặt các tính năng sau. Vì vậy, nếu bạn yêu cầu một số tính năng nhất định khi cài đặt ứng dụng, nhưng sau đó, bạn có thể giảm kích thước cài đặt bằng cách yêu cầu xóa tính năng này khỏi thiết bị.
