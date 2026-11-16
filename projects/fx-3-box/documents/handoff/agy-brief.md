# Brief giao việc cho Agy (tự đứng độc lập — copy toàn bộ khối dưới đây)

```
NHIỆM VỤ: Trích xuất và tổng hợp phương pháp trade FX "3 hộp" (box) từ video YouTube. Chỉ trích xuất, KHÔNG đánh giá phương pháp hay hay dở.

NGUỒN KHỞI ĐẦU
- Video: https://www.youtube.com/watch?v=fpukx0NRbhw
- Kênh: https://youtube.com/@tiensanhforex
- Tìm thêm tối đa 5 video khác của kênh nói về cùng phương pháp (cùng "hộp"/box). Liệt kê lý do chọn mỗi video.

QUY TẮC BẮT BUỘC
1. Chỉ ghi điều video thực sự nói/chiếu. Điều gì không nói → ghi "KHÔNG NÓI". Không suy diễn, không bổ sung kiến thức trade chung.
2. Mỗi quy tắc kèm timestamp mm:ss. Phân biệt rõ: [TRÍCH NGUYÊN VĂN] vs [DIỄN GIẢI].
3. Nếu không lấy được transcript/phụ đề cho một video, nói rõ, đừng bịa. Ghi video đó "chưa xử lý".
4. Ghi MỌI ví dụ lệnh trong video (ngày, cặp, khung TF, hướng, entry/SL/TP, kết quả). Ghi riêng ví dụ THUA hoặc ví dụ "không vào lệnh" nếu có. Nếu video không có ví dụ thua, ghi "KHÔNG CÓ VÍ DỤ THUA".
5. Ghi nếu video bán khoá học/nhóm/tín hiệu, hoặc dùng từ cam kết ("chắc chắn thắng", "không bao giờ thua").
6. VIDEO HỘI VIÊN (biểu tượng khoá / nhãn "Members only" / "Hội viên"): BỎ QUA. Chủ tài khoản không phải hội viên. Không cố vượt rào, không tìm bản re-up/leak ở nơi khác. Chỉ ghi vào INDEX.md: tên, ngày đăng, trạng thái "hội viên — không xử lý".
7. KHÔNG duyệt cả kênh. Chỉ chọn video có tên/mô tả liên quan đến hộp/box; mỗi video chọn kèm lý do. Tổng tối đa 6 video (gồm video gốc).

CẦN TRẢ LỜI CHO TỪNG VIDEO
a) "Hộp" là gì: cách xác định, vẽ từ đâu tới đâu, đỉnh/đáy hộp tính theo râu hay thân, "3 hộp" nghĩa là gì.
b) Điều kiện vào SELL và BUY (xu hướng, vị trí trong hộp, nến xác nhận, vùng kết nối giữa các hộp nếu có).
c) SL đặt ở đâu; TP đặt ở đâu; mục tiêu bao nhiêu R; có dời SL/chốt từng phần không.
d) Quản lý vốn (% rủi ro, khối lượng, số lệnh).
e) Cặp tiền, khung giờ/phiên, khung TF khuyến nghị.
f) Chỉ báo nào video dùng (nếu có). Nếu không dùng MA/RSI/Volume thì ghi rõ.
g) Khi nào KHÔNG vào lệnh.

ĐỊNH DẠNG ĐẦU RA
- Mỗi video → 1 file markdown theo mẫu `projects/fx-3-box/sources/_template.md`, đặt tên `projects/fx-3-box/sources/NN-ten-ngan.md`.
- Cập nhật bảng `projects/fx-3-box/sources/INDEX.md` (trạng thái: đã xử lý / chưa xử lý + lý do).
- Cuối cùng, 1 file `projects/fx-3-box/sources/SYNTHESIS-agy.md`: bảng gộp các video (chủ đề | video nào nói gì | mâu thuẫn), kèm mục "CÁC CHỖ MƠ HỒ / CẦN HỎI CHỦ KÊNH". Đánh dấu đầu file: "Bản tổng hợp của Agy — CHƯA kiểm chứng".

TRONG SYNTHESIS-agy.md, thêm mục "GIỚI HẠN NGUỒN": số video hội viên bị bỏ qua (kèm tên), và các chủ đề mà video công khai chỉ nhắc đến mà không giải thích đầy đủ (có dấu hiệu phần chi tiết nằm ở video hội viên).

KHÔNG LÀM: không đưa lời khuyên đầu tư, không viết thêm quy tắc không có trong video, không sửa các file khác trong repo.
```

## Ghi chú cho Owner
- **Đừng đưa quy trình sell/buy của bạn (mục 7b) cho Agy ở vòng này.** Nếu Agy biết trước bạn làm gì, nó dễ "chọn lọc" cho khớp. Ta so sánh sau, để thấy video thật sự nói gì và bạn đang làm khác chỗ nào.
- Nếu Agy không push được vào repo, bạn copy file nó tạo vào `projects/fx-3-box/sources/` rồi báo tôi.
