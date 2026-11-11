# Hướng dẫn làm việc trong parallel-linear-system

Đây là đồ án môn Tính toán song song về giải hệ \(Ax=b\). Nhóm thực hiện bài tích vô hướng chung và ba bộ giải Blocked Cholesky, Jacobi, Conjugate Gradient (CG). Mỗi bộ giải có bản CPU tuần tự và bản GPU song song. Bộ benchmark chính dùng chung ma trận đặc, đối xứng xác định dương (SPD).

## Tài liệu cần đọc

- Đọc [ai/AI_INSTRUCTION.md](ai/AI_INSTRUCTION.md) trước khi sửa mã hoặc tài liệu. Tệp này quy định phạm vi hỗ trợ của AI, cách kiểm chứng và cách ghi nhật ký trước mỗi commit.
- Đọc [human-doc/ke-hoach.tex](human-doc/ke-hoach.tex) để xác định phạm vi kỹ thuật, kế hoạch kiểm thử và các chỉ số cần đo. Dùng [human-doc/checklist.md](human-doc/checklist.md) và [human-doc/outline_table.md](human-doc/outline_table.md) để xác định công việc và cấu trúc báo cáo.
- Đọc [ai/AI_USAGE.md](ai/AI_USAGE.md) để xem các quyết định đã ghi và mẫu cập nhật nhật ký.

## Phạm vi thực hiện

- Thực hiện hạng mục theo yêu cầu hiện tại của người dùng. Giữ các mục chờ nhóm quyết định, như thiết kế PCAM, nguồn ma trận, chuẩn sai số, tiêu chuẩn dừng và cấu hình GPU, ở trạng thái chờ cho đến khi có lựa chọn.
- Với benchmark chính, đối chiếu CPU/GPU trên cùng đầu vào, độ chính xác và phạm vi đo. Kiểm tra điều kiện hội tụ của Jacobi và nghiệm cuối của cả ba bộ giải. Chạy tối thiểu ba kích thước và năm lượt đo mỗi cấu hình khi thực hiện benchmark chính.
- Sparse, matrix-free và tiền điều kiện là phần mở rộng khi nhóm yêu cầu. Chỉ báo cáo số liệu thực nghiệm có bản ghi kiểm chứng.
- Khi sửa nội dung kế hoạch, cập nhật nguồn LaTeX và kiểm tra bản PDF tạo từ nguồn đó.

## Nhật ký và commit

- Trước mỗi commit, cập nhật [ai/AI_USAGE.md](ai/AI_USAGE.md) theo mẫu và đưa nhật ký vào cùng commit. Gộp công việc nhỏ, gần nhau và cùng nội dung vào mục cuối. Mở mục mới khi công việc cách nhau đáng kể hoặc khối lượng đủ lớn.
- Đối chiếu lịch sử Git và thay dấu tạm của commit trước bằng mã Git kèm thông điệp. Ghi `lastest commit - <commit msg>` ở cuối dòng **Commit/issue liên quan** của mục hiện tại, với đúng thông điệp của commit sắp tạo.
