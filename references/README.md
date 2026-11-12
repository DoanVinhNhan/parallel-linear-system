# Tài liệu tham khảo cho các bộ giải tuyến tính

Các khóa trích dẫn bên dưới tương ứng với [refs.bib](refs.bib). Các phần được chỉ định tập trung vào ba bộ giải trong đồ án và cách triển khai trên CPU hoặc GPU.

## Blocked Cholesky

- **Haidar và cộng sự (2017)** · `haidar2017cholesky`. Nghiên cứu phân tích Cholesky ma trận đặc chạy hoàn toàn trên GPU. Mục 3.2 và Algorithm 1 trình bày cách chia khối và phối hợp `POTRF`, `TRSM`, `SYRK`, `GEMM`. Mục 4 phân tích các lựa chọn tối ưu trên GPU. [PDF](https://icl.utk.edu/projectsfiles/magma/pubs/63-main.pdf) · [DOI](https://doi.org/10.1145/3038228.3038237)
- **Buttari và cộng sự (2009)** · `buttari2009tiled`. Mục 3.1 mô tả phân tích Cholesky theo tile và mục 4 mô tả cách lập lịch theo đồ thị phụ thuộc. Dùng để xác định tác vụ có thể chạy đồng thời khi thiết kế PCAM. Các phép đo trong bài chạy trên CPU đa lõi. [PDF](https://icl.utk.edu/files/publications/2010/icl-utk-440-2010.pdf) · [DOI](https://doi.org/10.1016/j.parco.2008.10.002)

## Jacobi

- **Barrett và cộng sự (1994), *Templates for the Solution of Linear Systems*** · `barrett1994templates`. Mục 2.2.1 trình bày công thức lặp Jacobi, tính độc lập của cập nhật theo hàng và lý do cần giữ nghiệm vòng trước. Mục 4.2 phân biệt phần dư, sai số và tiêu chuẩn dừng. Mục 2.3.1 cũng trình bày CG. [PDF Netlib](https://www.netlib.org/templates/templates.pdf) · [DOI của sách](https://doi.org/10.1137/1.9781611971538)
- **Zhang, Miao và Wang (2009)** · `zhang2009cudajacobi`. Phần tóm tắt mô tả bộ giải lặp Jacobi song song bằng CUDA cho hệ tuyến tính đặc. Thông tin trích dẫn đã đối chiếu với bản ghi Crossref. Tại lần tra cứu này, chưa lấy được toàn văn công khai. [IEEE Xplore](https://ieeexplore.ieee.org/document/5385084/) · [DOI](https://doi.org/10.1109/IFCSTA.2009.68)
- **NVIDIA, `jacobiCudaGraphs`** · `nvidia2026jacobigraphs`. Mã mẫu cho Jacobi trên CUDA. Trong `jacobi.cu`, xem cách giữ hai vector nghiệm, reduction cho độ thay đổi giữa hai vòng lặp và cách tổ chức các lần gọi kernel bằng CUDA Graphs. Liên kết trỏ đến phiên bản mã đã kiểm tra. [Mã nguồn NVIDIA](https://github.com/NVIDIA/cuda-samples/tree/0ec046d5e99d7214cc8e9fbac2cc1e66f3019878/cpp/3_CUDA_Features/jacobiCudaGraphs)

## Conjugate Gradient

- **Shewchuk (1994)** · `shewchuk1994cg`. Mục 8–9 giải thích hướng liên hợp và hội tụ của CG, mục 11.2 thảo luận tiêu chuẩn dừng, và phụ lục B.2 cung cấp giả mã CG. [PDF Carnegie Mellon](https://www.cs.cmu.edu/~quake-papers/painless-conjugate-gradient.pdf)
- **Hestenes và Stiefel (1952)** · `hestenes1952cg`. Bài báo gốc giới thiệu CG cho hệ tuyến tính và phát triển cơ sở toán học của phương pháp. Dùng khi trích nguồn gốc thuật toán. [PDF NIST](https://nvlpubs.nist.gov/nistpubs/jres/049/jresv49n6p409_a1b.pdf) · [DOI](https://doi.org/10.6028/jres.049.044)
- **Trotter và cộng sự (2025)** · `trotter2025gpucg`. Mục 3.1 mô tả CG trên một GPU, gồm tích vô hướng, cập nhật vector, vị trí lưu hệ số vô hướng và điểm đồng bộ CPU–GPU. Các phép đo trong bài dùng ma trận thưa. Mục 3.1 có thể tham khảo khi thiết kế reduction và kiểm tra dừng cho đồ án. [PDF của nhóm tác giả](https://beyondmoore.com/_file/assets/preprint-pdfs/SC25_Inno4Scale_aCG.6fc2df87.pdf) · [Toàn văn ACM](https://doi.org/10.1145/3712285.3759774)
