
# OUTLINE BÁO CÁO MÔN TÍNH TOÁN SONG SONG
**Đề tài:** Giải hệ phương trình tuyến tính song song trên GPU
**Các thuật toán:** Blocked Cholesky, Jacobi và Conjugate Gradient (CG).

# Outline
| Phần | Nội dung chính | Lấy từ bước checklist | Kết quả cần đạt |
|---|---|---|---|
| **1. Giới thiệu** | Giới thiệu bài toán tích vô hướng, giải hệ $Ax=b$, mục tiêu và phạm vi nghiên cứu. | 1, 4, 5 | Phát biểu bài toán, xác định mục tiêu và phạm vi nghiên cứu. |
| **2. Cơ sở lý thuyết và thiết kế** | Lý thuyết Cholesky, Jacobi, CG; thiết kế PCAM cho bài A1 và ba thuật toán. | 4, 6, 7 | Cơ sở toán học, giả thuật toán, sơ đồ PCAM và phương án song song hóa. |
| **3. Cài đặt chương trình tuần tự trên CPU** | Cài đặt tích vô hướng và ba thuật toán giải hệ trên CPU; tổ chức dữ liệu và kiểm tra tính đúng đắn. | 3, 4, 6, 9 | Chương trình CPU tuần tự, sơ đồ xử lý và kết quả kiểm thử tính đúng đắn. |
| **4. Cài đặt chương trình song song trên GPU** | Cài đặt các thuật toán trên GPU; phân chia công việc, quản lý bộ nhớ, reduction và đồng bộ. | 4, 7, 8, 9 | Chương trình GPU song song, sơ đồ phân chia công việc, tổ chức bộ nhớ và kiểm thử CPU/GPU. |
| **5. Thiết kế thực nghiệm** | Môi trường, bộ dữ liệu, cấu hình thử nghiệm, phương pháp đo thời gian và đánh giá hiệu năng. | 2, 5, 10, 11 | Bảng môi trường, bộ dữ liệu, cấu hình thử nghiệm, tiêu chuẩn đánh giá và quy trình đo. |
| **6. Kết quả và phân tích** | So sánh CPU/GPU, thời gian, speedup, efficiency, sai số, hội tụ, đồng bộ và bộ nhớ. | 9, 11, 12, 13, 14 | Bảng kết quả thực nghiệm, biểu đồ thời gian, speedup, efficiency, sai số, hội tụ và nhận xét. |
| **7. Kết luận** | Tổng hợp kết quả, hạn chế và hướng phát triển. | 13, 15 | Tổng kết kết quả đạt được, đánh giá ưu nhược điểm và đề xuất hướng phát triển. |
| **Phụ lục** | Mã nguồn, hướng dẫn chạy, tham số và kết quả bổ sung. | 16 | Mã nguồn hoặc đường dẫn GitHub, hướng dẫn chạy, bảng tham số và dữ liệu bổ sung. |

> **Ghi chú:** Cột "Lấy từ bước checklist" tham chiếu 16 công việc trong file `human-doc/checklist.md`. Đây là khung nội dung báo cáo dự kiến và có thể điều chỉnh trong quá trình thực hiện.