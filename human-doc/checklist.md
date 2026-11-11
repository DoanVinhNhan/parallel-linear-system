
# CHECKLIST CÔNG VIỆC - PARALLEL COMPUTING

**Đề tài:** Giải hệ phương trình tuyến tính song song trên GPU

**Các thuật toán:** Blocked Cholesky, Jacobi và Conjugate Gradient (CG).

## Danh sách công việc

| STT | Công việc | Kết quả cần đạt |
|---|---|---|
| 1 | Chốt phương án thực hiện | Xác định 3 thuật toán Cholesky, Jacobi, CG và công nghệ GPU |
| 2 | Kiểm tra môi trường | Xác định CPU, GPU, RAM, hệ điều hành, compiler và thư viện |
| 3 | Thiết lập dự án | Tạo cấu trúc source, data, test, results |
| 4 | Thực hiện bài A1 - Tích vô hướng | PCAM, chương trình tuần tự và song song, kiểm thử |
| 5 | Chuẩn bị dữ liệu | Ma trận SPD, vector b, nghiệm tham chiếu, bộ test |
| 6 | Xây dựng thuật toán tuần tự | Cholesky, Jacobi, CG trên CPU |
| 7 | Thiết kế PCAM | Partitioning, Communication, Agglomeration, Mapping cho từng thuật toán |
| 8 | Xây dựng thuật toán song song | Cholesky, Jacobi, CG trên GPU |
| 9 | Kiểm thử chương trình | Đối chiếu nghiệm CPU/GPU, sai số và hội tụ |
| 10 | Thiết lập đo hiệu năng | Đo thời gian tổng, pha giải, truyền dữ liệu, đồng bộ |
| 11 | Chạy thực nghiệm | Ít nhất 3 kích thước, 5 lượt/cấu hình, khảo sát cấu hình song song |
| 12 | Tổng hợp kết quả | Median, min-max hoặc IQR, speedup, efficiency phù hợp |
| 13 | Phân tích và so sánh | Hiệu năng, sai số, hội tụ, reduction, đồng bộ, bộ nhớ |
| 14 | Lập bảng và vẽ biểu đồ | Thời gian, speedup, efficiency, sai số, vòng lặp |
| 15 | Viết báo cáo | Lý thuyết, PCAM, cài đặt, thực nghiệm, kết luận |
| 16 | Hoàn thiện sản phẩm | Kiểm tra mã nguồn, tài liệu, hướng dẫn chạy và file nộp |


