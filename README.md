# Geely EX2 — bản phát hành app

Kho chứa bản phát hành (release) của bộ app điều khiển xe **Geely EX2** — 3 app, mỗi cái
chạy trên một thiết bị khác nhau, xem bảng bên dưới.

> ⚠️ **TRẠNG THÁI: BETA — ĐANG THỬ NGHIỆM, CHƯA NÊN CÀI**
>
> CentralCar / CentralPhone đang ở giai đoạn **thử nghiệm (beta)** — được **team phát triển
> thử nghiệm trên xe thật**, chưa hoàn tất toàn bộ quá trình kiểm thử. **Sẽ chính thức
> release khi quá trình test trên xe thật đạt yêu cầu.**
>
> **KHÔNG NÊN CÀI** lên xe/điện thoại dùng hằng ngày khi chưa tới thời điểm đó.
> Cài tức là tự chịu trách nhiệm: app có thể lỗi, chưa ổn định, hoặc làm thay đổi hành vi
> hệ thống trên xe. Báo lỗi/góp ý gửi về nhà phát triển trước khi dùng đại trà.

## Các app trong kho này

| File | Cài ở đâu | Chức năng |
|---|---|---|
| `CentralCar-system(Không cài).apk` | **Màn hình xe Geely EX2** (Android 9) | App chạy trên xe: hiển thị thông số (tốc độ, pin, nhiệt độ), điều khiển xe qua VHAL (gương, kính, khoá…), ra lệnh giọng nói (wake word + PTT, nhận diện tiếng Việt, Vosk local + Google dự phòng), nhận lệnh từ xa qua cloud relay, App store cài thêm app cho xe, kiểm tra cập nhật. |
| `CentralPhone(Không cài).apk` | **Điện thoại Android** | App điều khiển xe từ xa: gửi lệnh tới xe qua cloud relay (không cần cùng Wi-Fi), chỉnh sửa câu lệnh giọng nói. **Sắp tới: cài app cho xe online qua cloud — giống CentralPC (cài app lên xe từ xa, không cần ADB/máy tính).** |
| `CentralPC(MacOS).dmg` | **Máy Mac** (Apple Silicon) | App quản lý trên máy tính: kết nối xe qua ADB, giao diện web `localhost:8848`, cài/gỡ app cho xe, chạy lệnh adb, cấu hình. |
| `CentralPC(Windows).exe` | **Máy Windows** | Bản Windows của CentralPC — cùng chức năng như bản macOS. |

> ✅ **CentralPC (`.dmg` / `.exe`) đã được kiểm thử và phát hành chính thức** — không còn ở
> giai đoạn beta. Chỉ **CentralCar / CentralPhone** đang beta và chưa nên cài.

## Chi tiết tính năng từng app

### 🚗 CentralCar — app trên màn hình xe (Android 9)

- **Thông số lên thanh trạng thái**: phần trăm pin (SOC), tốc độ km/h, nhiệt độ ngoài trời — kèm
  widget launcher, chỉnh vị trí từng biểu tượng
- **Chế độ lái**: Eco / Comfort / Sport + mức hồi năng lượng (thấp / trung bình / cao) — tự nhớ
  & khôi phục khi bật màn hình
- **Đèn viền nội thất**: bật/tắt + lịch hẹn giờ (chạy ngầm kể cả sau reboot)
- **AVAS**: tắt tiếng bíp cảnh báo người đi bộ + chỉnh âm lượng loa
- **Cửa & kính**: hé kính tự động khi mở cửa, đóng kính khi đóng cửa (tự bỏ qua khi xe đang chạy)
- **Điều khiển bằng giọng nói tiếng Việt** (~35 lệnh: đèn viền, WiFi, điều hoà, chế độ lái,
  khoá/mở cửa, kính, tắt màn hình…) — 3 tầng khớp lệnh + phản hồi bằng giọng nói (TTS)
- **Màn hình đen (blackout)** khi lái đêm + nút nổi truy cập nhanh (floater)
- **Điều khiển từ xa qua 4G** (cloud relay)
- **Cập nhật từ GitHub** (verify SHA-256) + App store cài thêm app
- **Nhận lệnh + cài APK từ xa** qua server `:44700` / `:8876` — không cần ADB/máy tính
- **Watchdog chống crash/bootloop** (tự khôi phục, an toàn)

### 📱 CentralPhone — app điện thoại

- **6 tab**: Tổng quan, Lái xe, Điều khiển, Điều hoà, Ứng dụng, Cài đặt
- **3 cách kết nối xe**: Bluetooth / WiFi cùng mạng / Cloud (4G) — tự động reconnect, chạy nền
- **Tổng quan**: tốc độ + pin %, chế độ lái, nhiệt độ ngoài trời, gear, odometer, quãng đường
  còn đi được, **áp suất lốp 4 bánh** (cảnh báo lốp thấp)
- **Điều khiển xe từ xa**: khoá/mở cửa, kính từng cửa (% mở), đèn viền, WiFi xe, scene
  (nghỉ ngơi / cắm trại)
- **Điều hoà**: bật/tắt A/C, nhiệt độ ±0.5°C, quạt gió, tuần hoàn, chế độ nhanh ECO, sấy kính
- **Quản lý app trên xe từ xa**: mở app, ẩn/hiện (không mất dữ liệu), gỡ cài đặt, gỡ kẹt PIP,
  chia màn hình 2 app
- **Cài APK lên xe không cần ADB** (đẩy qua `:8876`): chọn file APK hoặc **App store tải & cài
  tự động** (verify SHA-256)
- **Đồng bộ cài đặt xe**: widget thanh trạng thái, lịch đèn viền, auto-window, auto-WiFi,
  ghi nhớ chế độ lái/regen
- **Cập nhật CentralCar từ GitHub** — xe không cần internet (phone tải rồi đẩy qua)

### 💻 CentralPC — app máy tính (macOS / Windows)

- **Cứu hộ qua ADB**: hướng dẫn mở khoá ADB (firmware 1111/1114), tự tính mã kỹ thuật theo giờ,
  kiểm tra kết nối — adb được nhúng sẵn trong app
- **Tab ⚡ Cài nhanh**: bấm 1 nút là tải + cài (SmartTube, Waze, VietMap…) — hỗ trợ link
  GitHub blob / Google Drive / tải trực tiếp
- **Cài từ file / folder**: kéo-thả APK/XAPK/APKS/APKM, chọn đúng ABI, Doze whitelist chống
  giết nền, xử lý xung đột chữ ký, quét folder cài hàng loạt
- **Quản lý package trên xe**: ẩn/hiện app (không mất dữ liệu), gỡ cài đặt, đánh dấu yêu thích
- **Công cụ thiết bị**: chia màn hình 2 app, gỡ kẹt PIP (SmartTube), chạy lệnh shell tuỳ ý
- **Điều khiển xe trực tiếp** (không qua ADB): chế độ lái, hồi năng lượng, AVAS, đèn viền, WiFi,
  điều hoà, scene, khoá cửa, kính — kèm telemetry realtime
- **Hệ thống cấp mã kích hoạt** (xem mục "Kích hoạt mở thêm gì?" bên dưới)
- Chế độ demo (xem giao diện không cần xe), nhật ký realtime, đổi theme 🌓

**Quy tắc tên file:** APK có chữ `(Không cài)` là **đang thử nghiệm (beta)** — tải về xem/đánh
giá thì được, **chưa nên cài** lên xe/điện thoại dùng hằng ngày. Bản nào hết beta sẽ bỏ chữ này.
**CentralPC không mang chữ `(Không cài)`** — bản này **đã được kiểm thử và phát hành chính thức**.

## Cách cài

- **Lên xe (CentralCar):** dùng CentralPC trên máy tính (mục Cài nhanh / Cài app) cài
  `CentralCar-system(Không cài).apk`, hoặc `adb install` trực tiếp. App chạy trên màn hình xe.
- **Lên điện thoại (CentralPhone):** tải `CentralPhone(Không cài).apk` về, cho phép cài từ
  nguồn không rõ (Cài đặt → Bảo mật), cài như APK thường. Mở app → vào tab Cloud → kết nối xe.
- **Trên máy tính (CentralPC):** tải `.dmg` (Mac) hoặc `.exe` (Windows) → mở app → trình duyệt
  tự mở `http://localhost:8848` → dùng được ngay; muốn thêm tính năng thì **kích hoạt mã**
  (xem phần tiếp theo).

## Kích hoạt mở thêm gì?

CentralPC **dùng được ngay không cần kích hoạt** (cài app cho xe, quản lý file, chạy lệnh adb…).
Kích hoạt bằng **mã + số điện thoại** (do quản trị viên cấp, 1 mã = 1 người, 1 máy mặc định)
sẽ mở thêm:

- **Tab Điều khiển xe** — điều khiển xe qua VHAL (gương, kính, khoá…)
- **Tab Công cụ thiết bị** — công cụ quản trị thiết bị trên xe
- **Mục VietMap Live** trong Cài nhanh

## Báo lỗi / góp ý

- Đang trong giai đoạn beta nên rất cần phản hồi của anh/chị: lỗi gặp phải, màn hình bị kẹt,
  app chạy không ổn định…
- Gửi về **quản trị viên / nhà phát triển** kèm thông tin: đang chạy bản nào, thao tác gì thì
  lỗi, ảnh chụp màn hình (nếu chụp được).

## Ghi chú kỹ thuật (cho nhà phát triển)

- Xe/phone **từ chối cài nếu SHA-256 sai/thiếu** — mọi bản đặt lên đây phải verify trước khi push.
- APK chỉ đặt bản **system platform-signed** (bản user build không có quyền uid system,
  ghi VHAL/quản trị app sẽ lỗi).
- Quy trình phát hành tự động: `publish-artifacts.sh` trong repo code (tự build + đẩy lên đây).
