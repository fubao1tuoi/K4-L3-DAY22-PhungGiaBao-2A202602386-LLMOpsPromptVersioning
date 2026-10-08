# Phân tích kết quả RAGAS — Prompt V1 và V2

| Metric | V1 | V2 | Nhận xét |
|---|---:|---:|---|
| Faithfulness | 0.9595 | 0.9323 | V1 cao hơn 0.0272 |
| Answer relevancy | 0.9272 | 0.8915 | V1 cao hơn 0.0357 |
| Context recall | 1.0000 | 1.0000 | Hai phiên bản bằng nhau |
| Context precision | 0.9450 | 0.9450 | Hai phiên bản gần như bằng nhau |

V1 đạt faithfulness và answer relevancy cao hơn V2 vì prompt yêu cầu trả lời trực tiếp, ngắn gọn trong 2–4 câu và chỉ sử dụng thông tin có trong context. Ràng buộc này làm giảm số nhận định phụ không được context hỗ trợ, đồng thời giúp câu trả lời tập trung hơn vào đúng câu hỏi.

V2 yêu cầu câu trả lời dài hơn, có phân tích, bằng chứng hoặc cơ chế giải thích trong 3–5 câu. Cách diễn đạt này có thể cung cấp nhiều chi tiết hơn, nhưng cũng tạo thêm cơ hội để mô hình diễn giải vượt quá nội dung được truy xuất hoặc thêm thông tin ít liên quan trực tiếp; vì vậy faithfulness và answer relevancy thấp hơn V1 một chút.

Context recall của hai phiên bản đều đạt 1.0 và context precision đều xấp xỉ 0.945 vì cả V1 và V2 dùng chung knowledge base, embedding model, chunking và retriever `k=3`. Hai metric này chủ yếu đánh giá chất lượng truy xuất nên gần như không bị ảnh hưởng bởi cách viết system prompt. Chênh lệch rất nhỏ ở các chữ số cuối của context precision chỉ là sai số tính toán số thực, không phải khác biệt có ý nghĩa.

Cả hai phiên bản đều vượt mục tiêu faithfulness ≥ 0.8 và đồng thời vượt mức 0.9, trong đó V1 phù hợp hơn khi ưu tiên câu trả lời chính xác, ngắn gọn và bám sát nguồn.
