# 04 — Retention Definition

| Thành phần | Định nghĩa |
|---|---|
| **Unit** | Một sinh viên (`user_id`) |
| **Cohort entry** | Lần đầu có `meal_cooked` đạt ngưỡng chất lượng (first-value activation) |
| **Return event** | Một `meal_cooked` ở dịp nấu khác, dùng ít nhất một nguyên liệu có trong tồn kho lúc gợi ý |
| **Window** | 14 ngày sau cohort entry; cửa sổ tùy chỉnh tạm thời, cần đối chiếu với khoảng cách giữa các dịp nấu tự nhiên. Không gọi đây là D7. |
| **Threshold** | Ít nhất một return event trong window |
| **Segment** | Học viên AI20K tự nấu ở nhà ít nhất mỗi tuần và có tồn kho tủ lạnh dùng được. Theo dõi riêng nhóm nấu ít hơn; xác thực cách chia segment với người dùng. |

## Ba mốc so sánh

1. **Chu kỳ tự nhiên:** So với khoảng cách thực tế giữa các dịp nấu ở nhà; nếu 14 ngày không khớp thì điều chỉnh window.
2. **Cohort/segment phù hợp:** So giữa các cohort có tần suất nấu và tình trạng tồn kho tương đồng; không gộp người thường nấu với người chủ yếu ăn ngoài.
3. **Benchmark ngành:** So với sản phẩm quản lý thực phẩm/lập kế hoạch bữa ăn tương đồng nếu có dữ liệu; chưa giả định con số benchmark.
