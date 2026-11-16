# Bộ prompt cho NotebookLM / Agy

**Cách dùng:** tạo 1 notebook, thêm các link video YouTube (3–5 video gốc về "3 hộp" trước, đừng nạp cả kênh). Chạy lần lượt các prompt, copy kết quả về repo.
Yêu cầu chung dán kèm mọi prompt: *"Chỉ dùng nội dung có trong nguồn. Mỗi ý kèm tên video và timestamp. Nếu nguồn không nói, ghi 'KHÔNG NÓI'. Không tự suy diễn."*

## P1 — Định nghĩa
> Trong các video, "3 cái hộp" là gì? Liệt kê từng hộp: tên/màu, cách xác định (dựa vào cái gì: vùng giá, phiên, cấu trúc, MA...), ý nghĩa. Nếu video dùng số hộp khác 3 (vd chuỗi nhiều hộp), giải thích khi nào dùng cái nào.

## P2 — Điều kiện vào lệnh
> Liệt kê chính xác điều kiện vào lệnh BUY và SELL: xu hướng cần có, hộp nào, tín hiệu xác nhận (nến, phá vỡ, retest, RSI, MA, volume), khung thời gian, cặp tiền/phiên. Khi nào video nói KHÔNG nên vào lệnh?

## P3 — SL / TP / R
> Đặt SL ở đâu? Đặt TP ở đâu? Mục tiêu bao nhiêu R? Có dời SL về hoà vốn / chốt từng phần không? Có ví dụ nào lệnh +3R và +1R không, đặt TP theo cơ sở nào?

## P4 — Quản lý vốn
> % rủi ro mỗi lệnh, khối lượng lệnh tính thế nào, số lệnh tối đa, quy tắc dừng giao dịch trong ngày/tuần.

## P5 — Ví dụ & tỷ lệ thắng
> Liệt kê mọi ví dụ lệnh trong video: ngày, cặp, hướng, entry/SL/TP, kết quả. Video có nêu ví dụ THUA hoặc tỷ lệ thắng thực tế không? Có số liệu backtest nào không?

## P6 — Mâu thuẫn giữa video
> Chỉ ra chỗ các video nói khác nhau về định nghĩa hộp, điều kiện vào, SL/TP. Lập bảng: chủ đề | video A nói | video B nói.

## P7 — Chỉ báo trên chart
> Chart dùng 2 MA, RSI(8), Volume. Nguồn có nói loại MA, chu kỳ, và vai trò của từng chỉ báo trong phương pháp không?

## Định dạng trả về
Mỗi video → 1 file theo `../../sources/_template.md`; đặt tên `NN-ten-ngan.md`; cập nhật `../../sources/INDEX.md`.
