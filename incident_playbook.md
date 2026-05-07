# incident_playbook.md

**Scenario:**  
9h30 sáng. Customer tweet screenshot: AI của startup phân tích sai 1 clause trong hợp đồng lao động.  
200 retweets trong 30 phút. Có signal viral.

---

## ✅ 0–5 phút — VERIFY

**Câu hỏi:** Đây có thật là AI của mình không?

### Action (cụ thể, không mơ hồ)

1. Mở **Helicone dashboard**
   - URL: https://www.helicone.ai/dashboard

2. Filter:
   - user_id (nếu có)
   - timestamp (±5 phút từ lúc tweet)
   - keyword trong screenshot

3. Check:
   - Full prompt (input contract)
   - Full response (AI output)
   - Confidence score / metadata

4. Compare:
   - Screenshot vs log (check exact wording)
   - Detect fake / edited screenshot

✅ Output cần có trong 5 phút:

- ✅ Confirm: real AI output / fake
- ✅ Identify user_id + conversation

---

## ✅ 5–15 phút — STOP THE BLEEDING

**Decision:** chọn **SOFT KILL** ✅

### Action:

- Disable AI analysis cho new request:

```env
AI_ANALYSIS_ENABLED = false
```

- Switch sang fallback:
  - Show message:
    > “AI analysis temporarily unavailable. Please request human review.”

### Lý do chọn soft kill:

- Không downtime toàn hệ thống
- Giữ service chạy (UX không bị phá hoàn toàn)
- Tránh phát sinh thêm case sai

### KHÔNG chọn:

- Hard kill → quá cực đoan
- Block 1 user → không phải case isolated
- Tighten prompt → chưa verify root cause

✅ Expected result:

- Không có thêm output sai mới
- Limit damage ngay lập tức

---

## ✅ 15–25 phút — CUSTOMER COMM (DM)

**To:** Customer bị ảnh hưởng

---

**Message:**

Tiêu đề: Từ Founder về việc vừa xảy ra

Chào anh/chị,

Đây là mình — founder của sản phẩm. Mình vừa thấy case AI bên mình phân tích sai hợp đồng của anh/chị.

Việc xảy ra:  
AI đã đánh giá sai một điều khoản trong hợp đồng. Đây là lỗi của hệ thống bên mình.

Mình đang làm gì:  
Mình đã tạm tắt tính năng AI analysis và đang kiểm tra log từng case để tìm root cause.

Mình sửa thế nào:  
Bên mình sẽ refund 100% phí sử dụng hôm nay + hỗ trợ review hợp đồng của anh/chị manually (free). Không cần làm form.

Mình sẽ gọi cho anh/chị trong 24h:  
[Founder phone / Calendly link]

— [Tên founder]  
[Email cá nhân founder]

---

✅ Checklist:

- Dùng "I" (không dùng "we")
- Có action cụ thể
- Có compensation cụ thể
- Có contact trực tiếp

---

## ✅ 25–30 phút — PUBLIC RESPONSE

**Tweet (<280 ký tự):**

Hi everyone — I'm the founder. I just saw the issue where our AI gave incorrect contract analysis.  
I've disabled the AI feature while I investigate.  
Reaching out to affected users directly now.  
More update in 24h.

---

✅ Rules:

- Personal voice (founder)
- Không corporate statement
- Có action rõ
- Có next update time

---

## ✅ POST-INCIDENT (sau 24h — không trong crisis loop)

Sau khi contain:

### 1. Root cause

- Prompt bug?
- Model hallucination?
- Missing rule validation?

### 2. Fix

- Add validation layer:
  - Risk classification bắt buộc
  - Confidence threshold
- Add fallback logic nếu low confidence

### 3. Prevent recurrence

- Add test cases (contract edge cases)
- Update RULES / RAILS
- Add vào weekly ritual

---

## 🎯 3 quyết định quan trọng

- ✅ Verify trong 5 phút
- ✅ Soft kill trong 10 phút
- ✅ Founder trực tiếp communicate

---

## ✅ 3-AM TEST

Nếu 3h sáng, founder chỉ cần:

1. Mở Helicone → check log
2. Tắt AI (env var)
3. Gửi DM template
4. Tweet

👉 Không cần suy nghĩ thêm
