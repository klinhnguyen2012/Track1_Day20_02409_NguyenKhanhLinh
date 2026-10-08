# 03 — Metric System

> **Giả thuyết:** Chưa có dữ liệu về cadence của sinh viên AI20K. Cửa sổ 14 ngày và segment “nấu ở nhà ít nhất mỗi tuần” bên dưới là giả định ban đầu cần xác thực.

## Activation

- **Start event — `inventory_batch_added`:** Người dùng hoàn tất lưu một đợt thực phẩm sau khi xác nhận tên, lượng và hạn dùng.
- **First-value event — `meal_cooked`:** Người dùng xác nhận đã nấu món được gợi ý; món dùng ít nhất một nguyên liệu còn hạn có trong tồn kho lúc gợi ý.
- **Time window:** Trong **14 ngày** từ đợt thực phẩm đầu tiên. Đây là giả thuyết onboarding cho người nấu ở nhà không thường xuyên; cần xác thực với sinh viên.
- **Activation rate:** Số sinh viên có `meal_cooked` đạt điều kiện trong 14 ngày ÷ số sinh viên có `inventory_batch_added` đầu tiên.
- **Active ≠ activated:** Active là có ít nhất một `meal_cooked` trong cửa sổ báo cáo. First-value activation là lần đầu có món nấu đạt điều kiện. Tín hiệu lặp lại riêng: ít nhất hai `meal_cooked` ở hai ngày khác nhau trong cửa sổ 14 ngày giả thuyết; kiểm tra xem điều này có dự báo retention không.

## Engagement — hai góc đo

1. **Frequency:** Số món nấu đạt điều kiện trên mỗi sinh viên qua các dịp nấu ở nhà; xem số món trong cửa sổ quan sát 14 ngày và tỷ lệ phiên yêu cầu gợi ý chuyển thành món nấu.
2. **Depth / food use:** Số gram nguyên liệu được ghi nhận đã dùng vào hoặc trước hạn trên mỗi chu kỳ tồn kho. Chỉ số phụ thuộc vào lượng nhập và lượng dùng do người dùng ghi nhận.

## North Star Metric

**Tỷ lệ phiên yêu cầu gợi ý món dẫn đến một món được xác nhận đã nấu đạt ngưỡng chất lượng.**

- **Unit of value:** Một bữa ăn người dùng thực sự nấu.
- **Quality threshold:** Người dùng xác nhận đã nấu; món dùng ít nhất một nguyên liệu có trong tồn kho lúc gợi ý; không dùng nguyên liệu nào đã quá hạn tại thời điểm nấu.
- **Frequency:** Theo mỗi dịp nấu ăn tự nhiên có sản phẩm hỗ trợ; tối đa một món đạt điều kiện cho mỗi `meal_session_id`.
- **Công thức:** Số `meal_session_id` có `meal_cooked` đạt điều kiện ÷ số phiên `meal_suggestion_requested` hợp lệ. Yêu cầu phải có ngày dự định ăn; chỉ tính món được xác nhận trước khi hết ngày địa phương đó.

Gram thực phẩm dùng trước hạn là metric bổ trợ; NSM không nên thưởng cho việc dùng lượng lớn bất kể chất lượng bữa ăn.

## Leading indicators

1. **Inventory readiness rate:** Mặt hàng có tên, lượng, hạn dùng đã xác nhận ÷ số mặt hàng nhận diện trong đợt đi chợ. Tồn kho đáng tin cậy hơn giúp tạo công thức khả thi.
2. **Feasible recipe selection rate:** Gợi ý được chọn mà nguyên liệu yêu cầu đang có ÷ tổng gợi ý đã hiển thị. Việc chọn món có thể báo trước hành vi nấu nhưng chưa chứng minh món đã nấu.
3. **Expiring-item recipe selection rate:** Khi có nguyên liệu còn dùng được trong cửa sổ nhắc trước hạn, tỷ lệ món được chọn có dùng nguyên liệu đó. Có thể dự báo thực phẩm được dùng trước hạn.

## Counter-metric

- **Expired-item suggestion rate:** Tỷ lệ công thức gợi ý có nguyên liệu đã quá hạn tại thời điểm gợi ý. Mục tiêu: **0%**.
