# 02 — Action Nature Card + kết luận cadence

## Action đang phân tích

Nấu một món được gợi ý, dùng ít nhất một nguyên liệu đã lưu trong tủ lạnh, rồi xác nhận đã nấu.

| Thành phần | Câu trả lời |
|---|---|
| **Actor** | Một học viên AI20K, cấp người dùng cá nhân |
| **Intent** | Chọn được món khi đi học về mệt, tận dụng thực phẩm sẵn có và ưu tiên đồ sắp hết hạn |
| **Trigger** | Nhu cầu ăn vào một bữa cụ thể; người dùng chủ động xem món có thể nấu. Đồ sắp hết hạn làm tăng lý do dùng sớm. Notification là nurture, không phải nhu cầu tự nhiên. |
| **Effort** | Ghi thực phẩm cần chụp ảnh và nhập/chỉnh lượng cùng hạn dùng; chọn món ít tốn công; nấu món tốn thời gian tùy công thức; xác nhận món và lượng đã dùng cần thao tác ngắn. |
| **Value timing** | Giảm phân vân ngay khi chọn được món; giá trị bữa ăn sau khi nấu; giảm lãng phí tích lũy qua nhiều lần dùng thực phẩm trước hạn. |
| **State** | Danh sách nguyên liệu, lượng còn lại và hạn dùng; công thức đã chọn; lịch sử món đã nấu; lượng nguyên liệu đã dùng. |
| **Dependency** | Độ chính xác tồn kho/hạn dùng; nguyên liệu đủ; thời gian, dụng cụ và kỹ năng nấu; lịch học và thói quen ăn ngoài/ở nhà. |
| **Repeat condition** | Người dùng lại chuẩn bị một bữa ăn, có nguyên liệu trong tủ lạnh và chọn nấu ở nhà. |

## Kết luận cadence

- **Dạng hành vi:** Thói quen thường xuyên, theo dịp nấu ăn; nhu cầu ăn thường xuyên nhưng người dùng không tự nấu mọi bữa.
- **Kết luận:** Đối với **học viên AI20K thường đi học về mệt và có thực phẩm trong tủ lạnh**, core action **nấu một món được gợi ý từ nguyên liệu sẵn có và xác nhận đã nấu** thường xuất hiện **vào những dịp người dùng chọn nấu một bữa ở nhà**, vì **nhu cầu ăn quay lại thường xuyên nhưng thói quen nấu ở nhà khác nhau theo người**. Do đó, nhịp đo phù hợp là **theo dịp nấu ăn tự nhiên của từng người dùng**, ở cấp **sinh viên cá nhân**.
- Dùng bot nhiều hơn không tự động có nghĩa là value cao hơn; một gợi ý tốt có thể giúp quyết định nhanh.
- **Cần xác thực:** Hỏi sinh viên AI20K về tần suất nấu ở nhà; kiểm tra cadence bằng dữ liệu. Nhóm thường nấu và nhóm thường ăn ngoài có thể cần phân tích riêng.
