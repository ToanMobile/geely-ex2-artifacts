# Changelog

Nội dung file này **lên thẳng màn hình Cập nhật** của cả hai app: `publish-artifacts.sh` đọc mục
đúng version đang phát hành rồi ghi vào `releaseNotes` của `artifacts/update.json` (xe tự kiểm tra
bản mới) và `artifacts/apps.json` (kho ứng dụng trên điện thoại).

**Khuôn bắt buộc — script dò theo đúng dòng tiêu đề này:**

```
## CarConnect 1.0.59
- Gạch đầu dòng viết cho CHỦ XE đọc, không phải cho lập trình viên
```

Quy ước:

- Tiêu đề phải là `## <Tên app> <VERSION_NAME>` — `CarConnect` hoặc `PhoneConnect`, version khớp
  `app/version.properties`. Sai khuôn thì script rơi về chuỗi cũ `"CarConnect v1.0.58(158)"` và
  màn Cập nhật lại trống trơn như trước.
- Viết bằng **ngôn ngữ người dùng**: "kính tự hé khi mở cửa" chứ không phải "sửa `DoorPosDecoder`".
- Ngắn gọn — popup trên xe và thẻ trên điện thoại đều hẹp. Vài gạch đầu dòng là đủ; chi tiết kỹ
  thuật để trong `docs/` và trong KDoc.
- Mục mới thêm lên **trên cùng**.
- **Đừng xoá mục cũ**: file đã tích luỹ từ 30/08 (đính chính 14/09/2026), `publish-artifacts.sh` dò đúng mục `## <Tên app> <VERSION_NAME>`. Không đụng các mục bản trước đó.

---

## CarConnect 1.2.0

- **Khắc phục triệt để lỗi trợ lý giọng nói tự kích hoạt khi đàm thoại & tối ưu nhận diện "Hi Geely"**: Nâng cấp thuật toán lọc từ khoá KWS tầng 2, loại bỏ hoàn toàn hiện tượng xe tự động bật "Đang nghe..." khi người ngồi trong xe nói chuyện đời thường, đồng thời hỗ trợ đầy đủ các biến âm lướt nhẹ khi người lái nói ở âm lượng đàm thoại bình thường mà không cần hét lớn.
- **Cải tiến trợ lý giọng nói chuyển chế độ lái Eco linh hoạt**: Mở rộng nhận diện tự nhiên hàng loạt biến thể khẩu lệnh chuyển sang chế độ tiết kiệm năng lượng ("đổi sang eco", "thay đổi sang chế độ eco", "chuyển sang lái tiết kiệm", "đổi chế độ tiết kiệm"...), phản hồi tức thì và chính xác.
- **Nâng cấp kho ứng dụng Cài nhanh**: Cập nhật nguồn tải tốc độ cao và ổn định cho Waze Mod và YouTube Morphe phiên bản mới nhất, tự động nhận diện gói ứng dụng tương đương và kiểm tra điều kiện cài đặt MicroG thông minh.
- **Tối ưu hóa độ ổn định toàn hệ thống**: Hoàn thiện cơ chế cấp phép dùng thử và tinh chỉnh hiệu năng đa nhiệm trên màn hình xe.

## PhoneConnect 1.2.0

- **Đồng bộ phiên bản 1.2.0 với xe**: Đồng bộ toàn diện hệ thống điều khiển và danh mục ứng dụng cài nhanh mới nhất với màn hình xe.
- **Cải thiện kết nối và trải nghiệm người dùng**: Tối ưu hóa phản hồi lệnh điều khiển từ xa và nâng cao độ mượt mà khi tương tác.

## CarConnect 1.1.9

- **Tự động toàn màn hình khi tắt 1 ứng dụng chia đôi**: Khi đang chia đôi 2 ứng dụng, nếu tắt 1 ứng dụng thì ứng dụng còn lại tự động bung ra toàn màn hình ngay lập tức, không còn bị kẹt nửa màn hình.
- **Khắc phục lỗi ứng dụng mở mới bị hiển thị dạng cửa sổ nổi**: Tự động dọn dẹp sạch sẽ các vùng cửa sổ chia đôi cũ, giúp ứng dụng mở mới từ màn hình chính luôn hiển thị trọn vẹn toàn màn hình.
- **Kéo vạch chia đôi siêu mượt mà 60 FPS**: Tối ưu hóa phản hồi cảm ứng mượt mà khi di chuyển vạch chia đôi, tích hợp cơ chế tự động căn chỉnh thông minh vào các tỷ lệ chuẩn (30:70, 50:50, 70:30), bảo vệ trải nghiệm xem video và bản đồ không bị gián đoạn.
- **Thêm nút "Reset màn hình" trên bảng tiện ích nổi**: Hỗ trợ xử lý nhanh các tình huống kẹt cửa sổ, khôi phục giao diện xe về trạng thái chuẩn với cơ chế chạm 2 bước xác nhận an toàn chống bấm nhầm khi đang lái xe.

## PhoneConnect 1.1.9

- **Đồng bộ phiên bản 1.1.9 với đầu xe**: Nâng cao độ ổn định kết nối và đồng bộ trạng thái hiển thị nhiều cửa sổ với hệ thống xe.

## CarConnect 1.1.8

_(Bỏ số 1.1.7 để nhảy lên 1.1.8 đồng bộ cùng phiên bản PhoneConnect 1.1.8 = mã 1108.)_

- **Nhận diện giọng nói "Hi Geely" siêu nhẹ và tức thì**: Tích hợp mô hình nhận diện từ khóa chuyên dụng mới siêu nhẹ (chỉ ~140 KB), phản hồi cực nhanh dưới 50ms, bảo vệ tuyệt đối bản quyền.
- **Tiết kiệm pin và giải phóng tải phần cứng xe**: Tối ưu gom khung âm thanh 160ms giúp giảm 50% số lần xử lý và khóa luồng nền chạy trên lõi phụ, giữ màn hình xe luôn mượt mà 60 FPS khi đang dẫn đường bản đồ.
- **Không nuốt âm, không rụng chữ**: Bộ đệm âm thanh thông minh 2 giây lưu trọn vẹn giọng nói khi ra lệnh liền mạch "Hi Geely mở điều hòa 24 độ", xe hiểu ngay không cần ngắt quãng.
- **Bảo mật tệp và chống lỗi nguồn điện**: Cơ chế lưu trữ nguyên tử chống hỏng tệp khi tắt mở xe đột ngột, phân quyền bảo mật cấp hệ thống chống sao chép trái phép.

## PhoneConnect 1.1.8

- **Đồng bộ toàn diện với hệ thống xe bản 1.1.8**: Tối ưu kết nối điều khiển xe từ xa qua mạng nội bộ Hotspot và Bluetooth SPP ổn định cao.
- **Tối ưu trải nghiệm điều khiển tức thì**: Cải tiến hàng đợi lệnh điều hòa, kính cửa và chế độ lái, tự động gửi lại khi vừa nối lại xe.

## CarConnect 1.1.6

- **Ghép đôi 1 chạm với điện thoại**: popup toàn màn hình "<máy> muốn ghép đôi · mã XXXX — Từ chối / Cho phép"; chỉ nhận qua Wi‑Fi/Bluetooth, 1 yêu cầu/lúc, khoá 5 phút sau 3 lần từ chối.
- **Hình nền từ điện thoại đổi ngay trên màn hình xe** (trước đây launcher Flyme bỏ qua ảnh chưa đăng ký): ô hình nền của CarConnect trong bộ sưu tập ROM — đăng ký 1 lần (chạm "Áp dụng" trên xe), sau đó mọi ảnh gửi lên tự chuyển 1920×1080 và áp ngay, không chạm.
- **Bộ nhận dạng giọng nói tải về có tiến độ rõ ràng**: xe nâng cấp từ bản 1.0.x phải tải lại bộ nhận dạng tiếng Việt (56 MB). Nay màn Giọng nói và Cài đặt ➔ Cập nhật hiện % đang tải, nói rõ "xe chưa có mạng" thay vì "thử lại sau ít phút", có nút Tải lại; mất mạng giữa chừng thì lần sau tải tiếp, không tải lại từ đầu.
- **Gọi "Hi Geely" nhận nhiều giọng hơn**: xe từng bác oan cách gọi của khách (nghe thành "hi gi li"); nay nhận đúng và không còn báo "Lệnh không chính xác" khi bạn vừa gọi xong chưa kịp ra lệnh.
- **Nói câu có ngắt vẫn hiểu trọn**: "máy lạnh … hai lăm độ" (ngắt giữa chừng) nay đặt đúng 25 °C thay vì chỉ bật điều hoà.
- **Lấy gió trong / gió ngoài giữ đúng trạng thái**: nói "gió ngoài" khi xe đã gió ngoài không còn bị lật ngược; thêm cách nói "mở tuần hoàn", "đóng gió trong".
- **Sấy gương** đọc/ghi đúng kênh xe (bản trước có thể lỗi im lặng).
- **Cập nhật ứng dụng không còn chặn khi xe đang chạy**; bản tải dở được giữ lại tới khi cài xong.
- Kỹ thuật: thêm số đo tải bộ nhận dạng, lượt gọi Hi Geely được chấp nhận/bác, và lưu mẫu 2 giây mỗi lần gọi (khi bật "gửi mẫu giọng nói") để huấn luyện bộ nhận gọi tên tiếng Việt.

## PhoneConnect 1.1.7

_(Bỏ số 1.1.6: mã 1106 đã public dưới tên 1.1.5; tên nhảy lên 1.1.7 = mã 1107.)_

- **Ghép đôi 1 chạm** (cả Android lẫn iOS): không cần quét QR khi đã nối Wi‑Fi/Bluetooth — bấm "Ghép đôi 1 chạm", xe hiện hộp xác nhận to với mã 4 số, chạm "Cho phép" trên xe là xong. QR vẫn giữ để ghép từ xa.
- Hình nền: chọn ảnh trong danh sách trên xe → hộp xem trước "Đặt hình nền này ngay" (iOS giống Android); xe đổi ngay, app đánh dấu đúng ảnh đang dùng. Ảnh chụp dọc không còn bị xoay ngang.
- iOS: hết 2 khối trắng thừa cuối trang Nhạc & Hình nền; các hộp xác nhận trên trang con hiện đúng chỗ.
- Ra lệnh khi chưa nối được xe: lệnh được xếp hàng và tự gửi khi nối lại (lệnh kính/khoá cửa chỉ giữ 5 phút để an toàn).
- Đồng bộ mã lệnh với xe bản 1.1.6.
- **Chế độ lái & hồi năng: chạm là đổi ngay**, không còn hộp thoại hỏi lại trên điện thoại (chỉ ra lệnh bằng giọng nói xe mới hỏi).
- Nút nào xe báo chưa đọc được tín hiệu sẽ có dòng nhắc, lệnh vẫn được gửi (không khoá nút).
- Quét mã QR: mã sai hoặc đã hết hạn nay báo ngay và cho quét tiếp, không còn đứng im; rung nhẹ khi quét trúng.
- Giờ "Đỗ lúc" giữ đúng thời điểm đỗ, không còn bị cập nhật liên tục khi xe đứng yên.
- Mở khoá cửa: vì lý do an toàn xe chỉ nhận mở khoá bằng chìa/tay nắm cửa (đo thật 19/09) — bấm trong app nay chỉ nhắc, không gửi lệnh; thêm nút "Đã khóa / Mở khóa" rõ ràng ở Điều khiển.
- iPhone: xe đổi mạng/đổi IP nay tự tìm lại (trước phải mở lại app); hết hiện tượng rớt nối 35 giây sau khi ra nền; giờ "Đỗ lúc" không còn bị ghi đè khi mất Wi‑Fi tại chỗ đỗ.
- Cloud 4G (iPhone): sửa phiên cũ hết hạn vẫn mở kênh thứ hai chen phiên mới.
- Xoay màn hình không còn mất trang đang mở; xoá bản ghi sổ bảo dưỡng phải xác nhận.
- **iPhone (đồng bộ 100 % với Android)**: gửi nhạc/hình nền lên xe chạy được (trước đây xe luôn từ chối); kết nối Cloud 4G tự nối lại sau khi rớt; báo rõ khi xe từ chối token và có nút "Quét QR ngay"; Kho ứng dụng & Cài nhanh cài thật (tải, kiểm chữ ký/SHA, đẩy lên xe, báo đúng kết quả), quản lý ứng dụng trên xe đủ Ẩn/Hiện/Mở/Gỡ; ảnh chọn từ Photos, xem thumbnail, nghe thử nhạc; gửi tệp lớn không còn tốn RAM và có tiến độ thật; kiểm tra cập nhật iOS an toàn (xác minh chữ ký, ép cập nhật khi cần) và mở đúng TestFlight; app luôn tiếng Việt; token bảo mật lưu trong Keychain.

## CarConnect 1.1.5

- **🗺️ Google Maps tích hợp tối ưu mượt mà 60 FPS**: Tự động chuyển sang chế độ 2D siêu nhẹ, tắt toà nhà 3D và giao thông nặng nề, xoay theo hướng xe và tắt hiệu ứng chuyển động toàn hệ thống ngay khi cài đặt — phản hồi tức thì 0ms, không còn lag giật.
- **🎧 YouTube Music & Spotify chạy ngầm bất tử**: Nghe nhạc xuyên suốt cả chuyến đi! Chuyển sang app khác hoặc ẩn xuống nền xe không bao giờ bị hệ thống tự động tắt nhạc giữa chừng như trước.
- **📱 Chia đôi màn hình vừa dẫn đường vừa nghe nhạc**: Thoải mái mở song song Vietmap Live / Google Maps bên cạnh YouTube / Spotify. Nhạc vẫn phát ngầm liên tục, đặc biệt xe tự động giảm nhỏ âm lượng nhạc thông minh mỗi khi có thông báo tốc độ hoặc cảnh báo phạt nguội.
- **🔘 Phím nổi đa năng tiện ích (Quick Floater)**: Nút nổi thông minh kéo thả mọi vị trí trên màn hình. Đang xem bản đồ chỉ cần chạm nhẹ là chỉnh ngay chế độ lái (Sport/Comfort/Eco), mức hồi năng, quạt gió điều hoà hoặc tắt đen màn hình nghỉ ngơi mà không cần bấm thoát ra ngoài.
- **🎵 Phím vô-lăng chuyển bài chuẩn xác**: Nút chuyển bài tới/lui trên vô-lăng nhận diện hoàn hảo với YouTube Music, YouTube và Spotify — bấm một nấc đổi đúng một bài, không còn bị nhảy cóc 2 bài liên tiếp (Spotify gói Free không hỗ trợ lùi bài do giới hạn từ app).
- **🗣️ Xác nhận giọng nói rảnh tay**: Khi xe hỏi lại để xác nhận an toàn (hạ kính, đổi chế độ lái lúc đang chạy), xe sẽ tự động mở mic chờ nghe. Các bác chỉ cần nói tự nhiên "có" / "phải" / "dạ" hoặc "không" / "hủy" mà không cần bấm lại nút nói trên vô-lăng.
- **🧭 Mở app & bản đồ thông minh hơn**: Nói "khởi động YouTube" xe hiểu là mở app (không còn bị nghe nhầm thành đóng app); nói "mở maps" mở đúng bản đồ (không mở nhầm VTV Go); nói "mở nhạc YouTube" mở chuẩn YouTube Music; lệnh chia đôi màn hình ("chia hai ứng dụng Google Maps và YouTube") nhận diện mượt mà kể cả khi có từ đệm.
- **📍 Google Maps giữ định vị GPS ổn định**: Không còn hiện tượng mất vị trí, đứng yên chấm xanh sau mỗi lần tắt / bật lại máy xe.
- **🛡️ Ổn định hệ thống**: Trợ lý giọng nói hoạt động bền bỉ, không còn bị ngắt đột ngột mỗi khi xe tự động đổi giao diện sáng / tối (khi bật đèn pha hoặc vào hầm).
- **🔤 Tên ứng dụng hiển thị chuẩn**: Toàn bộ ứng dụng đều hiển thị tên tiếng Việt rõ ràng, dễ nhìn, không còn hiện mã gói kỹ thuật (com.google...).
- **💡 Cách cập nhật**: Các bác mở ứng dụng CarConnect trên xe ➔ vào Cài đặt ➔ bấm Kiểm tra cập nhật (hoặc nhận file cài trực tiếp từ điện thoại qua ứng dụng PhoneConnect). Chúc các bác luôn có những chuyến đi vui vẻ và an toàn!

## PhoneConnect 1.1.5

- Đồng bộ mã lệnh và tối ưu Google Maps trực tiếp trong APK, gỡ bỏ các nút bấm thừa và tinh chỉnh giao diện mượt mà.

## CarConnect 1.1.4

- **YouTube Music & Spotify chạy ngầm không bị tắt**: Nhạc phát xuyên suốt, chuyển app hay ẩn xuống nền không bao giờ bị hệ thống ngắt giữa chừng.
- **Chia đôi màn hình vừa dẫn đường vừa nghe nhạc**: Vừa mở Vietmap Live / Google Maps vừa mở YouTube / Spotify song song, âm thanh phát liền mạch không ngắt quãng (tự động giảm nhỏ tiếng nhạc khi có cảnh báo giao thông/phạt nguội).
- **Phím nổi đa năng (Widget nổi Quick Floater)**: Nút nổi thông minh kéo thả trên màn hình, chạm là chỉnh nhanh chế độ lái, mức hồi năng, quạt gió điều hoà, hoặc tắt đen màn hình mà không cần thoát bản đồ.
- **Phím chuyển bài trên vô-lăng đã chạy với YouTube Music, YouTube và Spotify** — bấm tiến/lùi là đổi bài, không nhảy hai bài. (Spotify gói Free không cho lùi bài — giới hạn của Spotify.)
- **Xe hỏi lại thì cứ nói "có" / "phải" / "dạ"**: câu hỏi xác nhận (mở kính, đổi chế độ lái khi đang chạy) nay đứng yên chờ bạn trả lời và xe tự mở mic — không phải bấm nút nói nữa. Muốn hủy thì nói "không" hoặc "hủy".
- **Hiểu đúng hơn khi mở app**: "khởi động YouTube" không còn bị hiểu thành đóng app; "mở maps" không còn mở nhầm VTV Go; "mở / nghe nhạc YouTube" mở YouTube Music; "mở Google Maps", "mở YouTube Music" mở đúng bản đang cài trên xe.
- **Chia đôi màn hình bằng giọng nói dễ tính hơn**: "chia hai ứng dụng Google Maps *và* YouTube" mà xe nghe chệch chữ nối ("là", "rồi", "qua"…) vẫn hiểu.
- **Google Maps không còn mất định vị sau khi tắt/bật xe**: xe tự bật lại cài đặt vị trí mỗi lần khởi động (chỉ khi trên xe có cài Maps).
- **Chọn kênh Ổn định / Thử nghiệm không còn tự tải bản mới** — chạm ô kênh chỉ để xem, muốn tải thì bấm "Tải về & cài đặt". Nút "Kiểm tra cập nhật" vẫn tải và cài luôn như cũ.
- **Trợ lý giọng nói không còn tắt đột ngột** khi màn hình xe đổi sáng/tối (lỗi của bản 1.1.3).
- Tên ứng dụng hiện đúng tên người đọc được, không còn hiện tên kỹ thuật kiểu "com.google…".
- Ghi chú: tính năng gọi "Hi Geely" **vẫn đang tắt** như bạn đã tắt trước đó; bản này chưa có nút bật/tắt (đang bổ sung), muốn đổi thì báo để chỉnh từ máy tính. Ghi chú của bản 1.1.3 nói bản đó bật lại là chưa đúng.

## PhoneConnect 1.1.4

- Bản đồng bộ số hiệu với xe. Không có thay đổi nào trên điện thoại.

## CarConnect 1.1.3

- **Xe không còn tự ý làm việc khác khi nghe nhầm**: nói "mở cốp xe" từng bị hiểu thành "mở chốt xe",
  "dừng sạc" từng thành "dừng phát" (tắt nhạc). Nay gặp những câu này xe **im và hỏi lại** thay vì
  làm bừa. Mở rộng cho cả các câu về tốc độ, độ sáng, khử sương và giờ giấc.
- **"Sấy kính" hiểu lại bình thường**: bản thử trước đó vô tình chặn nhầm chính câu này.
- **"Xác nhận" và "chốt cửa" không còn bị nghe nhầm** sang chuyện sạc pin / cốp xe.
- **Micro không còn bị bỏ quên khi bấm nói lúc xe đang khởi động**: trước đây nếu thả nút nói sớm
  trong lúc xe chưa sẵn sàng, micro có thể ở trạng thái mở ngầm. Nay luôn được đóng đúng lúc.
- **Xe thôi chỉnh chế độ lái / hồi năng lượng lúc đang ngủ**: mỗi lần khởi động hoặc thức giấc, xe
  từng thử ghi lại các thiết lập này kể cả khi máy chưa nổ — vừa không có tác dụng vừa tốn điện.
  Nay chỉ làm khi xe thật sự sẵn sàng; lúc anh ngồi trong xe chưa nổ máy thì vẫn chỉnh được như cũ.
- **Nút "Tối ưu Google Maps cho đầu xe"**: chỉnh sẵn Maps cho màn hình xe (bỏ nghiêng 3D và lớp giao
  thông cho đỡ giật). Bấm trong Cài đặt → Màn hình & hệ thống, hoặc tự chạy sau khi cài Maps.
- **Có bộ nhận dạng "Hi Geely" mới, nhẹ hơn cho máy** — nhưng tính năng nghe gọi tên vẫn **ĐANG TẮT**
  vì trước đó anh đã tắt trong Cài đặt; bản cập nhật KHÔNG tự bật lại lựa chọn đó. Muốn dùng thì bật ở
  hiện CHƯA có nút bật/tắt nào trên xe lẫn trên điện thoại (xem mục 1.1.4).
  (Đính chính 16/09: câu ở bản phát hành đầu ghi nhầm là "bản này bật lại" — sai, xem mục 1.1.4.)

## PhoneConnect 1.1.3

- **Quét QR ghép đôi xong là dùng được ngay**: trước đây sau khi quét, thẻ cài đặt vẫn trỏ về địa chỉ
  xe cũ nên hay báo lỗi kết nối cho tới khi mở lại app.
- **Nút "Tối ưu Google Maps cho đầu xe"** trong màn Ứng dụng, chỉnh Maps trên xe ngay từ điện thoại.
- Nhiệt độ điều hòa chỉnh từ điện thoại dùng chung giới hạn với xe (17–32 °C), không còn lệch.

## CarConnect 1.1.2

- **"Điều hòa mát nhất" không còn bị hiểu thành nóng nhất**: xe khách 14/09 nói câu này, xe đặt 32 °C
  và đọc "Nhiệt độ 32 độ"; "bật điều hòa mức thấp nhất" từng thành quạt MẠNH NHẤT, "làm nóng nhanh"
  từng thành bật lạnh. Nay xe không bao giờ đảo mát ↔ nóng, thấp ↔ cao khi phải đoán câu gần đúng
  (im rồi hỏi lại còn hơn làm ngược), và có sẵn các câu "điều hòa/máy lạnh mát nhất, lạnh nhất,
  mức thấp nhất, làm ấm nhanh".
- **Lạnh nhất là 17 °C (mức "Lo" của xe), không phải 16**: bản cũ gửi 16 nên xe từ chối và báo "Đã bỏ
  qua" (7 lượt trên xe khách 14/09). Nói "mười sáu độ" xe vẫn hiểu và đặt 17; điện thoại/màn hình xe
  cũng không cho chỉnh dưới 17.
- "Chuyển sang chế độ comford" (xe nghe sai chữ cuối của comfort) nay hiểu lại như bản 1.0.67, vẫn hỏi
  xác nhận trước khi đổi chế độ lái.

## CarConnect 1.1.1

- **Giọng nói sau khi cập nhật không còn "Đang xử lý…" hàng phút**: 1.1.0 đổi sang mô hình nhận
  dạng mới nên xe khách phải tải lại (~vài phút); trong lúc tải, bản cũ để việc tải chiếm luôn
  luồng xử lý giọng nói — bấm nói là treo tới khi tải xong (đo trên xe khách 14/09: 5,6 phút).
  Nay tải chạy luồng riêng; tải lỗi (xe vừa boot chưa có Wi-Fi) tự thử lại giãn dần 30 s → 10 phút
  và tải ngay khi có mạng trở lại — cả mô hình chính lẫn mô hình "Hi Geely".
- **Hết toast "Vui lòng kết nối điện thoại với xe bằng cáp dữ liệu USB…" khi bấm nút nói trên
  vô-lăng**: toast này của phần mềm CarPlay trong xe, app nay tự tắt riêng toast của phần mềm đó
  lúc khởi động (CarPlay/Android Auto vẫn dùng bình thường, chỉ mất mấy toast phụ như "Đã kết nối").
- **Chưa có mô hình nhận dạng (đang tải sau cập nhật) thì xe báo "Đang tải model nhận dạng giọng nói, chưa nghe
  được"** và KHÔNG tạm dùng nhận dạng đám mây thay thế (chủ xe chốt 14/09) — giọng nói trong cabin không bay lên
  máy chủ trong lúc chờ; chọn "Trực tuyến" trong Cài đặt thì vẫn dùng đám mây như cũ.
- Lượt nói đầu tiên ngay sau khi app khởi động không còn chờ bảng kéo câu dựng xong (tối đa 2,5 s
  rồi dùng câu nghe thô).
- **Điều khiển từ xa qua 4G nay ký từng lệnh**: xe chỉ nhận lệnh có chữ ký đúng khoá relay, gửi
  trong vòng 5 phút và không lặp lại — kẻ lạ vào được kênh cũng không giả được điện thoại của bạn.
  **Phải cập nhật CẢ xe lẫn PhoneConnect lên 1.1.1**; điện thoại bản cũ sẽ nhận thông báo
  "Cập nhật PhoneConnect để dùng điều khiển từ xa".
- **Khoá relay phải đủ mạnh**: nhập khoá ngắn hơn 16 ký tự hex thì xe từ chối và báo rõ; nút sinh
  khoá / mã QR nay tạo khoá 32 ký tự.
- **Cài app, tắt máy, đóng mọi ứng dụng, sửa kho câu lệnh từ điện thoại luôn cần mã bảo vệ (QR)**
  kể cả khi công tắc "Yêu cầu token" đang tắt — lệnh điều hoà, kính, cửa… vẫn như cũ.
- Kho câu lệnh giọng nói tải từ điện thoại không còn nhận được lệnh nguy hiểm (gỡ app, tắt máy…).
- **Bản cập nhật phải có chữ ký của chủ dự án**: xe chỉ tải bản mới khi danh mục cập nhật (GitHub
  hoặc máy chủ) mang chữ ký đúng khoá; ai chiếm được máy chủ hay kho GitHub cũng không ép được xe
  cài bản lạ. Thiếu chữ ký thì xe im, không tải.
- **Gọi "Hi Geely" rồi nói lệnh một hơi nay nhận đúng** ("hi geely giảm quạt gió" trước đây bị
  bỏ vì xe tưởng thiếu câu gọi).
- **Xe hỏi "mở kính lái?" mà bạn nói "đóng đi" thì xe hỏi lại**, không còn hiểu là đồng ý rồi hạ
  kính; câu trả lời ngược chiều lần hai thì xe bỏ qua.
- **"Mở cả bốn cửa" / "mở 4 cửa" = hạ bốn kính** (chủ xe chốt 13/09); kho câu lệnh tự cập nhật
  các câu đã đổi nghĩa dù xe đã lưu bản cũ.
- **Cửa sổ hỏi-đáp không còn nghe nhầm chuyện trong cabin**: sau khi xe hỏi "đi đâu?", câu nói
  không gọi xe / không bấm nút sẽ không bị coi là điểm đến; hết giờ bấm nút thì câu hỏi cũng đóng.
- **Chia đôi màn hình không rơi về kiểu docked** trên xe đã bật freeform (kiểu docked từng làm
  treo hệ thống khi đang chạy 12,6 km/h); app bản đồ không bao giờ bị ép tắt khi thử lại.
- **Tự cập nhật bền hơn**: cài thất bại không còn tải lại 12,7 MB vô hạn (giãn dần, tối đa 3
  lần/ngày); không tự hạ cấp âm thầm; cài ngầm xong không đè màn hình khi xe đang chạy.
- **Kết nối điện thoại**: đứt mạng im lặng 10 phút mới coi là mất kết nối (trước 30 s dễ rớt khi
  xe qua vùng sóng yếu); nhập sai mã bảo vệ 5 lần trong 1 phút thì khoá 5 phút theo máy gửi;
  mỗi máy tối đa 4 kết nối; app hệ thống (bản đồ, SystemUI…) không bị tắt/gỡ từ xa.
- **Riêng tư**: đoạn ghi âm chỉ được lưu khi bạn bấm nút nói (không còn lưu lượt gọi "Hi Geely"
  kèm câu chuyện trước đó); công tắc "Gửi mẫu giọng nói để cải thiện" trong Cài đặt › Giọng nói —
  mặc định tắt; vị trí xe gửi kèm nhật ký nay làm tròn ~1 km.
- **Watchdog không còn tự khởi động lại xe khi bạn chủ động tắt hết module** (tưởng nhầm là
  tiến trình chết); bộ đếm crash không bị đồng hồ xe nhảy giờ làm sai; nút vô-lăng chỉ xử lý đúng
  phím đã cấu hình, bấm liên tiếp có trần.
- **Giữ chế độ lái / hoàn năng lượng lúc xe ngủ**: cổng "xe ngủ + màn tắt" nay hoạt động thật
  (bản cũ đọc trạng thái sai tiến trình nên không bao giờ chặn) — hết loạt lỗi ghi lúc 2–4 giờ
  sáng; ECU từ chối thì thôi, không ghi lặp 9–24 lần mỗi lần thức; ghi VHAL treo quá 0,8 s tự bỏ.
- Chữ trong app và tài liệu nói đúng hành vi: kính điều khiển từ floater/điện thoại đi thẳng,
  không hỏi lại (chủ xe chốt 13/09) — cẩn thận khi xe đang chạy.
- **Xe không còn gửi tiếng cabin lên máy chủ khi không ai gọi** (14/09): trước đây mỗi lượt xe tự
  nghe mà không ra chữ vẫn tải đoạn ghi âm và ghi nhật ký như một lệnh (30/43 lượt trong 24 giờ
  đầu bản 1.1.0 là tiếng ồn cabin); nay chỉ lượt bấm nút / gọi "Hi Geely" mới được ghi, và lượt
  tự nghe rỗng không ngắt nhạc.
- Thức xe không còn kích hoạt hai lần trong cùng một nhịp (nhịp canh 60 s chạy trùng lúc xe vừa
  thức); trạng thái "muốn giữ chế độ lái" chốt một lần khi hẹn, không đọc lại lúc áp.
- Cổng kết nối điện thoại bền hơn: lỗi tạm thời khi nhận kết nối không làm chết cổng 44700 / 8876;
  điện thoại ngắt trước khi gửi mã không bị tính là nhập sai; kết nối treo lúc gửi bị cắt sau 10 s
  thay vì kẹt cả nhịp tim; tối đa 8 kết nối đang chờ mã.
- Nhật ký lỗi gửi máy chủ đếm lại từ đầu mỗi bản (không mang số cũ từ bản trước); sự kiện kích
  hoạt mã không còn kèm tên chủ mã.

## CarConnect 1.1.0

- **Gọi "Hi Geely" đánh thức xe trở lại**: từ bản 11/09 xe chỉ nghe bằng bộ nhận từ khoá mới nên
  câu gọi quen thuộc không còn tác dụng. Nay xe nghe lại bằng đúng cách đã chạy ổn trước đây, bộ
  nhận từ khoá chỉ là lớp cộng thêm; gọi xong xe không mở phiên nghe hai lần.
- **Không đẩy tiếng trong cabin lên đám mây khi rảnh**: khi xe đang ở chế độ nhận dạng trực tuyến,
  lúc không ai gọi xe thì micro không gửi gì ra ngoài.
- **Xe tự báo tình trạng bộ nhận từ khoá** trong nhật ký để lần sau nếu "Hi Geely" không ăn, biết
  ngay là do đâu.
- **Bản 1.0.67/1.0.68 trên các xe khác có tiếng lại**: gói giọng đọc bị mất trên máy chủ từ 08/09
  khiến xe chỉ kêu "bíp" — đã đưa lại, không cần cập nhật app cũng có tiếng.

## CarConnect 1.0.81

- **Xe không còn tự đoán mức quạt khi nghe không rõ**: trước đây có lúc bạn nói một câu không hề
  nhắc con số nào mà xe vẫn tự đặt quạt về mức 1 hoặc mức 3. Nay nghe không rõ thì xe im, không
  đoán bừa.
- **"Giảm độ sáng" nay đúng là giảm sáng**: trước đây câu này làm màn hình **tắt đen hoàn toàn**,
  che cả bản đồ và camera lùi. Nay màn chỉ giảm còn 30 % và vẫn dùng được. Muốn tắt hẳn thì nói
  "tắt màn hình" như cũ.
- **Nhận lệnh nhanh hơn rõ rệt**: đo trên xe khi bấm nút nói, thời gian máy giải mã giảm khoảng
  một nửa.
- **Không còn mất lệnh khi bạn nói câu dài**: câu dài mà máy giải mã hơi lâu thì trước đây bị bỏ
  luôn dù đã nghe đúng; nay xe chờ thêm một chút để trả lời bạn.
- **"Tắt TV Go" nay đóng đúng ứng dụng** thay vì có lúc mở nó lên.

## CarConnect 1.0.79

- **Bấm nút micro ngắt lời xe tức thì (Barge-In)**: khi xe đang nói phản hồi, người lái bấm nút mic trên vô-lăng xe sẽ im lặng ngay và lắng nghe trọn vẹn câu lệnh mới, không bị nuốt âm nửa giây đầu và nhạc không tự ý phát át tiếng người lái.
- **Triệt tiêu hiện tượng đơ CPU khi chạm nút**: bấm nút nhanh hoặc tiếng click cơ học không còn làm nghẽn CPU hay làm tắt nhầm micro.
- **Tránh kích hoạt nhầm**: các câu nói thông thường như "ghi lý do" không còn kích hoạt nhầm tính năng giọng nói.
- **Tối ưu kho dữ liệu**: dọn sạch và đồng bộ dữ liệu kiểm thử thực tế giúp ứng dụng nhẹ hơn và phản hồi ổn định hơn.

## PhoneConnect 1.1.2

- **Xe từ chối vì thiếu mã bảo vệ thì có nút "Quét QR ngay"** (cài APK, đẩy tệp) — không còn phải tự
  mò vào Cài đặt để ghép mã; chụp màn hình xe không còn đòi mã.
- Màn Điều hoà: nhiệt độ thấp nhất chỉnh được là **17 °C** (mức "Lo" của xe) — trước cho kéo xuống 16
  nhưng xe không nhận.
- Máy ảo/thử nghiệm: banner "Có bản cập nhật mới" giả không còn tự bật (chỉ khi bật cờ thử).

## PhoneConnect 1.1.1

- **Điều khiển từ xa qua 4G ký từng lệnh** — cần CarConnect 1.1.1 trên xe; xe bản cũ sẽ hiện
  "Xe chưa cập nhật" trong lịch sử lệnh.
- **Khoá relay**: chỉ lưu khi đủ 16 ký tự hex trở lên, gõ sai định dạng là báo đỏ ngay dưới ô nhập.
- Gỡ lối cài thử ẩn khỏi bản phát hành; tắt sao lưu token/khoá relay lên đám mây của Android.
- **Bản cập nhật phải có chữ ký của chủ dự án** (như CarConnect 1.1.1): danh mục thiếu/sai chữ ký
  thì app không tải; tự cập nhật luôn đòi mã SHA của file APK.
- **Chuyển sang kênh Dev không còn báo "có bản mới" rồi cài thất bại** khi kênh đó chưa có bản
  cao hơn bản đang cài.
- Tra địa chỉ hành trình gửi toạ độ làm tròn ~100 m và giãn cách ≥1 giây khi phải dùng máy chủ
  ngoài; lệnh gửi qua 4G lúc mạng đứt báo lỗi ngay thay vì im lặng.
- Chữ dưới thanh kính: "Kính đi thẳng, không hỏi lại — cẩn thận khi xe đang chạy."
- Kênh 4G: xe trả 3 dòng liên tiếp không qua xác minh chữ ký thì điện thoại ĐÓNG kênh và rơi về
  Wi-Fi/Bluetooth, không giữ kết nối "đã nối" mà bỏ mọi dòng; kho ứng dụng (Cửa hàng) chỉ nhận
  danh mục có chữ ký, như bản cập nhật.

## PhoneConnect 1.1.0

- Đồng bộ theo bản CarConnect 1.1.0. Không có thay đổi nào ở phía điện thoại.

## PhoneConnect 1.0.66

- Đồng bộ theo bản CarConnect 1.0.80. Không có thay đổi nào ở phía điện thoại.

## PhoneConnect 1.0.64

- Bản đồng bộ số hiệu tương thích với ứng dụng trên xe. Không có thay đổi về tính năng hay giao diện.

## CarConnect 1.0.78

- **Sửa nghe nhầm nguy hiểm**: nói "mở cửa sổ" trước đây có lúc bị hiểu thành **mở khoá cửa xe**,
  "mở cốp trước" thành mở cốp sau. Nay khi câu ngắn có thể là phần đầu của một câu dài hơn thì xe
  chờ nghe hết câu. Nói hai lệnh "phát ..." sát nhau cũng không còn gõ lẫn từ khoá cũ vào lượt sau.
- **Tôn trọng lựa chọn tắt micro**: ai đã tắt "nghe liên tục" thì cập nhật xong xe vẫn giữ nguyên
  là tắt. Bản trước lỡ bật lại mà không hỏi — nay không còn.
- **Nghe trọn câu hơn**: không nuốt tiếng đầu khi nói liền tay, và câu ghép như "bật điều hoà và
  đóng kính" tách được thành hai lệnh.
- **Nghe không rõ thì nói rõ lý do**: thay vì im lặng, xe cho biết đang quá ồn, giọng quá nhỏ, hay
  chưa nghe được câu nào.
- **Gọi "Hi Geely" không cần chạm**: xe lắng nghe từ khoá đánh thức liên tục, mặc định bật. Muốn
  xe chỉ nghe khi bấm nút thì tắt mục nghe liên tục trong Cài đặt giọng nói.

## PhoneConnect 1.0.63

- Bản đồng bộ số hiệu với ứng dụng trên xe. Không có thay đổi nào về tính năng hay giao diện.

## CarConnect 1.0.76

- **Chuẩn hóa đa ngôn ngữ toàn diện**: 100% tài nguyên giao diện tiếng Việt & tiếng Anh khớp nhau hoàn hảo.
- **Nâng cấp giao diện điều khiển**: Tối ưu hoá thanh TopBar, thanh Dock Flyme Auto OEM và các thẻ điều khiển trạng thái xe.
- **Tiện ích và cập nhật OTA**: Cải thiện thông báo tiến trình tải và cập nhật phiên bản mới trực quan trên màn hình xe.

## PhoneConnect 1.0.61

- **Chuẩn hóa đa ngôn ngữ song ngữ**: Hoàn thiện 100% giao diện tiếng Việt và tiếng Anh cho tất cả các màn hình điều khiển.
- **Giao diện thẻ cập nhật & nhật ký**: Tối ưu độ tương phản chế độ tối (Dark mode) và làm mới danh mục nhật ký hành trình.
- **Thao tác nhanh mượt mà**: Nâng cấp trải nghiệm điều khiển cửa, kính xe, cốp trước và sổ theo dõi bảo dưỡng điện tử.

## CarConnect 1.0.69

- **Nút nổi truy cập nhanh**: một nút tròn luôn nổi trên màn hình, chạm là ra bảng điều khiển
  nhanh. Kéo thả tự dính mép, tự mờ đi khi không dùng, và tự chọn được những chức năng muốn hiện.
- **Quản lý nhạc & hình nền từ điện thoại**: xem, nghe thử, xoá nhạc và ảnh nền trên xe ngay trên
  điện thoại; đặt hình nền hoặc để xe tự đổi ảnh luân phiên.
- **Điều hoà thêm hướng gió**: chọn thổi mặt, thổi chân, mặt và chân, hay sấy kính. Có thêm chế độ
  **đảo gió tự động** — cứ 90 giây xe tự luân phiên mặt và chân cho đều hơi mát.
- **Mở cốp trước, mở khoá cốp sau** bằng giọng nói hoặc từ điện thoại.
- **Ghép đôi điện thoại bằng mã QR**: khỏi gõ tay địa chỉ IP và mã kết nối. Mã chỉ sống 2 phút rồi
  tự hết hạn cho an toàn.
- **Chế độ bảo dưỡng 1 chạm**: ẩn hết nút nổi và biểu tượng tuỳ biến trước khi mang xe đi bảo hành,
  xong bấm một lần là trả lại y như cũ.
- **Trợ lý hỏi đáp** (mặc định TẮT, bật trong Cài đặt): bấm giữ nút nói rồi hỏi một câu hỏi thật,
  xe trả lời. Nghe nhầm câu lệnh thì xe vẫn nói "chưa hiểu" chứ không trả lời bừa.
- **Tự cập nhật ngầm**: xe tự kiểm tra bản mới 30 phút một lần và chỉ cài khi đã đỗ, không cần mở
  ứng dụng. Thêm phím nhạc trên vô-lăng và biểu tượng nhiệt độ pin trên thanh trạng thái.

## PhoneConnect 1.0.54

- **Quản lý nhạc & hình nền trên xe**: xem danh sách, nghe thử ngay trên điện thoại, xoá bớt, gửi
  bài mới lên xe, đặt ảnh nền hoặc bật tự đổi ảnh luân phiên.
- **Quét mã QR trên xe để ghép đôi**: không phải gõ tay địa chỉ IP, cổng hay mã kết nối nữa.
- **Mất sóng không mất lệnh**: lệnh bấm lúc rớt kết nối được xếp hàng và tự gửi lại khi nối lại được.
- **Nhắc cập nhật rõ ràng hơn**: có bản bắt buộc thì hiện hẳn hộp thoại kèm lý do, không để lỡ.
- Điều khiển thêm hướng gió điều hoà, đảo gió tự động, mở cốp trước và mở khoá cốp sau.

## CarConnect 1.0.65

- **Nghe chính xác hơn**: tắt bộ lọc tiếng ồn và bỏ ràng buộc từ khoá của bản trước — hai thứ này
  đo lại trên kho ghi âm thật thì làm xe nghe **tệ hơn**, và từng khiến xe làm sai lệnh.
- **Hết lỗi đóng nhầm cửa kính**: nói "đóng kính tài lái" trước đây xe đóng **toàn bộ** kính còn lại.
- Nói "tắt tiếng cảnh báo" không còn bị hiểu thành **tắt WiFi**.
- Nói hụt câu kiểu "mở ứng dụng nhé" không còn bị hiểu thành **đóng hết ứng dụng**.
- **Xe đang chạy không còn bị chặn lệnh nào**: chia đôi màn hình, mở 2 ứng dụng, đóng ứng dụng…
  đều làm được khi đang lái. Vẫn hỏi lại trước khi chỉnh kính, chế độ lái và phanh tái sinh.
- Mở bài hát trên YouTube nay ra **thẳng trang kết quả tìm kiếm** thay vì chỉ mở app.

## PhoneConnect 1.0.50

- Đồng bộ theo bản xe mới; không đổi tính năng trên điện thoại.

---

## CarConnect 1.0.59

- Tự hé kính khi mở cửa: **nay chạy được thật**. Trước đây bật công tắc mà kính không bao giờ hạ,
  vì app hiểu sai mã trạng thái cửa của đầu xe nên tưởng cửa lúc nào cũng đang mở.
- Mức hé đổi từ 5% sang **7%** — mô-tơ kính từ chối mọi lệnh dưới 7%, đặt 5% là kính đứng im.
- Công tắc gộp còn **một dòng cho cả 4 cửa** thay vì 4 dòng riêng.
- Gạt công tắc trên màn hình xe nay **hiện sang điện thoại ngay**, không phải đợi kết nối lại.
- Lệnh kính báo kết quả trung thực hơn: trước đây có lúc báo "đã đóng kín" trong khi kính vẫn hở.

## PhoneConnect 1.0.44

- Màn *Cài đặt xe*: mục tự hé kính gộp còn **một dòng cho cả 4 cửa**.
- Không còn gạt được công tắc khi chưa kết nối xe — trước đây gạt xong nó tự nhảy về chỗ cũ.
