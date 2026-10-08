# Core Action Card — Ăn Gì Đây?

## Phân biệt bốn khái niệm

| Khái niệm | Câu trả lời |
|---|---|
| **Core job** | “Tôi đi học về mệt và không biết ăn gì. Giúp tôi chọn món từ đồ có sẵn trước khi chúng hết hạn.” |
| **Core action** | Nấu một món được gợi ý từ thực phẩm trong tủ lạnh, rồi xác nhận đã nấu trong app. |
| **Core value** | Chọn được bữa ăn dễ dàng và dùng thực phẩm đã mua trước khi chúng bị bỏ phí. |
| **Core value event** | `meal_cooked` — người dùng xác nhận đã nấu món và ghi nhận nguyên liệu trong tủ lạnh đã dùng. |

## Core Action Card

| Thành phần | Câu trả lời |
|---|---|
| **Target user** | Học viên AI20K đi học về mệt và có thực phẩm trong tủ lạnh |
| **Core job** | Chọn được món dễ nấu từ đồ đang có, đồng thời dùng thực phẩm trước khi hết hạn |
| **Core action** | Nấu một món được gợi ý, có dùng ít nhất một nguyên liệu đã lưu trong tủ lạnh, rồi xác nhận đã nấu |
| **Object** | Công thức món ăn và các nguyên liệu trong tủ lạnh |
| **Preconditions** | Có nguyên liệu trong tủ lạnh với lượng tương đối chính xác; công thức phù hợp với nguyên liệu và khả năng nấu của người dùng |
| **Completion rule** | Người dùng xác nhận đã nấu món; app ghi nhận món và nguyên liệu đã dùng |
| **Core value** | Người dùng giải quyết được câu hỏi “hôm nay ăn gì” và tận dụng thực phẩm đang có |
| **Evidence of value** | Món được xác nhận đã nấu; có ít nhất một nguyên liệu trong tủ lạnh được ghi nhận đã dùng |
| **Candidate event** | `meal_cooked` với `user_id`, `recipe_id`, `inventory_item_ids`, `cooked_at`, `quantity_used` |

## Tự kiểm 5 tiêu chí

- **Gần core value:** Có — nấu được món từ nguyên liệu sẵn có.
- **Có thể lặp lại:** Có — nhu cầu chọn và nấu bữa ăn quay lại theo lịch sinh hoạt.
- **Có thể quan sát:** Có — người dùng xác nhận đã nấu và ghi nguyên liệu đã dùng.
- **Có ý nghĩa:** Có — nhiều món được nấu từ đồ sẵn có cho thấy sản phẩm đang giải quyết đúng nhu cầu; vẫn cần theo dõi chất lượng gợi ý và lượng thức ăn bỏ đi.
- **Có thể tác động:** Có — sản phẩm có thể cải thiện nhận diện nguyên liệu, độ chính xác của công thức và cách ưu tiên đồ sắp hết hạn.

**Kết quả: 5/5 — qua Gate 1.** Đây không phải “hỏi bot” hay “xem công thức”; event chỉ ghi nhận khi người dùng cho biết họ đã nấu món. Vì event dựa trên xác nhận của người dùng, nó là bằng chứng tự báo cáo, chưa phải xác minh độc lập.
