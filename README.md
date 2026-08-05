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
| `CentralPhone(Không cài).apk` | **Điện thoại Android** | App điều khiển xe từ xa: gửi lệnh tới xe qua cloud relay (không cần cùng Wi-Fi), App store cài app cho xe từ xa, chỉnh sửa câu lệnh giọng nói. |
| `CentralPC(MacOS).dmg` | **Máy Mac** (Apple Silicon) | App quản lý trên máy tính: kết nối xe qua ADB, giao diện web `localhost:8848`, cài/gỡ app cho xe, chạy lệnh adb, cấu hình, quản lý bản quyền (mã kích hoạt). |
| `CentralPC(Windows).exe` | **Máy Windows** | Bản Windows của CentralPC — cùng chức năng như bản macOS. |

**Quy tắc tên file:** APK có chữ `(Không cài)` là **đang thử nghiệm (beta)** — tải về xem/đánh
giá thì được, **chưa nên cài** lên xe/điện thoại dùng hằng ngày. Bản nào hết beta sẽ bỏ chữ này.

## Cách cài

- **Lên xe (CentralCar):** dùng CentralPC trên máy tính (mục Cài nhanh / Cài app) cài
  `CentralCar-system(Không cài).apk`, hoặc `adb install` trực tiếp. App chạy trên màn hình xe.
- **Lên điện thoại (CentralPhone):** tải `CentralPhone(Không cài).apk` về, cho phép cài từ
  nguồn không rõ (Cài đặt → Bảo mật), cài như APK thường. Mở app → vào tab Cloud → kết nối xe.
- **Trên máy tính (CentralPC):** tải `.dmg` (Mac) hoặc `.exe` (Windows) → mở app → trình duyệt
  tự mở `http://localhost:8848` → **kích hoạt bằng mã + số điện thoại** do quản trị viên cấp
  (1 mã = 1 người, 1 máy mặc định).

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
