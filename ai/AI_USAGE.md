# Công khai việc sử dụng AI

Nhật ký ghi nhận các lượt trao đổi về chọn đề tài và lập kế hoạch. Các ô [ĐIỀN] dành cho người sử dụng hoặc nhóm. Lịch sử chi tiết hơn nằm trong [history-8-11-2026.md](ai-history/history-8-11-2026.md).

## 1. Chọn đề tài và phạm vi

- **Thời gian** — 24–25/10/2026, theo ngữ cảnh ngày hiển thị trong cuộc trò chuyện.
- **Người sử dụng** — Đoàn Vĩnh Nhân.
- **Công cụ/mô hình** — Codex (GPT-6.1 Sol).
- **Mục đích** — So sánh các chủ đề môn học và tìm mối liên hệ để hiểu bộ giải Neko (Framework CFD mà Đoàn Vĩnh Nhân đang contributor).
- **Prompt chính** — Chủ đề nào liên quan nhất đến Neko, giải tích số và CFD? Nên chỉ giải \(Ax=b\) hay xét thêm một phương trình cụ thể? Có các họ thuật toán nào?
- **Kết quả** — AI đề xuất Chủ đề 1, từng đề xuất Poisson 2D và thu hẹp sớm vào Jacobi/Gauss–Seidel, sau đó liệt kê các họ thuật toán khi người dùng yêu cầu.
- **Phần đã sử dụng** — Chủ đề giải hệ tuyến tính và phân loại thuật toán làm cơ sở thảo luận.
- **Chỉnh sửa của người dùng** — Đặt trọng tâm vào tính toán song song, giữ bài toán \(Ax=b\) ở dạng đại số, giữ Neko làm ngữ cảnh để học và yêu cầu mở lại lựa chọn thuật toán. Người dùng cũng yêu cầu tách phân hoạch ma trận khỏi phân rã miền vật lý.
- **Kiểm chứng** — Phạm vi được đối chiếu với yêu cầu Chủ đề 1 trong tài liệu môn học khi soạn kế hoạch. Chưa có kiểm thử hay số liệu thực nghiệm.
- **Commit/issue liên quan** — Không.

## 2. Chọn ba thuật toán và bộ dữ liệu chung

- **Thời gian** — 08/11/2026, theo ngày hiển thị trong cuộc trò chuyện.
- **Người sử dụng** — Đoàn Vĩnh Nhân.
- **Công cụ/mô hình** — Codex (GPT-6.1 Sol).
- **Mục đích** — Xác định các bộ giải trong Neko và chọn một đại diện cho mỗi họ để so sánh trong đồ án.
- **Prompt chính** — Có những thuật toán song song nào cho \(Ax=b\), Neko đang dùng cái nào, và nên chọn thuật toán đại diện nào cho từng họ? CG yêu cầu SPD phải không? Sparse, matrix-free và preconditioner có thuộc phạm vi không?
- **Kết quả** — AI đề xuất Blocked Cholesky, Jacobi và CG trên cùng bộ ma trận SPD chéo trội nghiêm ngặt. AI đề xuất để sparse, matrix-free và tiền điều kiện ở phần mở rộng.
- **Phần đã sử dụng** — Bộ ba thuật toán và bộ dữ liệu chung đi vào kế hoạch. Các phần mở rộng được đánh dấu tùy chọn.
- **Chỉnh sửa của người dùng** — Xác nhận dùng chung bộ SPD, chốt GPU làm nền tảng song song và chốt phần mở rộng ở mức tùy chọn.
- **Kiểm chứng** — Phần mô tả Neko đã đối chiếu các tệp src/krylov/krylov_fctry.f90, src/krylov/precon_fctry.f90 và examples/tgv/tgv.case trong bản mã nguồn cục bộ. Điều kiện SPD và chéo trội được ghi thành yêu cầu cho bộ sinh. Bộ sinh, mã giải và benchmark đang ở mức kế hoạch.
- **Commit/issue liên quan** — Không.

## 3. Soạn tài liệu kế hoạch và nhật ký

- **Thời gian** — 08/11/2026, theo ngày của bản lịch sử được yêu cầu.
- **Người sử dụng** — Đoàn Vĩnh Nhân.
- **Công cụ/mô hình** — Codex (GPT-6.1 Sol).
- **Mục đích** — Soạn, chỉnh sửa và tổ chức kế hoạch LaTeX/PDF, hướng dẫn AI, nhật ký sử dụng AI và bản tổng hợp cuộc trò chuyện.
- **Prompt chính** — Lập kế hoạch cho ba bộ giải GPU trên tập SPD dựa trên đề môn học. Nêu các bước thực hiện trong phần tóm tắt, xác định cấu hình thử nghiệm, công thức đo và thông tin cần lưu cho mỗi lượt chạy. Quy định cách cập nhật nhật ký AI trước mỗi commit.
- **Kết quả** — Tạo kế hoạch và tài liệu AI, sau đó sắp xếp kế hoạch trong `human-doc/`, tài liệu AI trong `ai/` và README ở thư mục gốc. Bổ sung quy tắc gộp hoặc mở mục nhật ký theo thời gian và khối lượng công việc, đồng thời quy định cách ghi commit sắp tạo khi mã Git chưa có.
- **Phần đã sử dụng** — Bản kế hoạch có phần tóm tắt, công thức đo và lược đồ lưu sai số theo từng chuẩn. Quy tắc cập nhật nhật ký được ghi trong `AI_INSTRUCTION.md` và áp dụng khi chuẩn bị lượt commit này.
- **Chỉnh sửa của nhóm** — Để mở nguồn ma trận và đánh dấu chỗ nhóm tự điền bốn đầu mục PCAM cho từng thuật toán, số lượng chuẩn, loại chuẩn và tiêu chuẩn dừng.
- **Kiểm chứng** — Đối chiếu PCAM, bài chung, số kích thước, số lượt đo và khai báo AI với văn bản đề. Biên dịch LaTeX và kiểm tra bố cục các bản PDF. Đối chiếu liên kết tới mẫu nhật ký và kiểm tra các thay đổi Markdown trước khi commit. Công thức và lược đồ bản ghi dùng cho thí nghiệm dự kiến. [ĐIỀN người duyệt và bằng chứng kiểm chứng của nhóm].
- **Commit/issue liên quan** — `2e37f0f` (Initial commit), `209afb7` (add abstract), `9acd038` (change doc), `0f316a9` (change doc), `5c1730a` (change instruction), `lastest commit - change instruction`.

## Mẫu cho phiên tiếp theo

- **Thời gian** — [ĐIỀN].
- **Người sử dụng** — [ĐIỀN].
- **Công cụ/mô hình** — [ĐIỀN].
- **Mục đích** — [ĐIỀN].
- **Prompt chính hoặc bản tóm tắt** — [ĐIỀN].
- **Kết quả** — [ĐIỀN].
- **Phần đã sử dụng** — [ĐIỀN].
- **Chỉnh sửa của nhóm** — [ĐIỀN].
- **Kiểm chứng** — [ĐIỀN lệnh chạy, test, log, số liệu hoặc nguồn đã kiểm tra].
- **Commit/issue liên quan** — [ĐIỀN].

## Tuyên bố

Nhóm chịu trách nhiệm về tính đúng đắn, bản quyền, số liệu thực nghiệm và mọi nội dung đã nộp.
