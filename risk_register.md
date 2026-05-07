# risk_register.md

**Startup:** AI check risk hợp đồng lao động  
**Use case:** Phân tích điều khoản hợp đồng lao động cho người dùng  
**Burn rate (ước tính):** $10,000/tháng

---

## 🔴 RISK 1 — AI Misinterpret Contract Clause

- **Type:** Customer-facing

**If** AI hiểu sai điều khoản quan trọng (ví dụ: non-compete, termination clause)  
**Then** user tin vào output → ký hợp đồng bất lợi → complain + yêu cầu bồi thường  
**Leading to:**

- Refund + support cost (~$5K)
- Legal dispute nhỏ (~$5K)  
  → Tổng ~$10K = **~1 tháng runway**

- **Likelihood (1–5):** 4
  - Legal text mơ hồ
  - User có xu hướng trust AI

- **Impact (1–5):** 2
  - ~1 tháng runway

👉 **Score = 4 × 2 = 8 (Watch / Mitigate)**

---

## 🔴 RISK 2 — Legal Liability Escalation (Lawsuit)

- **Type:** Regulatory

**If** nhiều user bị ảnh hưởng bởi AI advice sai  
**Then** 1 case escalate thành legal claim / lawsuit  
**Leading to:**

- Legal fee + settlement (~$30K–50K)  
  → **~3–5 tháng runway**

- **Likelihood (1–5):** 2
  - Không thường xuyên nhưng có precedent

- **Impact (1–5):** 4
  - 3–6 tháng runway

👉 **Score = 2 × 4 = 8 (Watch / Mitigate)**

---

## 🔴 RISK 3 — Founder Bandwidth Failure

- **Type:** Founder-bandwidth

**If** founder bận/ốm khi AI có critical bug  
**Then** không fix kịp → lỗi lan rộng → mất trust  
**Leading to:**

- 20–30% user churn
- ~$15K loss  
  → **~1.5 tháng runway**

- **Likelihood (1–5):** 3
  - Startup phụ thuộc founder

- **Impact (1–5):** 2
  - 1–2 tháng runway

👉 **Score = 3 × 2 = 6 (Watch / Mitigate)**

---

## 🔥 RISK 4 — Systematic Wrong Advice (KILL ZONE)

- **Type:** Customer-facing

**If** bug trong prompt/system khiến AI phân tích sai hàng loạt hợp đồng  
**Then** 100+ user nhận advice sai  
**Leading to:**

- Refund hàng loạt (~$50K–100K)
- Risk pháp lý  
  → **~5–10 tháng runway (gần hết runway)**

- **Likelihood (1–5):** 3
  - System-wide bug có thể xảy ra

- **Impact (1–5):** 5
  - > 6 tháng runway

👉 **Score = 3 × 5 = 15 → 🔥 KILL ZONE (Mitigate ngay)**

---

## 📊 Summary

| Risk                     | Type       | Likelihood | Impact | Score | Priority     |
| ------------------------ | ---------- | ---------- | ------ | ----- | ------------ |
| AI misinterpret clause   | Customer   | 4          | 2      | 8     | Watch        |
| Legal lawsuit escalation | Regulatory | 2          | 4      | 8     | Watch        |
| Founder bandwidth fail   | Founder    | 3          | 2      | 6     | Watch        |
| Systematic wrong advice  | Customer   | 3          | 5      | 15    | 🔥 KILL ZONE |

---

## 🎯 Key Insight

- Risk lớn nhất không phải PR, mà là:
  - AI advice sai → mất tiền thật
  - System lỗi → mất nhiều user cùng lúc
  - Founder không xử lý kịp → amplify thiệt hại

👉 **Measure risk bằng “tháng runway mất”, không phải $**

---

## ✅ Action Priority

- **Immediate (tuần này):**
  - Fix KILL ZONE (systematic wrong advice)
- **Next:**
  - Reduce hallucination risk
  - Add validation layer
- **Ongoing:**
  - Track incident + founder weekly review
