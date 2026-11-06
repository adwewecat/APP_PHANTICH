# SỔ TAY DỰ ÁN & HƯỚNG DẪN DÀNH CHO GEMINI / A.I / DEVELOPER

> **DỰ ÁN:** PHÂN GIẢI NGƯỢC (REVERSE ENGINEER ANYTHING - REA)  
> **KHO LƯU TRỮ CHÍNH (BACKUP REPO):** [https://github.com/adwewecat/REA_BACKUP.git](https://github.com/adwewecat/REA_BACKUP.git)  
> **KHO NGUỒN UPSTREAM:** [https://github.com/morluto/rea](https://github.com/morluto/rea)  
> **NGÀY KHỞI TẠO TÍCH HỢP:** 2026-11-06  
> **FILE CHỈ DẪN QUAN TRỌNG:** `gemini.md` (Tài liệu này) & `README.md`

---

## 1. MỤC ĐÍCH CỦA FILE `gemini.md`

Tài liệu này được tạo ra để đảm bảo:
1. **Tính liên tục tuyệt đối:** Khi người dùng cài lại Windows, đổi máy hoặc môi trường bị xóa trắng, bất kỳ AI nào (Gemini, Claude, GPT, v.v.) hay Lập trình viên (Developer) khác khi mở thư mục dự án này ra đọc đều có thể:
   - Hiểu được toàn bộ bản chất dự án, kiến trúc hệ thống và luồng hoạt động.
   - Nắm rõ các quy tắc làm việc bắt buộc.
   - Biết chính xác trạng thái hiện tại của dự án và **phải làm gì tiếp theo** mà không cần hỏi lại từ đầu.
2. **Nhật ký bắt buộc (Pre-Action Logging):** Trước khi làm, sửa đổi hoặc thêm bất kỳ tính năng gì, bắt buộc phải ghi chú mục đích, kế hoạch và các file sẽ thay đổi vào tài liệu này trước.

---

## 2. QUY TẮC BẤT DI BẤT DỊCH CỦA DỰ ÁN (PROJECT RULES)

Tất cả các AI và Developer tham gia vào dự án này bắt buộc phải tuân thủ nghiêm ngặt 5 quy tắc sau:

### Quy tắc 1: ĐẨY CODE LÊN GITHUB NGAY LẬP TỨC
- **Bất kỳ lúc nào thêm tính năng hoặc chỉnh sửa code**, sau khi kiểm tra xong phải lập tức tạo commit rõ ràng và `git push` về kho GitHub chính:
  ```bash
  git push origin main
  ```
- URL Repo: `https://github.com/adwewecat/REA_BACKUP.git`
- Tuyệt đối không để dồn commit nhiều ngày hoặc sửa nhiều việc mà không đẩy lên GitHub.

### Quy tắc 2: GHI CHÉP VÀ LƯU VẾT TRƯỚC KHI THỰC HIỆN
- Trước khi bắt tay vào code hoặc fix bug:
  - Phải ghi nhận mục tiêu vào mục `5. NHẬT KÝ THAY ĐỔI & TIẾN ĐỘ` trong `gemini.md`.
  - Phải ghi nhận nguyên nhân (nếu là bug) và giải pháp dự kiến.
- Sau khi hoàn thành:
  - Cập nhật kết quả thực tế, trạng thái đã kiểm tra (test passed).

### Quy tắc 3: CODE SẠCH HOÀN TOÀN (CLEAN CODE)
- Không để lại code dư thừa, code chết (dead code), code thử nghiệm không sử dụng.
- Dọn dẹp các file rác, file tạm, thư mục tạm (scratch/temp) trước khi commit.
- Giữ cấu trúc thư mục gọn gàng, đúng quy chuẩn kiến trúc của dự án.

### Quy tắc 4: CHÚ THÍCH CODE ĐẦY ĐỦ (IN-CODE DOCUMENTATION)
- Tất cả các hàm, class, module và tính năng mới hoặc được sửa đổi đều phải có comment/docstring giải thích:
  - Chức năng của đoạn code là gì.
  - Tham số đầu vào, giá trị trả về và các trường hợp lỗi (Edge Cases).
  - Giúp AI khác hoặc Dev khác đọc code nắm bắt ngay tức thì.

### Quy tắc 5: ĐẶC THÙ MÔI TRƯỜNG WINDOWS / POWERSHELL
- Trên Windows PowerShell, do chính sách `ExecutionPolicy`, lệnh `npm` hoặc `npx` có thể bị chặn bởi script PowerShell (`npm.ps1`).
- Luôn sử dụng lệnh **`npm.cmd`** và **`npx.cmd`** khi chạy trong terminal PowerShell:
  ```powershell
  npm.cmd run <script>
  npm.cmd ci
  npm.cmd test
  ```

---

## 3. TỔNG QUAN VÀ KIẾN TRÚC DỰ ÁN REA

### 3.1. Bản chất của REA
**REA (Reverse Engineer Anything)** là công cụ hỗ trợ phân giải ngược (Reverse Engineering) toàn diện, hoạt động cục bộ (local-only) thông qua:
1. **Giao diện dòng lệnh (CLI):** `rea <lệnh>` hoặc `node scripts/rea.mjs <lệnh>`.
2. **Model Context Protocol (MCP) Server:** Cho phép các AI Agent (Gemini, Claude Code, Codex, Cursor, Grok Build...) trực tiếp ra lệnh phân tích nhị phân, ứng dụng web, Electron, Android, v.v., và nhận về bằng chứng xác thực (evidence).

### 3.2. Cấu trúc thư mục chính
- `src/`: Toàn bộ mã nguồn cốt lõi bằng TypeScript (Node.js ES Modules):
  - `src/cli/`: Xử lý giao diện dòng lệnh.
  - `src/mcp/`: Server MCP, định nghĩa tool catalog và xử lý request từ AI Agent.
  - `src/analysis/` & `src/engines/`: Các thuật toán phân tích nhị phân, decompiler, deobfuscation.
  - `src/providers/`: Bộ tích hợp với các công cụ dịch ngược (Ghidra, Hopper, IDA, Cutter, JADX...).
  - `src/process/`: Quản lý tiến trình con độc lập, an toàn.
- `bridge/`: Các script cầu nối giao tiếp với các engine bên ngoài:
  - `bridge/ghidra/`: Java extension/bridge cho Ghidra.
  - `bridge/hopper_bridge.py`: Python bridge cho Hopper Disassembler.
  - `bridge/android/ReaJadxBridge.java`: Bridge phân tích APK qua JADX.
  - `bridge/pwndbg/`, `bridge/pwntools/`: Tích hợp phân tích lỗi crash và exploit.
- `scripts/`: Entrypoint thực thi:
  - `scripts/rea.mjs`: File entrypoint chính để khởi chạy REA.
- `native/`: Thành phần native C++/Addon hỗ trợ Windows (x64) và các nền tảng khác.
- `docs/`: Toàn bộ tài liệu chi tiết về API, CLI, kiến trúc và cách thức tích hợp.
- `tests/`: Bộ kiểm thử tự động phong phú (Vitest, unit test, conformance test).

---

## 4. HƯỚNG DẪN KHÔI PHỤC MÔI TRƯỜNG KHI CÀI LẠI WIN

Nếu máy tính vừa được cài lại Windows hoặc chuyển sang máy mới:

1. **Cài đặt công cụ nền tảng:**
   - Cài đặt Git: [https://git-scm.com/](https://git-scm.com/)
   - Cài đặt Node.js LTS (khuyến nghị v22.x hoặc v24.x): [https://nodejs.org/](https://nodejs.org/)
   - (Tùy chọn cho phân tích chuyên sâu) Java JDK 17+ (nếu dùng Ghidra), Python 3.10+ (nếu dùng Hopper/pwntools).

2. **Clone mã nguồn từ GitHub:**
   ```powershell
   git clone https://github.com/adwewecat/REA_BACKUP.git d:\LAPTRINH\phan_giai_nguoc
   cd d:\LAPTRINH\phan_giai_nguoc
   ```

3. **Cài đặt gói phụ thuộc (Dependencies):**
   ```powershell
   npm.cmd ci
   ```

4. **Kiểm tra trạng thái dự án:**
   ```powershell
   node scripts/rea.mjs --help
   npm.cmd run check:fast
   ```

5. **Kết nối MCP Server vào AI Agent:**
   - Cấu hình file cấu hình MCP của Agent (Gemini, Claude, Cursor...) trỏ đến:
     ```json
     {
       "mcpServers": {
         "rea": {
           "command": "node",
           "args": ["d:/LAPTRINH/phan_giai_nguoc/scripts/rea.mjs", "mcp"]
         }
       }
     }
     ```

---

## 5. NHẬT KÝ THAY ĐỔI & TIẾN ĐỘ (ACTIVITY LOG & CHANGELOG)

### [2026-11-06] Khởi tạo dự án & Tích hợp REA
- **Mục tiêu:**
  - Khởi tạo không gian làm việc `d:\LAPTRINH\phan_giai_nguoc`.
  - Tải mã nguồn `https://github.com/morluto/rea` về và tích hợp toàn bộ vào dự án.
  - Thiết lập Git Remote `origin` trỏ về `https://github.com/adwewecat/REA_BACKUP.git` và `upstream` trỏ về `https://github.com/morluto/rea.git`.
  - Kiểm tra và thiết lập file `README.md` cùng `gemini.md`.
  - Thiết lập danh sách quy tắc bất di bất dịch cho toàn bộ quá trình phát triển.
  - Đọc và rà soát toàn bộ hệ thống file Markdown `.md` trong dự án.
- **File tác động:**
  - `README.md`: Thêm thông tin định danh dự án, liên kết repo backup và tài liệu `gemini.md`.
  - `gemini.md`: Tạo mới với đầy đủ hướng dẫn, quy tắc, nhật ký và kế hoạch bàn giao.
  - Cấu trúc thư mục: Tích hợp trọn vẹn toàn bộ cây thư mục REA (v6.8.0).
- **Trạng thái:**
  - Đã tích hợp hoàn tất.
  - Git remote `origin` trỏ về `https://github.com/adwewecat/REA_BACKUP.git`.
  - Code sạch sẽ, không có file thừa. Sẵn sàng push lên GitHub.

---

## 6. KẾ HOẠCH BÀN GIAO TIẾP THEO (NEXT STEPS / ROADMAP)

Đối với bất kỳ AI (Gemini, Claude...) hay Developer nào nhận dự án sau thời điểm này:

1. **Bước 1: Đọc kỹ tài liệu này (`gemini.md`) và `README.md`** để nắm bắt toàn bộ ngữ cảnh.
2. **Bước 2: Xác nhận yêu cầu của người dùng:**
   - Người dùng muốn phân tích phần mềm gì? (Binary x86/x64, PE Windows, ELF Linux, Mach-O macOS, Web app, JavaScript, hay APK Android?)
   - Người dùng muốn thêm tính năng gì mới vào REA hay muốn chạy kiểm thử tính năng hiện có?
3. **Bước 3: Trước khi code:**
   - Ghi chú kế hoạch vào mục `5. NHẬT KÝ THAY ĐỔI & TIẾN ĐỘ`.
4. **Bước 4: Viết code & Chú thích:**
   - Tuân thủ clean code, ghi chú rõ ràng các function/module bằng tiếng Việt/tiếng Anh dễ hiểu.
5. **Bước 5: Đẩy code lên GitHub ngay lập tức:**
   ```powershell
   git add .
   git commit -m "feat/fix: <mô tả ngắn gọn>"
   git push origin main
   ```
