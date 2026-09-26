# [SquadMetrics] — SE100 · Nhóm 11

Hệ thống quản lý đội tuyển thi đấu phục vụ ba nhóm người dùng: huấn luyện viên, thủ quỹ và thành viên (thử việc hoặc chính thức), cùng ứng cử viên nộp hồ sơ từ bên ngoài.

Huấn luyện viên dùng hệ thống để đăng tin tuyển, xét duyệt hồ sơ, đánh giá thử việc, lập lịch tập và chốt đội hình thi đấu, nhằm vận hành đội theo đúng lộ trình tuyển → thử → chính thức → thi đấu.

Thủ quỹ dùng hệ thống để tạo khoản đóng quỹ theo tháng, nhắc và xác nhận thanh toán, ghi nhận thu chi, nhằm duy trì quỹ đội minh bạch và đủ chi tiêu.

Thành viên dùng hệ thống để xem lịch biểu, đóng quỹ qua QR và theo dõi kết quả thi đấu cá nhân, nhằm chủ động thời gian và nắm được tình trạng của mình trong đội.

Điều không được phép xảy ra: quỹ đội chi vượt quá số dư hiện có tại bất kỳ thời điểm nào, và một thành viên chưa qua thử việc lại được xếp vào đội hình thi đấu chính thức.

## Thành viên

| Tên | GitHub | Chủ trì mốc |
|---|---|---|
| Trần Thị Hoài Ngọc | Rawisl | M1: Yêu cầu |
| Lê Nguyễn Hữu Khang | WhoKeng | M2: Mô hình hoá |
| | | M3–M4: Thiết kế |
| | | M5: Giao hàng |

## URL

- Bản chạy: [https://squadmetrics.id.vn](https://squadmetrics.id.vn/)
- Pipeline: xem tab Actions

## Cấu trúc repo

```
docs/         yêu cầu, đặc tả use case, phân tích tác động
diagrams/     sơ đồ Mermaid (.mmd) — use case, lớp, tuần tự, trạng thái, C4
adr/          quyết định kiến trúc, mỗi quyết định một tệp
phan-tu/      bản phản tư M0–M5 và bảng phản hồi cáo buộc
ai-log/       bản ghi hội thoại với agent, theo mốc
src/          mã nguồn
.github/      workflow kiểm mốc — đừng sửa
AGENTS.md     ràng buộc kiến trúc cho agent đọc — viết ở M4
```

## Mốc

| Mốc | Hạn | Nộp gì | CI kiểm thêm |
|---|---|---|---|
| M0 | CN tuần 2 | README, đề tài, `docs/cau-hoi-khach-hang.md` (≥ 3 câu) | 4 người có commit |
| V1 | CN tuần 4 | Hệ thống chạy, `docs/hoi-cuu-vong1.md`, ai-log | Giảng viên kiểm tay, không tính điểm |
| M1 | CN tuần 5 | `docs/yeu-cau.md` | ≥ 3 tác nhân, ≥ 6 FR, ≥ 3 NFR có số, ≥ 1 BR |
| M2 | CN tuần 7 | `diagrams/use-case.mmd` (≥ 5 UC), `docs/dac-ta-UC-*.md` ×3, `diagrams/seq-*.mmd` ×2 | Mermaid parse được |
| M3 | CN tuần 9 | `diagrams/class.mmd` (≥ 5 lớp), `diagrams/state.mmd`, `docs/tu-danh-gia-M3.md` | Đối chiếu chéo lớp ↔ sequence; mọi lớp có trong docs/ |
| M4 | CN tuần 10 | `diagrams/c4-context.mmd`, `c4-container.mmd`, `docs/du-lieu.md`, `adr/0001-*.md`, `AGENTS.md` | ADR có ≥ 2 phương án; AGENTS.md hết comment mẫu |
| M5 | CN tuần 13 | Pipeline riêng xanh, URL sống, `docs/tac-dong-vong3.md`, `docs/trung-lap.md` có 2 lần đo | URL trả 200 |

Mốc nào cũng kèm `phan-tu/Mn.md` (M0 ≥ 40 từ, còn lại ≥ 120 từ, có mã commit) và một tệp trong `ai-log/`. Từ M2 thêm `phan-tu/Mn-phan-hoi.md`.

## Cách nộp mốc

1. Tạo nhánh `moc/Mn` rồi làm việc trên đó.
2. Mở Pull Request vào `main`, tiêu đề `Mn — [tên nhóm]`.
3. Đợi workflow **Kiểm mốc** chạy. Đỏ thì đọc log, sửa, push lại.
4. Xanh thì merge. Thời điểm merge là thời điểm nộp.
