# Quy trình phản biện (Claude làm trên đầu ra của Agy / NotebookLM)

Mỗi lần có kết quả mới → tôi viết `review/NN-critique.md` theo bảng dưới, **trước khi** gì được đưa vào `documents/method.md`.

## Bảng chấm từng quy tắc
| # | Quy tắc (nguyên văn) | Nguồn+timestamp | Kiểm tra A: có nguồn? | B: áp dụng được theo thời gian thực? | C: đo được/không mơ hồ? | Phán quyết |
|---|----------------------|-----------------|-----------------------|--------------------------------------|-------------------------|------------|

**Phán quyết:** `Nhận` · `Thiếu nguồn` · `Mơ hồ — hỏi lại` · `Mâu thuẫn` · `Loại`.

## Các phép thử cố định
1. **Nguồn:** quy tắc không có timestamp/trích dẫn → không được vào `method.md`.
2. **Thời gian thực (chống hindsight):** quy tắc có cần biết nến *sau đó* để quyết định không? "Hộp" xác định được tại thời điểm nến đóng, hay chỉ thấy khi giá đã đi xong?
3. **Đo được:** hai người đọc cùng quy tắc có vẽ ra cùng một hộp không? Ngưỡng nào (râu/thân, bao nhiêu % hộp)?
4. **Thiên kiến chọn lọc:** video có ví dụ thua / ví dụ "không vào" không? Nếu chỉ có ví dụ thắng → ghi cảnh báo.
5. **Tính nhất quán chéo:** video A và B có nói khác nhau không → `open-questions.md`.
6. **Số liệu R:** kiểm tra phép tính R của từng ví dụ (entry, SL, TP có khớp 3R/1R như video nói không).
7. **Dấu hiệu bán hàng:** cam kết lợi nhuận, bán khoá học/tín hiệu → hạ độ tin cậy của nguồn.
8. **Đối chiếu với thực hành của Owner:** so bảng quy tắc video với mục 7b; chỗ nào Owner làm khác video, chỗ nào video nói mà Owner chưa dùng.

## Đầu ra mỗi vòng
- Bảng chấm + 3–5 câu hỏi sắc nhất cho Owner.
- Danh sách quy tắc `Nhận` → đề xuất vào `method.md`.
- Việc cho vòng sau (video nào cần xử lý lại, prompt nào cần chỉnh).
