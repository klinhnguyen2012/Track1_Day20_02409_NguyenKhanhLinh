# AI Support Log — Ăn Gì Đây?

- **Brainstorm core action:** AI giúp tôi cân nhắc giữa “xem công thức được gợi ý” và “nấu món được gợi ý bằng nguyên liệu đang có”. AI đặt câu hỏi phản biện như: *Hành vi nào chứng minh người dùng thật sự nhận value? Xem công thức đã đủ chưa, hay cần xác nhận đã nấu?* Tôi chọn hành vi nấu và xác nhận vì nó gần core value hơn.
- **Gợi ý tracking:** AI đề xuất event `meal_cooked` và acceptance criteria mẫu: chỉ ghi event sau khi người dùng xác nhận đã nấu, không ghi khi chỉ xem hoặc chọn công thức; tải lại hoặc retry không được tạo event trùng.
- **Thử thách core job và cadence:** AI đóng vai sinh viên AI20K khó tính, hỏi liệu tôi có thật sự nấu ở nhà thường xuyên không, hay thường ăn ngoài khi mệt; nếu chỉ nấu vài lần mỗi tuần thì đo theo dịp nấu ăn tự nhiên có hợp lý hơn ép daily không? Các câu hỏi này giúp tôi xem lại giả định về core job và nhịp quay lại.
