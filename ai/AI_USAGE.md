# Công khai việc sử dụng AI

Nhật ký ghi nhận các lượt trao đổi về chọn đề tài và lập kế hoạch. Các ô [ĐIỀN] dành cho người sử dụng hoặc nhóm. Lịch sử chi tiết hơn nằm trong [history-8-11-2026.md](ai-history/history-8-11-2026.md).

## 1. Chọn đề tài và phạm vi

- **Thời gian** — 24–25/10/2026, theo ngữ cảnh ngày hiển thị trong cuộc trò chuyện.
- **Người sử dụng** — Đoàn Vĩnh Nhân.
- **Công cụ/mô hình** — Codex (GPT-6.1 Sol).
- **Mục đích** — So sánh các chủ đề môn học và tìm mối liên hệ để hiểu bộ giải Neko.
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
- **Mục đích** — Soạn kế hoạch LaTeX/PDF, hướng dẫn AI, nhật ký sử dụng AI và bản tổng hợp cuộc trò chuyện.
- **Prompt chính** — Lập kế hoạch xây dựng ba bộ giải GPU trên tập SPD, chốt các số liệu cần đo, cấu hình cần khảo sát, trường của mỗi lượt chạy và đánh dấu các giá trị nhóm cần điền. Đối chiếu với tệp đề môn học.
- **Kết quả** — Tạo bản kế hoạch với thiết kế PCAM, mốc thực hiện, cấu hình, phương pháp đo và lược đồ bản ghi, cùng ba tệp Markdown về sử dụng AI.
- **Phần đã sử dụng** — Bản kế hoạch và các tệp ghi nhận AI được tạo cho nhóm rà soát.
- **Chỉnh sửa của nhóm** — [ĐIỀN sau khi rà soát. Ghi mục đã sửa và lý do].
- **Kiểm chứng** — Yêu cầu PCAM, bài chung, số kích thước, số lượt đo và khai báo AI được đối chiếu với văn bản đề. Mã LaTeX biên dịch thành công và cả 5 trang PDF đã được kiểm tra bố cục. Chỉ số và lược đồ bản ghi là thiết kế cho thí nghiệm dự kiến. [ĐIỀN người duyệt và bằng chứng kiểm chứng của nhóm].
- **Commit/issue liên quan** — Initial commit.

## 4. Sửa kế hoạch và tổ chức tài liệu

- **Thời gian** — [ĐIỀN ngày rà soát nếu cần].
- **Người sử dụng** — Đoàn Vĩnh Nhân.
- **Công cụ/mô hình** — Codex (GPT-6.1 Sol).
- **Mục đích** — Chỉnh kế hoạch và sắp xếp tài liệu vào một thư mục trên Desktop.
- **Prompt chính** — Để nguồn ma trận mở, dành bốn mục PCAM của mỗi thuật toán cho nhóm tự điền, ghi công thức đo, và để nhóm tự chọn số lượng cũng như loại chuẩn.
- **Kết quả** — Cập nhật mã LaTeX và PDF. Cấu trúc bàn giao có human-doc cho kế hoạch, ai cho nhật ký và hướng dẫn, cùng README ở thư mục gốc.
- **Phần đã sử dụng** — Công thức tổng quát theo chuẩn được chọn và lược đồ lưu kết quả theo từng chuẩn đã đưa vào kế hoạch.
- **Chỉnh sửa của người dùng** — Nhóm giữ quyền chọn nguồn ma trận, viết PCAM và chốt chuẩn. Các chỗ này được đánh dấu trong PDF.
- **Kiểm chứng** — Kiểm tra biên dịch và bố cục bản PDF cập nhật. [ĐIỀN người duyệt và quyết định cuối của nhóm].
- **Commit/issue liên quan** — [ĐIỀN khi có].

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
