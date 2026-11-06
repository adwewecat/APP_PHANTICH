# SỔ TAY DỰ ÁN & HƯỚNG DẪN DÀNH CHO GEMINI / A.I / DEVELOPER

> **DỰ ÁN:** APP_PHANTICH (TÍCH HỢP REVERSE ENGINEER ANYTHING - REA)  
> **KHO LƯU TRỮ CHÍNH (ORIGIN GITHUB REPO):** [https://github.com/adwewecat/APP_PHANTICH.git](https://github.com/adwewecat/APP_PHANTICH.git)  
> **KHO NGUỒN GỐC (UPSTREAM REPO):** [https://github.com/morluto/rea](https://github.com/morluto/rea)  
> **NGÀY KHỞI TẠO TÍCH HỢP:** 2026-11-06  
> **FILE CHỈ DẪN CỐT LÕI:** `gemini.md` (Tài liệu này) & `README.md`

---

## 1. MỤC ĐÍCH CỦA FILE `gemini.md`

Tài liệu này là kim chỉ nam tối cao của dự án **APP_PHANTICH**, được tạo ra để đảm bảo:

1. **Tính liên tục tuyệt đối khi cài lại Win hoặc đổi máy:**  
   Bất kỳ khi nào người dùng cài lại hệ điều hành Windows, chuyển sang máy tính mới hoặc môi trường làm việc bị xóa trắng, khi một AI (Gemini, Claude, GPT, v.v.) hoặc một Lập trình viên (Developer) khác mở thư mục dự án này ra đọc file `gemini.md`, họ sẽ ngay lập tức:
   - Hiểu được 100% bản chất của dự án, kiến trúc hệ thống và cách thức hoạt động.
   - Nắm rõ các quy tắc làm việc bất di bất dịch cần phải tuân thủ nghiêm ngặt.
   - Biết chính xác môi trường cần thiết lập và cách khôi phục dự án.
   - Biết rõ trạng thái hiện tại và **phải làm gì tiếp theo** mà không cần người dùng giải thích lại từ đầu.
2. **Quy định ghi chép trước khi làm (Pre-Action Logging):**  
   Trước khi bắt tay vào làm hay sửa bất kỳ một vấn đề nào (dù lớn hay nhỏ), AI hoặc Developer bắt buộc phải ghi chú mục đích, kế hoạch và các file dự kiến thay đổi vào tài liệu này trước khi đụng vào code.

---

## 2. QUY TẮC BẤT DI BẤT DỊCH CỦA DỰ ÁN (PROJECT RULES)

Tất cả AI (Gemini, Copilot, Claude...) và Developer tham gia phát triển dự án này **BẮT BUỘC** phải tuân thủ nghiêm ngặt 5 quy tắc vàng sau:

### 🔴 Quy tắc 1: ĐẨY CODE LÊN GITHUB NGAY LẬP TỨC (MANDATORY IMMEDIATE PUSH)

- **Bất kỳ lúc nào thêm tính năng hoặc chỉnh sửa code**, sau khi kiểm tra xong phải lập tức tạo commit rõ ràng và `git push` về kho GitHub chính:
  ```powershell
  git add .
  git commit -m "feat/fix: <mô tả chi tiết việc vừa làm>"
  git push origin main
  ```
- URL Repo chính thức: `https://github.com/adwewecat/APP_PHANTICH.git`
- Tuyệt đối không được giữ code cục bộ mà không đẩy lên GitHub. Bất kỳ thay đổi nào cũng phải đồng bộ ngay.

### 🔴 Quy tắc 2: GHI CHÉP VÀ LƯU VẾT TRƯỚC KHI THỰC HIỆN (PRE-ACTION LOGGING)

- Trước khi bắt đầu viết code hoặc sửa bất kỳ vấn đề gì:
  - Phải ghi nhận mục tiêu vào mục `5. NHẬT KÝ THAY ĐỔI & TIẾN ĐỘ` trong `gemini.md`.
  - Nếu là sửa lỗi (bug fix): ghi nhận hiện tượng lỗi, nguyên nhân gốc rễ và hướng xử lý.
- Sau khi hoàn thành:
  - Cập nhật kết quả thực tế, kết quả kiểm thử (test passed/build passed).

### 🔴 Quy tắc 3: CODE SẠCH HOÀN TOÀN, LOẠI BỎ CODE THỪA (CLEAN CODE)

- Build code phải hoàn toàn sạch sẽ.
- Bỏ triệt để các code dư thừa, code không sử dụng (dead code), biến không dùng, console log tạm bợ hoặc file thử nghiệm thừa thãi.
- Dọn dẹp các file rác, file tạm (scratch, temp files) trước khi commit.
- Giữ cấu trúc thư mục gọn gàng, chuẩn mực theo chuẩn kiến trúc của dự án.

### 🔴 Quy tắc 4: CHÚ THÍCH CODE ĐẦY ĐỦ VÀ RÕ RÀNG (IN-CODE DOCUMENTATION)

- Tất cả các module, class, hàm (function) và tính năng mới hoặc được sửa đổi đều phải có comment/docstring giải thích:
  - Chức năng của đoạn code là gì, phục vụ mục đích gì.
  - Các tham số đầu vào (parameters), kiểu dữ liệu và ý nghĩa.
  - Giá trị trả về (return value) và các trường hợp ngoại lệ (exceptions/edge cases).
  - Viết chú thích dễ hiểu (tiếng Việt hoặc tiếng Anh chuẩn) để AI hay Dev khác đọc lại code nắm bắt ngay tức thì.

### 🔴 Quy tắc 5: ĐẶC THÙ MÔI TRƯỜNG WINDOWS / POWERSHELL

- Trên Windows PowerShell, do chính sách bảo mật `ExecutionPolicy`, các lệnh gọi script `.ps1` (như `npm.ps1`, `npx.ps1`) có thể bị chặn.
- Luôn sử dụng lệnh **`npm.cmd`** và **`npx.cmd`** khi thực thi trong terminal PowerShell:
  ```powershell
  npm.cmd run <script>
  npm.cmd ci
  npm.cmd test
  ```

---

## 3. TỔNG QUAN KIẾN TRÚC DỰ ÁN APP_PHANTICH (TÍCH HỢP REA)

### 3.1. Bản chất của dự án

**APP_PHANTICH** được tích hợp từ nền tảng công nghệ mạnh mẽ của **REA (Reverse Engineer Anything)** — một bộ công cụ phân tích, giải mã và dịch ngược (Reverse Engineering) toàn diện, chạy hoàn toàn cục bộ (local-only), cung cấp:

1. **Giao diện dòng lệnh (CLI):** Thực thi phân tích trực tiếp qua terminal bằng `node scripts/rea.mjs <lệnh>` hoặc `rea <lệnh>`.
2. **Máy chủ MCP (Model Context Protocol Server):** Tích hợp sâu vào các AI Coding Agent (Gemini, Claude Code, Cursor, Codex, Windsurf...) cho phép AI tự động ra lệnh phân tích nhị phân, ứng dụng web, Electron, Android APK, .NET assembly... và trích xuất bằng chứng xác thực (evidence-backed findings).

### 3.2. Cấu trúc thư mục chi tiết

- `src/`: Toàn bộ mã nguồn cốt lõi bằng TypeScript (Node.js ES Modules):
  - `src/cli/`: Xử lý giao diện dòng lệnh, điều hướng cờ (flags) và tham số lệnh.
  - `src/mcp/`: Server MCP, định nghĩa bộ công cụ (tool catalog) cho AI Agent giao tiếp.
  - `src/analysis/` & `src/engines/`: Thuật toán phân tích cấu trúc nhị phân, decompiler, deobfuscation, CFG (Control Flow Graph).
  - `src/providers/`: Module tích hợp và điều khiển các engine dịch ngược (Ghidra, Hopper, IDA Pro, Cutter, JADX, Rizin/Radare2...).
  - `src/process/`: Quản lý an toàn các tiến trình phân tích độc lập.
- `bridge/`: Các module cầu nối với các engine chuyên dụng bên ngoài:
  - `bridge/ghidra/`: Java extension và bridge giao tiếp với Ghidra Decompiler.
  - `bridge/hopper_bridge.py`: Python bridge cho Hopper Disassembler.
  - `bridge/android/ReaJadxBridge.java`: Bridge phân tích mã nguồn APK qua JADX.
  - `bridge/pwndbg/`, `bridge/pwntools/`: Tích hợp phân tích lỗi crash bộ nhớ và khai thác an toàn.
- `scripts/`: Chứa entrypoint thực thi:
  - `scripts/rea.mjs`: Entrypoint khởi chạy REA.
- `native/`: Thành phần C++/Addon hỗ trợ tối ưu hiệu năng trên Windows (x64) và các OS khác.
- `docs/`: Hệ thống tài liệu kỹ thuật chi tiết về CLI, MCP contract, quy chuẩn phân tích.
- `tests/`: Bộ kiểm thử tự động toàn diện (Vitest, unit tests, integration tests).
- `website/`: Nền tảng tài liệu và cổng thông tin giới thiệu công cụ.

---

## 4. HƯỚNG DẪN KHÔI PHỤC MÔI TRƯỜNG KHI CÀI LẠI WIN

Nếu máy tính vừa được cài lại Windows hoặc chuyển sang làm việc trên máy mới:

1. **Cài đặt các phần mềm nền tảng:**
   - Cài đặt Git: [https://git-scm.com/](https://git-scm.com/)
   - Cài đặt Node.js LTS (khuyến nghị v22.x hoặc v24.x): [https://nodejs.org/](https://nodejs.org/)
   - (Tùy chọn cho tính năng dịch ngược chuyên sâu) Java JDK 17+ (cho Ghidra/JADX), Python 3.10+ (cho Hopper/pwntools).

2. **Clone mã nguồn từ GitHub về thư mục làm việc:**

   ```powershell
   git clone https://github.com/adwewecat/APP_PHANTICH.git d:\LAPTRINH\APP_PHANTICH
   cd d:\LAPTRINH\APP_PHANTICH
   ```

3. **Cấu hình remote upstream (để đồng bộ cập nhật từ REA khi cần):**

   ```powershell
   git remote add upstream https://github.com/morluto/rea.git
   ```

4. **Cài đặt các gói phụ thuộc (Dependencies):**

   ```powershell
   npm.cmd ci
   ```

5. **Kiểm tra trạng thái dự án:**

   ```powershell
   node scripts/rea.mjs --help
   npm.cmd run check:fast
   ```

6. **Kết nối MCP Server vào AI Agent (Gemini, Claude, Cursor...):**
   - Thêm vào file cấu hình cấu trúc JSON sau:
     ```json
     {
       "mcpServers": {
         "app_phantich": {
           "command": "node",
           "args": ["d:/LAPTRINH/APP_PHANTICH/scripts/rea.mjs", "mcp"]
         }
       }
     }
     ```

---

## 5. NHẬT KÝ THAY ĐỔI & TIẾN ĐỘ (ACTIVITY LOG & CHANGELOG)

### [2026-11-06] Khởi tạo dự án APP_PHANTICH & Tích hợp REA

- **Mục tiêu:**
  - Khởi tạo Git repository trong thư mục `d:\LAPTRINH\APP_PHANTICH`.
  - Kết nối kho từ xa `origin` trỏ về `https://github.com/adwewecat/APP_PHANTICH.git`.
  - Tải toàn bộ mã nguồn `https://github.com/morluto/rea` và tích hợp vào dự án qua merge upstream.
  - Xử lý xung đột và chuẩn hóa file `README.md`.
  - Tạo mới file `gemini.md` với đầy đủ quy tắc, kiến trúc, tài liệu khôi phục và hướng dẫn vận hành.
  - Rà soát toàn bộ các file `.md` trong kho mã nguồn.
  - Đảm bảo code sạch sẽ, không có rác hay file thừa.
  - Đẩy toàn bộ mã nguồn lên GitHub `https://github.com/adwewecat/APP_PHANTICH.git`.
- **File tác động:**
  - `README.md`: Chuẩn hóa tiêu đề dự án APP_PHANTICH, liên kết kho và `gemini.md`.
  - `gemini.md`: Tạo mới toàn bộ tài liệu hướng dẫn và quy tắc.
  - Cấu trúc thư mục: Tích hợp đầy đủ cây thư mục dự án REA v6.8.0.
- **Trạng thái:** Hoàn tất thành công, mã nguồn sẵn sàng đẩy lên GitHub.

### [2026-11-06] Cài đặt dependencies, Build REA & Phân tích CustomerOder.apk

- **Mục tiêu:**
  - Thực thi `npm.cmd ci` cài đặt đầy đủ các gói thư viện phụ thuộc của dự án.
  - Phục hồi native addon Windows (`native/windows/build/`) từ bản phát hành chính thức `rea-agents@6.8.0`.
  - Thực thi `npm.cmd run build:cached` biên dịch runtime TypeScript của REA sang `dist/`.
  - Sử dụng các công cụ phân tích của REA (APK signature inspection, artifact inspection, archive member inventory, SQLite database inspection, DEX analysis) để giải mã và phân tích file `CustomerOder.apk`.
  - Xuất báo cáo bằng chứng chi tiết về ứng dụng `CustomerOder.apk`.
- **Kết quả phân tích CustomerOder.apk:**
  - **Đơn vị sở hữu / Ký số:** Golden Gate Restaurant Group (Tập đoàn Cổng Vàng - G-People, TP. Hồ Chí Minh). Chữ ký APK Scheme v2 hợp lệ, self-consistent = true.
  - **Package Name & Phiên bản:** `vn.com.ggg.customerorder` - v1.6.91.
  - **Kiến trúc phần mềm:** Android Native (Java/Kotlin) mô hình MVP (Model-View-Presenter).
  - **Hệ thống cơ sở dữ liệu cục bộ (Offline Database):** CSDL SQLite 3 (`assets/CustomerOrder`) lưu trữ offline danh mục món (`Item`), thực đơn, sơ đồ tầng/bàn (`HallPlan`), nhóm khách (`GuestType`), món đi kèm (`Modifier`, `CoMenuItemDetail`).
  - **Giao thức truyền thông thời gian thực:** Sử dụng giao thức **MQTT** (Eclipse Paho Client) kết nối tới server `tcp://103.7.43.216:1883` để đồng bộ trạng thái món ăn, gọi nhân viên, đồng bộ bếp (KDS) và thu ngân theo thời gian thực.
  - **Tích hợp POS & Bếp:** Tích hợp đồng bộ hệ thống máy POS nhà hàng R-Keeper (`syncRK`), in phiếu bếp (`printOrder`), in hóa đơn tạm tính (`printBillTemp`).
  - **Hệ thống thanh toán tại bàn (CO-Pay / G-Pay):** Sinh mã QR thanh toán động (`createPaymentQRCode`), xuất hóa đơn điện tử VAT Thái Sơn (`submitPrintBillVAT`, `companyInfoV4ThaiSon`), quản lý Voucher ưu đãi (`redeemVoucher`), tính tiền Tip cho nhân viên (`tippingWaiterTalent`).
  - **Giám sát & Tracing:** OpenTelemetry gateway tại `https://otel-gateway.ggg.com.vn/v1/traces`.
- **File tác động:**
  - `gemini.md`: Cập nhật nhật ký tiến độ và kết quả phân tích.
  - `.gitignore`: Bổ sung `*.apk`.
- **Trạng thái:** Hoàn tất xuất sắc, code sạch sẽ, sẵn sàng đồng bộ lên GitHub.

### [2026-11-06] Phân tích chuyên sâu hệ sinh thái Stafforder.apk (SO) và KDS.apk (KDS)

- **Mục tiêu:**
  - Sử dụng REA phân tích chữ ký số, tính toàn vẹn và chứng thư của `Stafforder.apk` và `KDS.apk`.
  - Trích xuất và phân tích cấu trúc Manifest, Activity, Service, Permission của cả 2 ứng dụng.
  - Phân tích cơ chế truyền thông MQTT, cấu hình Broker, các Topic trao đổi giữa SO, CO và KDS.
  - Phân tích luồng nghiệp vụ Staff Order (SO): quản lý ca, mở bàn, gán bàn, duyệt order, điều chỉnh món, hủy món.
  - Phân tích luồng nghiệp vụ Kitchen Display System (KDS): hiển thị đơn theo trạm chế biến, điều phối món, cập nhật trạng thái làm xong / hết món.
  - Trích xuất các API endpoints, Retrofit services và cơ sở dữ liệu cục bộ.
  - Xuất báo cáo tổng hợp chi tiết bức tranh toàn cảnh hệ sinh thái 3 ứng dụng (CO - SO - KDS).
- **File tác động:**
  - `gemini.md`: Cập nhật kế hoạch và kết quả phân tích.
- **Trạng thái:** Đang tiến hành phân tích.

---

## 6. KẾ HOẠCH BÀN GIAO TIẾP THEO (NEXT STEPS / ROADMAP)

Dành cho bất kỳ AI (Gemini, Claude...) hay Developer nào mở dự án này ra tiếp tục:

1. **Bước 1: Đọc kỹ tài liệu này (`gemini.md`) và `README.md`** để hiểu toàn cảnh và nằm lòng 5 quy tắc bất di bất dịch.
2. **Bước 2: Xác nhận nhiệm vụ cụ thể từ người dùng:**
   - Người dùng muốn phân tích mục tiêu nào? (File nhị phân PE .exe/.dll Windows, file ELF Linux, file Mach-O macOS, ứng dụng Electron/Node.js/JavaScript, file APK Android, file .NET assembly, hay web application?)
   - Người dùng muốn xây dựng tính năng phân tích mới hay chạy thử nghiệm/kiểm thử hệ thống?
3. **Bước 3: Ghi chép trước khi code:**
   - Cập nhật vào mục `5. NHẬT KÝ THAY ĐỔI & TIẾN ĐỘ` trong `gemini.md`.
4. **Bước 4: Thực thi & Chú thích code:**
   - Giữ code sạch sẽ tuyệt đối, không code thừa.
   - Thêm chú thích chi tiết cho từng hàm/tính năng.
5. **Bước 5: Đẩy code lên GitHub ngay lập tức:**
   ```powershell
   git add .
   git commit -m "feat/fix: <mô tả công việc đã làm>"
   git push origin main
   ```
