# Thư mục artifacts — bản phát hành APK

> ⚠️ **TRẠNG THÁI: BETA — ĐANG THỬ NGHIỆM, CHƯA NÊN CÀI**
>
> CentralCar / CentralPhone trong repo này đang ở giai đoạn **thử nghiệm (beta)** —
> được **team phát triển thử nghiệm trên xe thật**, chưa hoàn tất toàn bộ quá trình
> kiểm thử. **Sẽ chính thức release khi quá trình test trên xe thật đạt yêu cầu.**
>
> **KHÔNG NÊN CÀI** lên xe/điện thoại dùng hằng ngày khi chưa tới thời điểm đó.
> Cài tức là tự chịu trách nhiệm: app có thể lỗi, chưa ổn định, hoặc làm thay đổi hành vi
> hệ thống trên xe. Báo lỗi/góp ý gửi về nhà phát triển trước khi dùng đại trà.

Quyết định 2026-08-03: **code repo (`ToanMobile/GeelyEx2`) giữ private** — APK phát hành +
`update.json` + `apps.json` được đẩy sang **một repo GitHub public riêng** (xe/phone tải qua
URL public, không cần token GitHub).

## Luồng phát hành bản mới (CentralCar system)

1. **Build**: `CentralCar/scripts/build-system-apk.ps1` (Windows, ký platform testkey — xem
   `CentralCar/docs/system-install.md`). Cũng có thể build từ macOS: `assembleSystemRelease`
   rồi ký bằng key platform (`.pk8` + `.x509.pem`) qua `apksigner`.
2. **Copy APK** vào đây: `artifacts/geely-ex2-tools-system-platform-signed.apk`.
3. **Sửa `update.json`** (repo root — file này được đẩy sang repo public):
   - `versionCode`/`versionName` = version mới (nhớ `VERSION_CODE += 1`)
   - `apkUrl` → URL raw của APK **trong repo public** (chưa public repo thì ghi tạm đường dẫn
     dự kiến, đổi sau khi push)
   - `sha256` = `shasum -a 256 <apk>` (macOS/Linux) hoặc `Get-FileHash` (Windows)
4. **Nếu APK là app store** (cài được từ CentralPhone → App store): cập nhật `apps.json`
   tương ứng (packageName `com.toanmobile.geelytools`, version, SHA-256, downloadUrl).
5. **Push cả 3 file lên repo public** (thư mục gốc repo public). Bắt buộc:
   - `update.json` + `apps.json` + APK nằm ở nhánh `main` của repo public
   - URL trong `update.json`/`apps.json` trỏ đúng path trong repo public
6. **Đổi URL trong code** (chỉ 1 lần, khi repo public có tên): `UpdateDefaults` trong
   `shared/src/main/kotlin/com/toanmobile/geely/CarProtocol.kt` — `UPDATE_JSON_URL` +
   `APP_CATALOG_URL` → `https://raw.githubusercontent.com/<user>/<repo-public>/main/...`
   rồi build lại CentralCar + CentralPhone.

## 4 app trong repo này — cái nào dùng cho thiết bị nào

| File | Dành cho | Chức năng |
|---|---|---|
| `CentralCar-system(Không cài).apk` | **Màn hình xe Geely EX2** (Android 9, ký AOSP platform — có quyền hệ thống) | App chạy trên xe: hiển thị thông số (tốc độ, pin, nhiệt độ), điều khiển xe qua VHAL (gương, kính, khoá…), ra lệnh giọng nói (wake word + PTT, Vosk local + Google dự phòng), nhận lệnh từ xa qua cloud relay (Supabase Realtime), App store cài thêm app cho xe, kiểm tra cập nhật. **⚠️ BETA — không nên cài** |
| `CentralPhone(Không cài).apk` | **Điện thoại Android** | App điều khiển xe từ xa: gửi lệnh tới xe qua cloud relay (không cần cùng Wi-Fi), App store cài app cho xe từ xa, chỉnh sửa câu lệnh giọng nói. Viết bằng Kotlin Multiplatform (bản iOS mới là shell tạm). **⚠️ BETA — không nên cài** |
| `CentralPC(MacOS).dmg` | **Máy Mac** (Apple Silicon) | App quản lý CentralPC: kết nối xe qua ADB (Wi-Fi, mở giao diện web `localhost:8848`), cài/gỡ app cho xe, chạy lệnh adb, cấu hình, hệ thống cấp phép bản quyền (mã kích hoạt + số điện thoại qua Supabase). Đây là bản phát hành chính thức. |
| `CentralPC(Windows).exe` | **Máy Windows** | Bản Windows của CentralPC — cùng chức năng như bản macOS. |

**Quy tắc tên file:** APK có chữ `(Không cài)` là **đang thử nghiệm (beta)** — tải về xem/đánh giá
thì được, **chưa nên cài** lên xe/điện thoại dùng hằng ngày. Bản nào hết beta sẽ bỏ chữ này.

## Ghi chú

- `update.json`/`apps.json` trỏ `ToanMobile/geely-ex2-artifacts/main` (repo public riêng —
  quyết định 2026-08-04). **404 cho tới khi repo được tạo + push**:
  tạo tại https://github.com/new?name=geely-ex2-artifacts&visibility=public rồi đẩy
  `update.json` + `apps.json` + APK vào nhánh main.
- Xe/phone **từ chối cài nếu SHA-256 sai/thiếu** — verify trước khi push.
- APK chỉ nên đặt bản **system platform-signed** (bản user build không có quyền uid system,
  ghi VHAL/quản trị app sẽ lỗi).
