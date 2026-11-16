# Kế hoạch dự án fx-3-box (bản nháp để Owner duyệt)

> Soạn theo tinh thần brainstorming (khám phá bối cảnh → làm rõ → đề xuất hướng → thiết kế từng phần → duyệt rồi mới làm).
> Skill `/brainstorming` thật của Superpowers **chưa được bật** trong phiên này — đây là bản áp dụng tay. Bật plugin xong sẽ chạy lại bản chuẩn.

## 1. Bối cảnh (đã biết)
- Kênh nguồn: https://youtube.com/@tiensanhforex
- Chart tham chiếu: `images/ref_XAUUSD_H1_5-boxes_sell-limit.png` — **XAUUSD, H1**, 2 đường MA (đỏ nhanh, xanh chậm), RSI(8), Volume, 2 trendline xanh ở đỉnh, **5 hộp xanh** xếp bậc thang giảm dần, hộp cuối nằm ở đáy ~3850.
- Lệnh chờ đang treo trên chart: SELL LIMIT @ 4144, SL 4152 (rủi ro ~8 điểm giá) — là lệnh mới, chưa phải 1 trong 2 lệnh đã lãi.
- Kết quả thử tay: 1 sell +3R, 1 buy +1R (tại hộp xanh cuối). n=2.

## 2. Quan sát ban đầu từ chart (GIẢ THUYẾT, cần video xác nhận)
- Mỗi hộp có vẻ là một **vùng đi ngang/hồi ngắn** giữa hai nhịp giảm; hộp sau thấp hơn hộp trước → cấu trúc xu hướng giảm (lower-high, lower-low).
- Giá chạy dưới cả hai MA trong suốt chuỗi hộp.
- Chart có **5 hộp**, không phải 3 → "3 hộp" có thể là: 3 hộp liên tiếp thì vào lệnh? hay 3 là số hộp tối thiểu? hay tên gọi 3 loại hộp? **Đây là câu hỏi số 1 cần video trả lời.**
- Mọi hộp trên chart được vẽ **sau khi giá đã đi** → nguy cơ thiên kiến nhìn lại (hindsight). Phương pháp chỉ đáng tin nếu quy tắc vẽ hộp áp dụng được **theo thời gian thực**, từng nến một.

## 3. Phân công (đề xuất)
| Việc | Ai làm | Vì sao |
|------|--------|--------|
| Xem video, trích quy tắc kèm timestamp | **NotebookLM** (ưu tiên) hoặc Agy | NotebookLM nhận link YouTube làm nguồn, trả lời có trích dẫn từng đoạn; rẻ hơn nhiều so với tôi xem video |
| Đưa kết quả về dạng chuẩn (`sources/NN-*.md`) | Owner dán / Agy xuất file | Giữ đúng mẫu `_template.md` |
| Đối chiếu nhiều video, tìm mâu thuẫn, hợp nhất `method.md` | **Claude (PM)** | Làm trên văn bản, không cần xem video |
| Biến quy tắc thành **checklist máy đọc được** | Claude | Để kiểm chứng không mơ hồ |
| Kiểm chứng: thống kê nhật ký, backtest | Claude + dữ liệu giá từ Owner | Cần CSV giá XAUUSD H1 |
| Chốt mọi quy tắc cuối, quyết khi video mâu thuẫn | **Owner** | Quyết định của bạn |

> Ghi chú: tôi hiểu "Agy" là Google Antigravity — bạn xác nhận giúp. Tôi không có quyền điều khiển Agy/NotebookLM từ phiên này; bạn chạy các prompt trong `documents/handoff/` rồi đưa kết quả về repo.

## 4. Ba hướng tổng thể (chọn 1)
- **A. NotebookLM trước (khuyên dùng):** nạp 10–20 video vào 1 notebook → chạy bộ prompt trích xuất → dán kết quả về repo → tôi hợp nhất/kiểm chứng. Rẻ, có trích dẫn, ít bịa.
- **B. Agy làm tất cả phần video:** Agy xem và viết thẳng các file `sources/`. Tự động hơn, nhưng cần soát kỹ vì dễ bỏ sót chi tiết/ảo giác.
- **C. Tôi tự lấy transcript:** chỉ khả thi nếu mạng của phiên này cho phép và video có phụ đề; tốn token nhất. Chỉ dùng cho vài video then chốt để đối chứng.

## 5. Các giai đoạn
1. **Chốt định nghĩa** (nhanh): Owner trả lời câu hỏi mở bên dưới + chọn 3–5 video "gốc" của kênh nói về phương pháp 3 hộp.
2. **Trích xuất:** chạy `handoff/notebooklm-prompts.md` trên các video gốc → `sources/01-…md`.
3. **Hợp nhất:** tôi đối chiếu → `method.md` v0.1 + `open-questions.md`. Owner chốt mâu thuẫn.
4. **Formalize:** viết checklist vào/ra lệnh từng bước, không còn chỗ "cảm nhận".
5. **Kiểm chứng:**
   - 5a. Đánh dấu lại 2 lệnh đã lãi bằng checklist: checklist có *tự đưa ra* đúng 2 lệnh đó không? Nếu không → quy tắc còn thiếu.
   - 5b. Backtest tay/semi-auto trên ≥30–50 setup trong dữ liệu quá khứ XAUUSD H1 (ghi cả thua), tính tỷ lệ thắng, R trung bình, drawdown, số lệnh/tháng.
   - 5c. Forward-test demo vài tuần, nhật ký trong `journal/`.
6. **Quyết định đi tiếp:** chỉ khi có số liệu 5b/5c mới bàn chuyện tiền thật hoặc tự động hoá.

## 6. Tiêu chí "xong" cho từng bước
- `method.md`: mỗi quy tắc có nguồn video+timestamp hoặc gắn nhãn "giả định".
- Checklist: người lạ đọc xong vẽ ra đúng hộp trên chart mẫu.
- Kiểm chứng: có bảng thống kê n ≥ 30 lệnh, kèm ảnh/ghi chú từng lệnh; nêu rõ kết quả xấu nếu có.

## 7. Rủi ro đã thấy
- **Mẫu nhỏ & hindsight:** 2 lệnh thắng + hộp vẽ sau sự kiện → chưa chứng minh gì.
- **Video YouTube có thiên kiến chọn lọc:** kênh thường chỉ chiếu ví dụ đẹp. Cần tìm cả ví dụ thất bại.
- **Vàng biến động mạnh, đòn bẩy lớn:** SL 8 điểm giá trên XAUUSD và khối lượng lệnh phải tính đúng, kẻo 1R lớn hơn dự kiến.
- **Tài chính:** đây là ghi chép học tập, không phải lời khuyên đầu tư.

## 8. Câu hỏi mở cho Owner (xem thêm `open-questions.md`)
1. Phương pháp áp dụng cho **chỉ vàng (XAUUSD)** hay nhiều cặp FX? Khung H1 hay có khung khác?
2. "3 hộp" nghĩa là gì theo video? (chart có 5 hộp.)
3. Hai MA là MA gì (EMA/SMA, chu kỳ)? RSI(8) và Volume có vai trò vào lệnh không hay chỉ là nền?
4. Hai lệnh đã lãi: cặp, ngày, entry/SL/TP — và lệnh buy +1R ở hộp xanh cuối vào theo tín hiệu gì?
5. Bạn có dữ liệu giá lịch sử (xuất CSV từ MT5) để backtest không?
6. Chọn hướng A, B hay C?
