# Track1_Day20_2A202602525_DamQuangTrung

- **Họ tên:** Đàm Quang Trung
- **MHV:** 2A202602525
- **Dự án chọn làm:** Web app luyện thi JLPT N5–N4 (dự án cá nhân) — use case: người tự học ôn từ vựng bằng flashcard.
- **Metrics Pack:** [metrics_pack.md](https://github.com/trungdam1305/Track1_Day20_2A202602525_DamQuangTrung/blob/main/metrics_pack.md) (repo public)
- **AI Support Log:** [ai-support-log.md](ai-support-log.md)

## Điều tôi mang về áp dụng cho dự án thật

1. **Sửa lỗi tính Streak ảo theo lượt đăng nhập:** Trong `StudentUser.java`, hiện tại `streakCount` đang được cộng dựa trên `lastLoginDate` (chỉ cần đăng nhập là tăng streak) — đây là vanity metric kinh điển. Tôi sẽ sửa lại logic backend: chỉ tăng streak khi học viên có hành động tạo ra giá trị thật trong ngày (hoàn thành ít nhất 1 phiên ôn flashcard đạt chuẩn `flashcard_session_completed` hoặc nộp 1 bài thi thử `quiz_attempt_submitted`).
2. **Bổ sung khái niệm "Phiên học" (Session) vào backend & frontend:** Trong `FlashcardService.java` hiện tại, hệ thống chỉ lưu trạng thái từng từ riêng lẻ (`UserWordMetric`) mà không có khái niệm `session_id`, thời điểm bắt đầu/kết thúc phiên hay thời gian xem thẻ (`dwell_ms`). Tôi sẽ bổ sung cấu trúc phiên học để theo dõi thời lượng thực tế và gắn acceptance criteria (≥ 10 thẻ, ≥ 1.5s/thẻ) nhằm lọc click-spam.
3. **Khép kín Progress Loop (Tính năng "Ôn từ vựng chưa thuộc"):** Hiện tại trên Dashboard, khi bấm vào danh sách từ yếu (`weakVocabulary`), giao diện chỉ chuyển sang `/flashcards` mở toàn bộ deck mà chưa lọc riêng các từ này. Để hoàn thiện chu kỳ 2 của Progress loop, tôi sẽ build tính năng cho phép mở phiên ôn tập riêng chỉ chứa các từ có trạng thái `NOT_MASTERED` để giúp học viên giải quyết dứt điểm lỗ hổng kiến thức.
4. **Bổ sung trường ngày thi mục tiêu (`target_exam_date`):** Thêm trường khai báo ngày thi dự kiến vào `StudentUser` để phân nhóm học viên (gấp ≤ 2 tháng vs bình thường > 2 tháng). Từ đó thiết kế thuật toán nhắc nhở ôn tập ngắt quãng (Spaced Repetition) sát với nhịp sinh hoạt thực tế và đo lường Retention theo đúng phân khúc người dùng.
