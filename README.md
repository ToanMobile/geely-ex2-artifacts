# Thư mục artifacts — bản phát hành APK

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

## Ghi chú

- `update.json`/`apps.json` trỏ `ToanMobile/geely-ex2-artifacts/main` (repo public riêng —
  quyết định 2026-08-04). **404 cho tới khi repo được tạo + push**:
  tạo tại https://github.com/new?name=geely-ex2-artifacts&visibility=public rồi đẩy
  `update.json` + `apps.json` + `CentralCar-system.apk` + `CentralPhone.apk` vào nhánh main.
- Xe/phone **từ chối cài nếu SHA-256 sai/thiếu** — verify trước khi push.
- APK chỉ nên đặt bản **system platform-signed** (bản user build không có quyền uid system,
  ghi VHAL/quản trị app sẽ lỗi).
