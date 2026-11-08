# Hướng dẫn AI hỗ trợ đồ án

## Phạm vi đã chốt

- Đây là đồ án môn Lập trình tính toán song song về giải hệ \(Ax=b\). Xây dựng Blocked Cholesky, Jacobi và Conjugate Gradient (CG), mỗi thuật toán có bản CPU tuần tự và bản GPU song song.
- Bộ benchmark chính dùng chung ma trận thực, đặc, lưu tường minh, đối xứng xác định dương (SPD). Nguồn dữ liệu có thể là bộ ma trận bên ngoài hoặc bộ tự sinh. Nhóm sẽ chốt nguồn và kiểm tra điều kiện hội tụ của Jacobi. Dùng cùng dữ liệu, kiểu số và phép kiểm nghiệm cuối cho mọi bộ giải.
- Sparse, matrix-free và preconditioner là các nhánh tùy chọn. Chỉ lập kế hoạch chi tiết hoặc triển khai khi nhóm yêu cầu. Neko là ngữ cảnh để hiểu cách dùng CG và reduction trong thực tế. Phạm vi đồ án là hệ tuyến tính đại số.
- Dùng [bản kế hoạch](../human-doc/ke-hoach.tex) làm điểm đối chiếu. Nhóm tự điền bốn mục PCAM cho từng thuật toán, chọn số lượng và danh sách chuẩn, rồi xác định tiêu chuẩn dừng. Giữ các quyết định này dưới dạng placeholder cho đến khi nhóm xác nhận.

## Công việc AI được hỗ trợ

- Giải thích khái niệm và mã, phân tích PCAM, gợi ý phép kiểm thử, chẩn đoán lỗi, đề xuất tối ưu và phản biện benchmark. Chia đề xuất thành các phần đủ nhỏ để người phụ trách đọc, kiểm chứng và giải thích.
- Khi đề xuất mã, nêu đầu vào, đầu ra, giả định, phụ thuộc giữa kernel, điểm đồng bộ và phép kiểm tra có thể tái lập. Phân biệt mã mới viết, đoạn dựa trên nguồn ngoài và mã đã có của nhóm. Ghi nguồn, phiên bản và giấy phép khi dùng mã hoặc tài liệu ngoài.
- Phân biệt rõ đề xuất, dữ liệu minh họa và kết quả đã đo. Chỉ báo cáo số liệu thật từ bản ghi do chương trình sinh. Nêu trạng thái kiểm chứng của các lệnh chạy, kiểm thử và profiling. Khi chưa có bằng chứng, ghi rõ là chưa kiểm chứng.
- Dữ liệu cá nhân, khóa truy cập, mã riêng tư và đề chưa công bố phải được giữ ngoài dịch vụ AI công cộng. Khi cần trao đổi, dùng đoạn đã lược bỏ thông tin hoặc ví dụ tối thiểu được nhóm cho phép chia sẻ.
- Nhóm tự viết hoặc rà soát mã, kiểm thử, chạy thí nghiệm và chịu trách nhiệm về nội dung nộp. Mỗi thành viên phải giải thích được các thay đổi mình đưa vào. Cấm tạo giả dữ liệu đo, biểu đồ, nhật ký, commit, kết quả kiểm thử hoặc trích dẫn.

## Điểm cần kiểm chứng khi rà soát

- **Cholesky.** Kiểm tra phụ thuộc giữa phân tích tile đường chéo, giải tam giác và cập nhật tile còn lại. Kiểm tra tile dư, nghiệm cuối và việc khôi phục \(A\) nếu thuật toán ghi đè đầu vào.
- **Jacobi.** Kiểm tra việc đọc nghiệm cũ, ghi nghiệm mới, đổi vùng nhớ và thứ tự kiểm tra phần dư. Đo ảnh hưởng của tần suất kiểm tra dừng và cách quản lý hai vector bằng các đối chứng riêng.
- **CG.** Xác nhận SPD, phép nhân ma trận–vector, reduction và thứ tự cập nhật hệ số. Tính lại phần dư cuối từ dữ liệu gốc.
- **GPU.** Rà soát race condition, deadlock, truy cập ngoài biên, thứ tự stream, lỗi số học và rò rỉ tài nguyên. Ghi công cụ kiểm tra, lệnh chạy và kết quả khi có.
- **Benchmark.** Giữ tối thiểu 3 kích thước và 5 lượt đo mỗi cấu hình. Dùng cùng dữ liệu, kiểu số, ngưỡng chấp nhận và phạm vi thời gian khi tính speedup. Giữ kết quả lỗi, trạng thái không hội tụ và số lượt hợp lệ. Tách lượt profiling nếu công cụ làm thay đổi thời gian.

## Nhật ký sử dụng

Trước mỗi lượt commit, cập nhật [AI_USAGE.md](AI_USAGE.md#mẫu-cho-phiên-tiếp-theo) theo mẫu có sẵn trong tệp và đưa phần cập nhật vào cùng commit. Ghi thời gian, người sử dụng, công cụ hoặc mô hình, mục đích, prompt chính, đầu ra, phần được dùng, chỉnh sửa, bằng chứng kiểm chứng và commit hoặc issue liên quan.

Trước khi chạy `git commit`, kiểm tra dòng cuối của mục nhật ký đang cập nhật (**Commit/issue liên quan**) có mục `lastest commit - <commit msg>` ở cuối dòng. Điền đúng thông điệp của commit sắp tạo. Khi chuẩn bị lượt commit kế tiếp, đối chiếu lịch sử Git và thay dấu tạm của commit trước bằng mã Git kèm thông điệp, rồi ghi dấu tạm cho commit sắp tạo.

Gộp vào mục cuối nếu công việc nhỏ, diễn ra gần nhau và tiếp nối cùng nội dung. Mở mục mới nếu đã qua một khoảng thời gian đáng kể hoặc khối lượng công việc đủ lớn để ghi riêng. Khi gộp, giữ các mốc thời gian và thông tin kiểm chứng cần thiết.

Giữ bản tóm tắt theo ngày trong [ai-history](ai-history/). Cập nhật trạng thái khi nhóm đã duyệt, kiểm thử hoặc quyết định bỏ một đề xuất.
