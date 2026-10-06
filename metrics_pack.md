# Metrics Pack — Đàm Quang Trung (2A202602525)

> Chuỗi: Core action → Nature → Metric + Retention → Loop (giả thuyết) → Tracking (phép thử)

---

## 00 — Phạm vi

1. **Dự án:** Web app luyện thi JLPT N5–N4 (dự án cá nhân `C:\IndiProject\individual`) — tra từ vựng + flashcard đánh dấu đã nhớ/chưa nhớ (miễn phí), quiz/đề thi thử tự chấm + sổ lỗi sai (gói Quiz Premium), dashboard tiến độ cá nhân.
2. **Persona:** Người tự học thi JLPT N5/N4 (không theo trung tâm), đã có mục tiêu một kỳ thi JLPT cụ thể.
3. **Core job** (lời người dùng, không phải tính năng): "Tôi cần tích lũy và duy trì vốn từ vựng N5/N4 đều đặn mỗi tuần để không bị học trước quên sau, kịp nhớ hết lượng từ cần thiết trước kỳ thi JLPT mà không phải tốn tiền đi học thêm ở trung tâm."

---

## 01 — Core Action

### Bốn khái niệm

| Khái niệm | Câu hỏi | Câu trả lời |
|---|---|---|
| Core job | User đang cố hoàn thành việc gì? | "Tôi cần tích lũy và duy trì vốn từ vựng N5/N4 đều đặn mỗi tuần để không bị học trước quên sau, kịp nhớ hết lượng từ cần thiết trước kỳ thi JLPT." |
| Core action | User làm gì trong sản phẩm để tiến tới giá trị? | Hoàn thành một phiên ôn tập flashcard (lật thẻ và đánh dấu Đã thuộc / Chưa thuộc cho một tập từ vựng). |
| Core value | User nhận được lợi ích gì? | Nhận biết chính xác từ nào đã thuộc, từ nào chưa thuộc để củng cố trí nhớ dài hạn (retrieval practice) và theo dõi tiến độ học tăng lên. |
| Core value event | Sự kiện nào chứng minh value đã xảy ra? | Sự kiện kết thúc một phiên ôn tập đạt chuẩn (≥ 10 thẻ hợp lệ, mỗi thẻ xem ≥ 1.5 giây): `flashcard_session_completed`. |

### Core Action Card

| Thành phần | Câu trả lời |
|---|---|
| Target user | Người tự học thi JLPT N5/N4, học tranh thủ thời gian rảnh. |
| Core job | "Tôi cần tích lũy và duy trì vốn từ vựng N5/N4 đều đặn mỗi tuần để không bị học trước quên sau, kịp nhớ hết lượng từ cần thiết trước kỳ thi JLPT." |
| Core action | Hoàn thành một phiên ôn flashcard (Review Session Completed). |
| Object | Bộ flashcard từ vựng theo trình độ (Level N5 hoặc N4). |
| Preconditions | Đã đăng nhập tài khoản học viên, chọn cấp độ từ vựng, mở màn hình Flashcard. |
| Completion rule | **Phiên** bắt đầu khi thẻ đầu tiên được đánh dấu và **kết thúc** khi học viên bấm "Kết thúc phiên" hoặc không thao tác quá 5 phút. Phiên được tính là hoàn tất khi có **≥ 10 thẻ hợp lệ** — thẻ hợp lệ là thẻ được đánh dấu Đã thuộc / Chưa thuộc với thời gian xem **của chính thẻ đó** ≥ 1.5 giây (loại bỏ click bừa; không dùng trung bình để tránh bù trừ). Mỗi thẻ chỉ tính 1 lần trong một phiên. |
| Core value | Nâng cao khả năng ghi nhớ từ vựng thực tế và đo lường được tiến độ học cá nhân. |
| Evidence of value | Thanh tiến độ % mastered tăng lên hoặc danh sách từ yếu (Weak Vocabulary) được cập nhật trên Dashboard để tiếp tục ôn luyện. |
| Candidate event | `flashcard_session_completed` |

### Tự kiểm 5 tiêu chí

| # | Tiêu chí | Đạt? | Lý do |
|---|---|---|---|
| 1 | Gần core value | Đạt | Việc lật và phân loại Đã thuộc / Chưa thuộc kích hoạt phản xạ gợi nhớ chủ động (retrieval practice) - cốt lõi của việc nhớ từ vựng lâu dài. |
| 2 | Có thể lặp lại | Đạt | Kho từ vựng N5/N4 có hàng trăm từ; học viên cần ôn đi ôn lại nhiều phiên trong tuần suốt lộ trình 3-6 tháng trước kỳ thi. |
| 3 | Có thể quan sát | Đạt | Hệ thống ghi nhận được sự kiện hoàn thành phiên khi học viên thực hiện đủ 10 thẻ hợp lệ kèm thời gian học. |
| 4 | Có ý nghĩa | Đạt | Đã có ràng buộc thời gian (≥ 1.5s/thẻ) và đánh dấu trạng thái 2 chiều, đảm bảo người học có tương tác tư duy chứ không chỉ lướt qua màn hình. |
| 5 | Có thể tác động | Đạt | Team sản phẩm có thể tối ưu luồng ôn tập, gợi ý danh sách từ yếu trên Dashboard, gửi lời nhắc đến hạn ôn (spaced repetition). |

**Vì sao không phải "mở app" / "hỏi AI":**
- "Mở app" chỉ là hành vi truy cập bề mặt (vanity metric), không chứng minh người học có thực sự tiếp thu hay rèn luyện kiến thức.
- "Hỏi AI" hay "lướt xem thẻ" chỉ là tiếp nhận thụ động (passive consumption); chỉ khi người học tự gợi nhớ và phân loại trạng thái ghi nhớ trong một phiên hoàn chỉnh thì giá trị học tập mới thực sự được tạo ra.

---

## 02 — Nature & cadence

### Action Nature Card

| Thành phần | Câu trả lời |
|---|---|
| Actor | Học viên tự học JLPT (StudentUser). |
| Intent | Ôn luyện, ghi nhớ từ vựng để chuẩn bị cho kỳ thi JLPT N5/N4. |
| Trigger | Thói quen học tập cá nhân, danh sách từ yếu trên Dashboard, hoặc mục tiêu duy trì tiến độ trước ngày thi. |
| Effort | Vừa phải (3–5 phút tập trung cho 1 phiên 10–15 thẻ). |
| Value timing | Ngay lập tức (nhận biết từ nhớ/quên và thấy % tiến độ cập nhật ngay sau khi hoàn thành phiên). |
| State | Cập nhật bản ghi `UserWordMetric` (status, lastReviewedAt) và cập nhật danh sách `weakVocabulary` trên Dashboard. |
| Dependency | Thiết bị có kết nối mạng, dữ liệu từ vựng theo level đã được cấu hình trong hệ thống. |
| Repeat condition | Còn từ vựng chưa thuộc hoặc đến chu kỳ cần ôn lại theo quy luật quên. |

### Kết luận cadence

- **Dạng hành vi:** Thói quen học tập vi mô lặp lại theo tuần (Weekly habit).
- **Kết luận:** Đối với người tự học thi JLPT N5/N4, core action hoàn thành một phiên ôn flashcard thường xuất hiện 3–4 ngày mỗi tuần vì việc ghi nhớ từ vựng cần sự đều đặn nhưng người tự học (sinh viên/người đi làm) có lịch sinh hoạt biến động, khó cam kết học đủ 7/7 ngày liên tục. Do đó, nhịp đo phù hợp là Weekly ở cấp User.

---

## 03 — Metric System

### Activation

| | Định nghĩa |
|---|---|
| Start event | `account_registered` — tài khoản học viên được tạo thành công (không dùng đăng nhập làm mốc). |
| Activation event | `flashcard_session_completed` (phiên ôn flashcard đầu tiên đạt chuẩn ≥ 10 thẻ hợp lệ) |
| Time window | Trong vòng 24 giờ kể từ thời điểm đăng ký (Day 1) |

### Engagement (tối đa 2 góc đo)

- **Tần suất (Frequency):** Active Review Days / Week (Số ngày trong tuần có ít nhất 1 phiên ôn hoàn thành).
- **Cường độ (Intensity):** Weekly Cards Reviewed (Tổng số thẻ từ vựng được ôn tập hợp lệ trong tuần).

### North Star Metric

- **NSM:** Weekly Active Learners Completing ≥ 3 Quality Review Sessions (Số học viên tích cực hoàn thành ≥ 3 phiên ôn tập đạt chuẩn mỗi tuần).
  - Unit of value: 1 phiên ôn tập hoàn thành đạt chuẩn; NSM đếm số **học viên** đạt ≥ 3 phiên như vậy trong một tuần (đơn vị đếm: learner-week).
  - Quality threshold: Phiên chỉ được tính khi có ≥ 10 thẻ hợp lệ (mỗi thẻ xem ≥ 1.5 giây, đánh dấu Đã thuộc / Chưa thuộc), theo completion rule ở mục 01.
  - Frequency: Hàng tuần (Weekly).

### Leading indicators (tối đa 3)

| Indicator | Vì sao tin nó dự báo core action lặp lại |
|---|---|
| Day-1 Session Completion Rate | Học viên trải nghiệm và nhận được giá trị ghi nhớ ngay trong 24h đầu có xác suất duy trì thói quen học tuần cao hơn gấp nhiều lần. |
| Weak Vocabulary Click Rate | Học viên chủ động bấm vào danh sách "Từ vựng chưa thuộc" từ Dashboard chứng tỏ họ có nhận thức về lỗ hổng kiến thức và có nhu cầu quay lại phiên ôn. |
| Quiz Mock Exam Attempt Rate (chỉ áp dụng segment Premium, vì quiz yêu cầu gói trả phí) | Học viên tham gia làm bài thi thử (Quiz) sẽ nhận ra các từ vựng mình chưa thuộc trong đề, tạo động lực mạnh mẽ quay lại ôn flashcard. |

### Counter-metric (≥ 1)

| Counter-metric | Bảo vệ điều gì |
|---|---|
| Speed-clicking Rate (% thẻ được đánh dấu với thời gian xem < 1.5s) & Session Abandonment Rate (% phiên thoát khi < 10 thẻ) | Bảo vệ chất lượng học thật, ngăn chặn tình trạng học viên bấm Next / Đã thuộc liên tục chỉ để cày điểm xếp hạng (rankPoints) hoặc cày streak mà không thực sự ghi nhớ. |

---

## 04 — Retention Definition

| Thành phần | Câu trả lời |
|---|---|
| Unit | User (StudentUser đã đăng ký tài khoản). |
| Cohort entry | Học viên có sự kiện `flashcard_session_completed` đầu tiên trong tuần W0. |
| Return event | Sự kiện `flashcard_session_completed` (hoàn thành ít nhất 1 phiên ôn đạt chuẩn). |
| Window | Weekly, tính theo tuần tương đối từ cohort entry: W*n* = ngày 7*n* → 7*n*+6 kể từ thời điểm `flashcard_session_completed` đầu tiên (W1 = ngày 7–13, W2 = ngày 14–20, …). |
| Threshold | ≥ 1 phiên ôn tập hoàn thành trong tuần. |
| Segment | Phân nhóm theo trình độ mục tiêu (N5 vs N4, lấy từ `jlpt_level`) và thời gian đến kỳ thi (gấp ≤ 2 tháng vs bình thường > 2 tháng). Thời gian đến kỳ thi lấy từ `target_exam_date` của event `exam_target_set`; nếu học viên chưa khai báo thì suy ra kỳ thi JLPT gần nhất (chủ nhật đầu tháng 7 hoặc tháng 12) sau ngày `account_registered`. |

**So với ba mốc:**
- **Natural cycle:** Khớp với chu kỳ tự nhiên theo tuần của người học ngoại ngữ (thường học 3–4 buổi/tuần thay vì ép buộc hàng ngày).
- **Cohort đúng segment:** Tách riêng nhóm học viên có mục tiêu thi JLPT rõ ràng trong kỳ thi gần nhất để đo lường chính xác nhu cầu giữ chân thực tế.
- **Benchmark category:** Ngành EdTech / Ngôn ngữ có Retention W1 trung bình khoảng 20–30%, W4 khoảng 10–15% (ước lượng, chưa kiểm chứng nguồn — cần bổ sung); việc đo theo phiên chất lượng giúp tránh số liệu ảo từ việc chỉ mở app.

---

## 05 — Product Loop

- **Loại loop:** Progress loop — mỗi phiên ôn để lại trạng thái tích lũy (% mastered theo level, danh sách từ yếu), và chính phần tiến độ còn dở là lý do quay lại.

```
Nhận diện từ chưa thuộc (Natural trigger) → Mở app hoàn thành phiên ôn Flashcard (Core action) → Cập nhật thanh tiến độ % & phân loại từ nhớ/quên (Immediate value) → Lưu danh sách "Weak Vocabulary" trên Dashboard (Saved state / investment)
→ Nhìn thấy danh sách từ yếu cần ôn lại (Next natural trigger) → Bắt đầu phiên ôn các từ chưa thuộc (Core action tiếp theo) → Tăng tỷ lệ nhớ từ & sẵn sàng thi thử (Repeat value)
```

- **Chu kỳ 1:** Học viên học bộ từ vựng mới → Đánh dấu "Chưa thuộc" cho những từ khó → Hệ thống lưu các từ này vào danh sách `weakVocabulary` trên Dashboard cá nhân.
- **Chu kỳ 2:** Học viên vào Dashboard thấy danh sách từ chưa thuộc kèm thanh tiến độ chưa đạt 100% → Bấm vào ôn lại các từ này (*cần build:* hiện bấm từ yếu chỉ chuyển sang `/flashcards` cả deck, chưa mở phiên chỉ gồm từ `NOT_MASTERED`) → Đổi trạng thái sang "Đã thuộc" → Tiến độ % tăng lên → Tự tin thử sức với đề thi thử (Quiz Attempt).
- **Metric hypothesis:** Nếu loop này hoạt động, khi so sánh trong cùng tập học viên cohort W0 **vẫn còn hoạt động ở W1–W2 và đều có ≥ 1 từ Chưa thuộc**, metric Weekly Retention tại tuần W4 (ngày 28–34 kể từ cohort entry) của phân khúc có tương tác với danh sách từ yếu (phát sinh ≥ 1 sự kiện `dashboard_weak_vocab_clicked` trong W1–W2) sẽ thay đổi theo hướng **cao hơn ít nhất 5 điểm phần trăm tuyệt đối** so với phân khúc không click ôn từ yếu, vì học viên có mục tiêu khắc phục lỗ hổng kiến thức cụ thể và vòng lặp khép kín giúp giải quyết dứt điểm các từ chưa thuộc thay vì nản lòng do học dàn trải.
- **Điều kiện kiểm chứng:**
  - Hypothesis chỉ đo được loop thật sau khi build tính năng "Ôn từ yếu" (bấm từ yếu trên Dashboard mở phiên chỉ gồm các từ `NOT_MASTERED`). Trước đó, `dashboard_weak_vocab_clicked` chỉ đo cú click, chưa đo hành vi ôn từ yếu.
  - So sánh click / không click là tương quan, chưa phải nhân quả (học viên chăm chỉ vừa hay click vừa hay quay lại). Muốn chứng minh nhân quả: A/B test hiển thị / ẩn nút "Ôn từ yếu" trên Dashboard, so Weekly Retention giữa hai nhánh.

---

## 06 — Tracking nhanh

| Tên event | Ý nghĩa | Thời điểm ghi nhận | Metric sử dụng |
|---|---|---|---|
| `account_registered` | Tài khoản học viên được tạo thành công | Khi server lưu xong bản ghi StudentUser (không bắn khi mới submit form) | Activation (start event), Retention segment (suy ra kỳ thi gần nhất) |
| `exam_target_set` | Học viên khai báo/đổi ngày thi mục tiêu | Khi server lưu xong `target_exam_date` (cần build field mới) | Retention segment (thời gian đến kỳ thi) |
| `flashcard_session_started` | Một phiên ôn thực sự bắt đầu | Khi thẻ **đầu tiên** của phiên được đánh dấu (không bắn khi chỉ mở/tải lại màn hình) | Session Abandonment Rate (counter-metric) |
| `flashcard_word_marked` | Đánh dấu nhớ/chưa nhớ 1 thẻ (kèm `session_id`, `vocabulary_id`, `status`, `dwell_ms`) | Khi server lưu xong `UserWordMetric` sau khi bấm "Đã thuộc" hoặc "Chưa thuộc" | Intensity (Weekly Cards Reviewed), Counter-metric (dwell time) |
| `flashcard_session_completed` | Hoàn thành phiên ôn tập đạt chuẩn (≥ 10 thẻ hợp lệ) | Khi phiên kết thúc (bấm "Kết thúc phiên" hoặc 5 phút không thao tác) và phiên có ≥ 10 thẻ hợp lệ | Core Action, Activation, NSM, Retention |
| `dashboard_weak_vocab_clicked` | Bấm vào ôn từ yếu từ Dashboard | Khi click vào một từ trong mục Weak Vocabulary | Leading indicator, Product Loop validation |
| `quiz_attempt_submitted` | Nộp bài thi thử / quiz | Khi `QuizAttempt` chuyển từ `IN_PROGRESS` sang `SUBMITTED` và đã chấm điểm | Leading indicator, Outcome metric |

### Tiêu chí nghiệm thu (≥ 2)

1. Với mỗi `session_id`, hệ thống chỉ ghi `flashcard_session_completed` khi phiên đã **kết thúc** và có `valid_cards >= 10` (thẻ hợp lệ = `dwell_ms >= 1500`). Phiên dừng ở thẻ thứ 9, hoặc có 10 thẻ nhưng chỉ 9 thẻ hợp lệ, không được tạo event.
2. Với mỗi `session_id`, hệ thống ghi **tối đa 1** `flashcard_session_completed`. Tải lại trang, retry request hoặc gửi lại không tạo thêm event; đánh dấu lại cùng một `vocabulary_id` trong cùng phiên không làm tăng `valid_cards`.
3. Mọi event phải có đủ thuộc tính bắt buộc: `student_id`, `jlpt_level`, `timestamp`; event của tài khoản ADMIN/nội bộ bị loại khỏi metric.

---

## 07 — Tự soi lỗi (Phase 5)

| Câu hỏi | Đạt? | Ghi chú |
|---|---|---|
| Core action không phải thao tác giao diện hay output hệ thống? | Đạt | Là "hoàn thành phiên ôn tập" có kèm điều kiện đánh giá nhớ/quên và thời gian học, không phải chỉ click nút đơn thuần. |
| Activation không phải "xem hết hướng dẫn" hay "đăng nhập"? | Đạt (đã sửa) | Start event chỉ còn `account_registered` (bỏ phương án "lần đầu đăng nhập"); activation là phiên ôn đầu tiên đạt chuẩn trong 24h. |
| Frequency không cao hơn nhu cầu thật? | Đạt | Đo theo nhịp tuần (Weekly, 3–4 phiên/tuần), phù hợp với lịch sinh hoạt thực tế của người tự học. |
| Loop có reason to return ngoài notification? | Đạt | Có saved state là danh sách từ yếu (Weak Vocabulary) và thanh tiến độ dở dang trên Dashboard cá nhân. |
| Retention không dùng chung một window cho mọi cadence? | Đạt (đã sửa) | Window theo tuần tương đối từ cohort entry, khớp cadence Weekly, không dùng D1/D7. |
| Mọi event đều map về một metric? | Đạt | Cả 7 event đều map vào Activation, NSM, Engagement, Retention (kể cả segment), Leading indicator hoặc Counter-metric. |
| Metric nào cũng có event để tính nó? | Đạt (đã sửa) | Bổ sung `account_registered` (start event của activation) và `exam_target_set` (segment thời gian đến kỳ thi); `dwell_ms` trên `flashcard_word_marked` để tính Speed-clicking Rate. |

> **Phát hiện lỗi sẵn có trong mã nguồn:**
> Trong file `StudentUser.java` của dự án, trường `streakCount` đang được cộng dựa trên `lastLoginDate` (chỉ cần đăng nhập mỗi ngày là tăng chuỗi streak). Đây chính là **anti-pattern kinh điển** (đo lường hành vi bề mặt thay vì giá trị thật).
> **Đề xuất khắc phục:** Chỉ cộng streak khi có sự kiện `flashcard_session_completed` hoặc `quiz_attempt_submitted` thành công trong ngày.

---

## Revision log

- **2026-10-06 (rà soát gate):** Sửa lỗi nhất quán, không đổi core action và cadence: (1) bỏ phương án "lần đầu đăng nhập" khỏi start event; (2) bổ sung `account_registered`, `exam_target_set` để mọi metric/segment có event; (3) window retention tính theo tuần tương đối từ cohort entry thay vì vừa rolling vừa W1–W4; (4) chọn loại loop chuẩn của đề (progress); (5) định nghĩa kết thúc phiên và thẻ hợp lệ theo từng thẻ thay vì trung bình (trung bình cho phép bù trừ); (6) viết lại tiêu chí nghiệm thu chống ghi trùng khi reload/retry; (7) core job đổi "mỗi ngày" → "đều đặn mỗi tuần" cho khớp cadence.
- **2026-10-06:** Khởi tạo tài liệu, chốt Core Action là "Hoàn thành một phiên ôn flashcard", bổ sung completion rule (≥ 10 thẻ, ≥ 1.5s/thẻ) và thiết lập hệ thống metric theo nhịp Weekly.

---

## AI Support Log

Xem [ai-support-log.md](ai-support-log.md).
