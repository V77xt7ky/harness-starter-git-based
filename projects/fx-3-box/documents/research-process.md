# Quy trình nghiên cứu fx-3-box (bản hoàn chỉnh v1)

Mục tiêu: biến nội dung rải rác trong video/bài viết thành **bộ quy tắc kiểm chứng được**, và biết rõ chỗ nào còn là giả định. Không nhằm chứng minh phương pháp "đúng" — nhằm biết nó đúng đến đâu.

## Vai trò
| Vai | Làm gì | Không làm |
|-----|--------|-----------|
| **Owner** | Cung cấp nguồn, chốt quy tắc, tự trade & ghi nhật ký, quyết định cuối | — |
| **NotebookLM / Agy** | Trích xuất từ video: chỉ điều nguồn nói, có timestamp | Đánh giá, suy diễn, bổ sung kiến thức chung |
| **Claude** | Phản biện, đối chiếu, hợp nhất, formalize, thống kê, backtest | Xem hàng loạt video; tự chốt quy tắc khi nguồn mâu thuẫn |

## Luồng (6 giai đoạn, mỗi giai đoạn có cổng)
```
G0 Nguồn ─► G1 Trích xuất ─► G2 Phản biện ─► G3 Hợp nhất ─► G4 Formalize ─► G5 Kiểm chứng ─► G6 Quyết định
```

### G0 — Thu thập nguồn
- Vào: link video, bài Facebook, ảnh chart.
- Ra: `sources/INDEX.md` mỗi nguồn 1 dòng + trạng thái (công khai / hội viên / chưa đọc được).
- **Nguồn không truy cập được** (Facebook, video hội viên): Owner dán nội dung/transcript, hoặc ghi "không xử lý". Không đoán.
- **Cổng:** mọi nguồn đều có trạng thái rõ.

### G1 — Trích xuất (NotebookLM/Agy)
- Dùng `documents/handoff/agy-brief.md` hoặc `notebooklm-prompts.md`.
- Ra: `sources/NN-*.md` theo `_template.md` + `SYNTHESIS-agy.md` (nếu Agy).
- Không đưa quy trình riêng của Owner (7b) cho bên trích xuất, tránh thiên kiến xác nhận.
- **Cổng:** mỗi quy tắc có timestamp; chỗ không nói ghi "KHÔNG NÓI".

### G2 — Phản biện (Claude)
- Theo `review/README.md`: 8 phép thử (nguồn / thời gian thực / đo được / thiên kiến chọn lọc / nhất quán chéo / số liệu R / bán hàng / đối chiếu Owner).
- Ra: `review/NN-critique.md` + 3–5 câu hỏi cho Owner.
- **Cổng:** chỉ quy tắc "Nhận" đi tiếp.

### G3 — Hợp nhất
- Điền `documents/method.md` chỉ từ quy tắc "Nhận". Mỗi dòng kèm nguồn.
- Mâu thuẫn / mơ hồ → `open-questions.md`. Owner chốt, ghi lại ai quyết và vì sao (ADR nếu lớn, `management/decisions/`).
- **Cổng:** không còn quy tắc nào không nguồn trong `method.md`.

### G4 — Formalize
- Viết **checklist vào/ra lệnh** từng bước, ngưỡng đo được: đỉnh/đáy hộp tính theo gì, "50% hộp" tính thế nào, nến xác nhận cụ thể, SL, TP, khối lượng theo R.
- Kiểm tra "người lạ + chart mẫu → vẽ ra cùng hộp": thử trên `images/ref_*.png` và 2 lệnh đã lãi.
- **Cổng:** checklist tái hiện đúng 2 lệnh của Owner mà không cần biết kết quả trước.

### G5 — Kiểm chứng
- **5a. Tái hiện:** checklist có tự sinh lại 2 lệnh đã lãi không?
- **5b. Backtest tay trên quá khứ** (XAUUSD, BTC, H1): ≥30–50 setup, ghi cả thua, ghi trước khi nhìn kết quả (che chart bên phải). Ra: tỷ lệ thắng, R trung bình, expectancy, chuỗi thua dài nhất, drawdown (đơn vị R), số lệnh/tháng.
- **5c. Forward-test demo** vài tuần, `journal/trades.md`, mỗi lệnh có ảnh chart lúc vào.
- Chia mẫu: tuning (quy tắc chỉnh được) và holdout (không chỉnh), để tránh khớp quá mức.
- **Cổng:** n ≥ 30 lệnh, có số liệu; nêu cả kết quả xấu.

### G6 — Quyết định
- Dựa số liệu: bỏ / giữ & chỉnh / thử vốn nhỏ. Tự động hoá (EA/bot) chỉ bàn sau G5 đạt.
- Không phải lời khuyên đầu tư; quyết định và rủi ro là của Owner.

## Ngưỡng kết luận (đặt trước để không tự lừa mình)
- Kết quả tốt khi: expectancy > 0 sau phí/spread/trượt giá, trên cả tuning và holdout, ≥30 lệnh mỗi tài sản.
- Kết quả không đủ: n < 30, hoặc chỉ tốt ở một giai đoạn/tài sản, hoặc phụ thuộc vào việc vẽ hộp sau khi giá đã đi.
- Mọi con số lệnh thật nhớ trừ spread/phí; vàng và BTC biến động mạnh, tính khối lượng theo SL.

## Theo dõi
- Board: `management/backlog/0002-fx-3-box-method.md` (cập nhật phase khi xong cổng).
- Nhật ký phiên bản: mục "Lịch sử thay đổi" cuối `method.md`.
