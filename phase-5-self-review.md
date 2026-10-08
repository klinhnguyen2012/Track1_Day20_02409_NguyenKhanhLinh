# Phase 5 — Tự soi lỗi & nộp | Ăn Gì Đây?

## Gate 5 — Tự kiểm 7 câu

| Câu tự kiểm | Kết quả | Lý do / việc cần làm tiếp |
|---|---|---|
| **Core action có phải thao tác giao diện hay output hệ thống không?** | Đạt | Core action là nấu món được gợi ý bằng nguyên liệu đã lưu và xác nhận đã nấu. Hỏi bot hoặc nhận công thức chưa được tính là core value. Xác nhận của người dùng là bằng chứng tự báo cáo, chưa phải xác minh độc lập. |
| **Activation có phải đăng nhập hay hoàn tất hướng dẫn không?** | Đạt | Activation bắt đầu từ lúc lưu một đợt thực phẩm và chỉ tính khi có `meal_cooked` đạt điều kiện trong cửa sổ 14 ngày giả thuyết. |
| **Frequency có cao hơn nhu cầu tự nhiên không?** | Tạm đạt | NSM gắn với dịp yêu cầu gợi ý/nấu ăn tự nhiên, không dùng DAU hay streak hằng ngày. Cửa sổ 14 ngày là giả thuyết ban đầu cho nhóm sinh viên tự nấu ít nhất mỗi tuần; cần kiểm tra với sinh viên AI20K. |
| **Loop có lý do quay lại ngoài notification không?** | Đạt | Nhu cầu quyết định món cho bữa ăn, thực phẩm mới sau khi đi chợ và đồ sắp hết hạn tạo trigger tự nhiên. Notification có thể hỗ trợ nhưng không tạo ra nhu cầu ăn hoặc nấu. |
| **Retention có dùng chung một window cho mọi cadence không?** | Tạm đạt | Cửa sổ tùy chỉnh 14 ngày chỉ áp dụng cho segment mục tiêu là sinh viên tự nấu ở nhà ít nhất mỗi tuần. Nhóm nấu ít hơn cần được phân tích riêng theo cadence tự nhiên của họ. |
| **Mọi event có map về ít nhất một metric không?** | Đạt | `inventory_batch_added` → activation và chu kỳ tồn kho; `inventory_item_saved` → inventory readiness; `meal_suggestion_requested` → mẫu số NSM; `recipe_suggested` → mẫu số chọn món và counter-metric; `recipe_selected` → leading indicators; `meal_cooked` → activation, NSM, retention và frequency; `ingredient_used` → đo lượng thực phẩm dùng và kiểm tra ngưỡng chất lượng NSM. |
| **Mọi metric đều có event/data để tính không?** | Đạt, cần kiểm chứng dữ liệu | Activation/retention/NSM dùng `meal_cooked`; mẫu số NSM dùng `meal_suggestion_requested`; inventory readiness dùng event batch và item; chỉ số chọn món dùng `recipe_suggested`/`recipe_selected`; lượng dùng trước hạn dùng `ingredient_used`; counter-metric dùng trạng thái hạn sử dụng trong `recipe_suggested`. |

## Lý do điều chỉnh

Bản NSM đầu tiên đếm số món đã nấu trên mỗi chu kỳ đi chợ. Mình đổi thành tỷ lệ phiên yêu cầu gợi ý món dẫn đến món được xác nhận đã nấu đạt ngưỡng chất lượng, vì Phase 2 xác định hành vi tự nhiên là nấu ăn theo từng dịp. Chu kỳ tồn kho vẫn được dùng để đo lượng thực phẩm được tận dụng trước hạn.

## AI Support Log

**AI đã giúp tôi ở đâu?**

AI giúp tôi brainstorm ứng viên core action, đặt câu hỏi phản biện, gợi ý tên event và acceptance criteria, đồng thời đóng vai sinh viên AI20K khó tính để thử thách core job và cadence.

**AI sai, hời hợt hoặc đề xuất metric chưa khớp nature ở đâu?**

Cửa sổ 14 ngày, segment “tự nấu ở nhà ít nhất mỗi tuần” và thời điểm nhắc trước hạn đều là giả định; chưa có phỏng vấn hay dữ liệu sử dụng của sinh viên AI20K để xác nhận. Một món nấu đầu tiên chứng minh first value nhưng chưa chứng minh người dùng sẽ lặp lại hành vi.

**Tôi đã tự sửa hoặc quyết định lại điều gì?**

Tôi giữ core action là nấu món được gợi ý bằng thực phẩm đang có. Tôi căn NSM theo dịp nấu ăn tự nhiên, dùng chu kỳ tồn kho để đo việc tận dụng thực phẩm, và yêu cầu mỗi phiên gợi ý có ngày dự định ăn để xác định rõ món nào được tính. Tôi sẽ xác thực cadence và segment với sinh viên AI20K trước khi chốt cửa sổ 14 ngày.

## Trạng thái nộp bài

**Gate 5: Tạm đạt.** Đã rà đủ 7 câu tự kiểm. Việc còn lại là xác thực tần suất nấu ở nhà, thời điểm nhắc trước hạn và độ tin cậy của xác nhận nấu với sinh viên mục tiêu.
