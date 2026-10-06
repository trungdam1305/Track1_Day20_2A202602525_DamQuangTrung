# AI Support Log — Đàm Quang Trung (2A202602525)

Công cụ: Claude Code (Claude). Áp dụng cho tệp [metrics_pack.md](metrics_pack.md).

| Phase | Dùng AI để làm gì | Quyết định cuối cùng của tôi |
|---|---|---|
| — | Tạo khung tệp từ template của brief (Claude Code) | Không có quyết định nội dung |
| 0 | Đọc code dự án, tóm tắt tính năng thành dòng "Dự án" | Tôi xác nhận mô tả |
| 0 | Gợi ý 3 persona từ code (level N5/N4) | Tôi chọn: người tự học thi N5/N4 |
| 1 | Brainstorm 4 ứng viên core action (nộp đề thi thử, sửa câu trong sổ lỗi sai, đánh dấu đã nhớ, hoàn thành phiên ôn) + chấm sơ bộ 5 tiêu chí | Tôi chọn: **hoàn thành một phiên ôn flashcard** — _Lý do: Flashcard là tính năng miễn phí, cốt lõi, tần suất lặp lại cao nhất giúp người học rèn luyện phản xạ nhớ từ vựng liên tục mà không bị giới hạn bởi gói trả phí._ |
| 2 | Phản biện nguy cơ bẫy Daily cadence từ streak login; gợi ý các góc nhìn phân tích nhịp học tự nhiên | Tôi tự phân tích lịch học và quyết định cadence Weekly (3–4 ngày/tuần), tự viết câu kết luận ở cấp User |
| 3 | Gợi ý các phương án cấu trúc NSM và counter-metric chống click bừa | Tôi tự chọn NSM (Weekly Active Learners Completing ≥ 3 Quality Sessions), tự chốt ngưỡng chất lượng phiên và counter-metric Speed-clicking Rate |
| 4 | Rà soát cấu trúc 6 thành phần của Retention và chỉ ra sự không khớp giữa window và cadence | Tôi chốt định nghĩa Weekly Retention theo tuần tương đối từ cohort entry (Wn = ngày 7n → 7n+6), bỏ mô tả "rolling" để chuẩn hóa kỹ thuật |
| 5 | Gợi ý khung Product Loop (Progress loop) và phản biện lỗi lệch mẫu (selection bias) của nhóm so sánh trong hypothesis | AI gợi ý Progress loop, tôi đồng ý giữ; tôi tự viết lại metric hypothesis so sánh trong nhóm active W1–W2 có từ yếu và xác định mức tăng tuyệt đối |
| 6 | Gợi ý cú pháp tên event theo chuẩn object_action, chủ động đề xuất bổ sung account_registered và exam_target_set | AI thêm 2 event này, tôi đồng ý và duyệt bảng 7 event; tự chốt tiêu chí nghiệm thu chặt chẽ theo từng session_id |
| 7 | Đối chiếu checklist 7 câu hỏi và rà soát các trường trong database/model | Tôi tự đánh giá đạt cả 7 tiêu chí và xác nhận phát hiện lỗi tính streak theo login trong StudentUser.java |
| 1–6 | AI soát bài theo 5 gate, chỉ ra các lỗi kỹ thuật và trực tiếp sửa tệp theo yêu cầu của tôi | Tôi kiểm tra, nghiệm thu toàn bộ các sửa đổi kỹ thuật của AI (start event, window tuần tương đối, thẻ hợp lệ, kết thúc phiên, bảng event, tiêu chí nghiệm thu) |
| 4 | AI phản biện metric hypothesis (thiên lệch sống sót của nhóm so sánh, khung thời gian W4 = ngày 28–34, baseline ngầm định) và thêm mục "Điều kiện kiểm chứng" (cần build tính năng Ôn từ yếu, gợi ý A/B test) | Câu metric hypothesis do tôi tự viết và tự sửa |
