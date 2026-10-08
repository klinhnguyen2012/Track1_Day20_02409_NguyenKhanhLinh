# 06 — Tracking nhanh

| Tên event | Ý nghĩa | Thời điểm ghi nhận | Metric sử dụng |
|---|---|---|---|
| `inventory_batch_added` | Người dùng hoàn tất lưu một đợt thực phẩm sau khi đi chợ | Sau khi mặt hàng được xác nhận và lưu; gửi `user_id`, `batch_id`, `detected_item_count`, `occurred_at` | Start event activation; activation rate; chu kỳ tồn kho; mẫu số readiness |
| `inventory_item_saved` | Mặt hàng có tên, lượng, hạn dùng đã được người dùng xác nhận | Khi bản ghi hoàn chỉnh được lưu lần đầu; gửi `item_id`, `batch_id`, `quantity`, `expiry_at` | Tử số readiness; dữ liệu tồn kho |
| `meal_suggestion_requested` | Người dùng yêu cầu gợi ý cho một dịp ăn/nấu cụ thể | Khi yêu cầu hợp lệ được gửi; tạo `meal_session_id`; gửi `meal_for_date`, timezone | Mẫu số NSM |
| `recipe_suggested` | Công thức đã được tạo và hiển thị thành công | Sau khi danh sách hiển thị; gửi `meal_session_id`, `recipe_id`, `ingredient_ids`, trạng thái hạn dùng tại lúc gợi ý | Mẫu số chỉ số chọn món; counter-metric quá hạn |
| `recipe_selected` | Người dùng chọn một gợi ý để nấu | Khi lựa chọn được lưu; gửi `meal_session_id`, `recipe_id`, nguyên liệu đang có | Leading indicators chọn món khả thi/sắp hết hạn |
| `meal_cooked` | Người dùng xác nhận đã nấu công thức gợi ý, có dùng nguyên liệu từ tồn kho | Sau xác nhận nấu thành công; không bắn khi chỉ xem/chọn; gửi `user_id`, `recipe_id`, `meal_session_id`, `inventory_item_ids`, `cooked_at`, `meal_for_date` | Activation; repeat-activation signal; NSM; retention; frequency |
| `ingredient_used` | Lượng cụ thể của nguyên liệu tồn kho đã được dùng trong món | Khi người dùng xác nhận lượng dùng và tồn kho được cập nhật; mỗi nguyên liệu một event; gửi `item_id`, `meal_id`, `quantity_used`, `used_at`, `expiry_at` | Depth/food-use; kiểm tra ngưỡng chất lượng NSM |

## Acceptance criteria

1. Event chỉ ghi sau khi trạng thái tương ứng lưu thành công. `meal_cooked` không bắn khi người dùng chỉ mở, xem hoặc chọn công thức; `ingredient_used` không bắn nếu cập nhật tồn kho thất bại.
2. Reload/retry không ghi trùng: mỗi event có `event_id` hoặc khóa idempotency ổn định; cùng `meal_id` chỉ tạo một `meal_cooked`.
3. Sửa gram/hạn dùng trên cùng `item_id` cập nhật bản ghi, không tạo mặt hàng mới hay ghi lại `inventory_item_saved`.
4. `recipe_suggested` lưu trạng thái hạn dùng tại đúng thời điểm gợi ý để counter-metric không đổi theo chỉnh sửa sau đó.
