# fx-3-box — Phương pháp trade FX "3 cái hộp"

Dự án **nghiên cứu & tổng hợp** (không phải code): gom kiến thức từ nhiều video YouTube về phương pháp trade FX "3 hộp", chắt lọc thành một bộ quy tắc rõ ràng, rồi kiểm chứng bằng nhật ký lệnh thật/demo.

- **Mục tiêu:** một tài liệu phương pháp (`documents/method.md`) đủ rõ để người khác áp dụng được — cách xác định 3 hộp, điều kiện vào lệnh, đặt SL/TP, quản lý R.
- **Hiện trạng:** Owner đã thử tay → 2 lệnh có lãi (1 sell **+3R**, 1 buy **+1R** tại hộp xanh cuối). Mẫu còn rất nhỏ (n=2) — chưa đủ để kết luận gì về edge.
- **Cách làm:** mỗi video → 1 file ghi chú trong `sources/` → gộp/đối chiếu vào `documents/method.md` → mỗi lệnh thử → 1 dòng trong `journal/`.

## Cấu trúc

```
documents/
  plan.md            ← kế hoạch + phân công (NotebookLM/Agy/Claude) + câu hỏi mở
  handoff/           ← prompt giao việc cho NotebookLM / Agy
  method.md          ← tài liệu phương pháp (bản sống, sẽ hợp nhất dần)
  glossary.md        ← thuật ngữ: hộp, R, SL, TP...
  open-questions.md  ← chỗ video mâu thuẫn / chưa rõ, cần Owner chốt
sources/
  INDEX.md           ← danh sách video đã xem + trạng thái
  _template.md       ← mẫu ghi chú 1 video
journal/
  trades.md          ← nhật ký lệnh (cả lệnh thắng lẫn thua)
images/              ← ảnh chart minh hoạ (đặt tên theo lệnh: 2026-11-xx_pair_buy.png)
```

## Quy tắc làm việc

1. **Mọi quy tắc trong `method.md` phải trỏ về nguồn** (video + timestamp). Không có nguồn = ghi "giả định", không ghi như sự thật.
2. **Video mâu thuẫn nhau thì không tự chọn** — ghi vào `open-questions.md` cho Owner quyết.
3. **Ghi cả lệnh thua.** Nhật ký chỉ có lệnh thắng thì không kiểm chứng được gì.
4. Đây là tài liệu học tập/ghi chép cá nhân, **không phải lời khuyên đầu tư**. Rủi ro mất vốn khi trade FX là có thật.
