# rules_rails_ritual.md

**Startup:** AI kiểm tra rủi ro hợp đồng lao động  
**Risk chọn:** AI phân tích sai hợp đồng → user ký bất lợi → complain / kiện

---

## 🔴 R1 — RULES

### ❌ KHÔNG được làm

- KHÔNG deploy AI phân tích hợp đồng mà **không có disclaimer rõ ràng (not legal advice)**
- KHÔNG trả output contract analysis mà **không có risk level (LOW/MEDIUM/HIGH) và confidence score**
- KHÔNG xử lý hợp đồng có dữ liệu cá nhân qua **ChatGPT public / Claude public**

---

### ✅ Allowed alternative

- DÙNG **OpenAI Enterprise API** (data không train)  
  → Cost: ~$25–40/user/tháng

- DÙNG **internal prompt template + validation rules**  
  → Cost: $0

- DÙNG **rule-based fallback system** (FAQ / manual review)  
  → Cost: $0

---

### ⚠️ Hậu quả vi phạm

- Lần 1: Founder review case trực tiếp + fix system
- Lần 2: Remove quyền deploy / let go

---

### 🔄 Update mechanism

- Update tại Notion:  
  https://notion.so/ai-safety-contract-risk

---

## 🔵 R2 — RAILS

👉 Mục tiêu: chặn AI output sai + có audit log

---

### Tool 1 — Helicone (LLM logging)

- Use: log toàn bộ prompt + response
- Cost: $0–50/tháng
- Value:
  - Verify nhanh khi có incident
  - Audit toàn bộ AI output

---

### Tool 2 — Validation Layer (Guardrails.ai / custom rule)

- Use: bắt buộc AI output phải có:
  - Risk level (LOW / MEDIUM / HIGH)
  - Explanation rõ ràng
  - Disclaimer: “This is not legal advice”
- Cost: ~$0–30/tháng

---

### Tổng cost

👉 ~$50–80/tháng ✅ (< $500 requirement)

---

## 🟢 R3 — RITUAL

### Ritual: Weekly Contract Risk Audit (30 phút)

---

### Action (mỗi tuần)

- Founder review:
  - 5 contract AI đã phân tích
  - 1 case sai / edge case

---

### Founder hỏi team:

> “Có case nào AI nói ‘safe’ nhưng thực tế có risk không? Vì sao AI miss?”

---

### Expected output

- 1–2 failure pattern mới
- Update prompt / validation rule ngay trong tuần

---

## ✅ Self-check

- ✅ RAILS < $500/tháng
- ✅ implement trong 1 tuần
- ✅ RULES cụ thể (vendor + action)
- ✅ RITUAL có question rõ

---

## 🎯 Key takeaway

- AI trong legal = high-risk
- Sai 1 case nhỏ → có thể thành lawsuit
- Phải:
  - Rule rõ
  - Check tự động (rails)
  - Founder liên tục audit (ritual)

👉 **Rules = giấy, Rails = code, Ritual = behavior**
