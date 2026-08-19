# Reflection — Lab 19

**Tên:** _Nguyen Duc Tin_
**Cohort:** _3_
**Path đã chạy:** _lite_

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên golden set, BM25 thường mạnh nhất ở `exact` vì các từ kỹ thuật xuất hiện
nguyên văn trong corpus. Vector mạnh hơn ở `paraphrase` vì không cần khớp từ
chính xác, còn `mixed` là trường hợp hybrid/RRF phù hợp nhất: nó giữ được tín
hiệu từ khoá và bổ sung các kết quả tương đồng về ngữ nghĩa. Vì vậy hybrid là
lựa chọn mặc định khi truy vấn thực tế có cả thuật ngữ chính xác lẫn diễn đạt
tự nhiên. Mình không dùng hybrid cho truy vấn exact rất đơn giản khi BM25 đã đủ
nhanh và chính xác, hoặc khi chỉ cần tìm theo ý nghĩa trong corpus đa ngôn ngữ
và embedding model đã được kiểm chứng tốt. Hybrid cũng không đáng chi phí nếu
ngân sách latency cực thấp và một retriever đơn đã đạt chất lượng yêu cầu.

---

## Điều ngạc nhiên nhất khi làm lab này

Điểm đáng chú ý là chất lượng semantic phụ thuộc mạnh vào model embedding:
`bge-small-en` chạy nhẹ nhưng không lý tưởng cho paraphrase tiếng Việt.

---

