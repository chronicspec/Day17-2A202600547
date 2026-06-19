# Lab Day 2 — Test Hypothesis Rẻ Hơn

**Dự án:** Arionear  
**Nhóm:**   
**Ngày:** 18/06/2026

---

## Bước 1 — Chọn 1 hypothesis quan trọng

### Hypothesis đã chọn (H1)

> **Khi sửa paper bằng AI, sinh viên / nghiên cứu sinh sợ ChatGPT làm đổi số liệu hoặc ý chính — họ muốn nhìn thấy AI sửa chỗ nào (diff đỏ/xanh) trước khi chấp nhận.**

Viết ngắn hơn nữa:

> **User sợ AI sửa paper "làm bậy" → cần diff để tin.**

### Vì sao chọn cái này?

- Dễ hiểu, ai cũng hình dung được (đã từng copy-paste ChatGPT sửa paper)

---

## Bước 2 — Cách team đã / đang định test

### Team định làm thế nào?

```
Làm xong web/app → đưa cho user thật dùng vài tuần
    → đếm bao nhiêu lần bấm Accept vs Reject
    → phỏng vấn 5 người
    → mới biết user có tin diff không
```

### Vì sao gọi là "đắt"?


|           |                                                        |
| --------- | ------------------------------------------------------ |
| Thời gian | 2–4 tuần                                               |
| Cần gì    | User thật, server chạy ổn, bảng thống kê Accept/Reject |
| Rủi ro    | Build xong mới hỏi — nếu sai thì mất nhiều công sức    |


---

## Bước 3 — 3 cách **rẻ hơn** để test cùng H1

### Cách 1 — Hỏi + so sánh ảnh (nhanh nhất)

Cho 5 người xem **cùng 1 đoạn paper**:

- **Bên trái:** output ChatGPT (đoạn văn mới, không thấy sửa gì)
- **Bên phải:** diff Arionear (đỏ = cũ, xanh = mới)

Hỏi 3 câu trên Google Form:

1. Bạn tin bên nào hơn? (ChatGPT / Arionear diff)
2. Bạn sẽ dùng bên nào vào paper? (ChatGPT / Arionear / Tự sửa tay)
3. Bạn lo gì nhất khi AI sửa paper?


|             |                                          |
| ----------- | ---------------------------------------- |
| Thời gian   | 15 phút/người · chuẩn bị 30 phút         |
| Cần deploy? | **Không** — chỉ cần 1 slide 2 ảnh + Form |


---

### Cách 2 — Nhờ sửa hộ (Concierge)

Nhắn 3 bạn trong lớp:

> "Gửi mình 1 đoạn tiếng Anh trong paper bạn đang viết (3–5 câu). Mình sửa bằng Arionear, trả lại ảnh diff — bạn chọn **Đồng ý** hay **Không**."

Team chạy Quick Edit trên máy local → chụp màn hình diff → gửi lại.


|             |                              |
| ----------- | ---------------------------- |
| Thời gian   | 10 phút/bạn                  |
| Cần deploy? | **Không** — chạy local là đủ |


Ghi lại: Accept hay Reject? Vì sao?

---

### Cách 3 — Ngồi xem 1 bạn dùng thử (Think-aloud)

Mời 1 bạn ngồi cạnh, mở Arionear, bôi đen 1 đoạn → bấm Quick Edit → **quan sát** bạn đó đọc diff và quyết định Accept/Reject.

Sau đó hỏi 2 câu:

1. "Diff có giúp bạn yên tâm hơn dán ChatGPT không?"
2. "Điều gì khiến bạn không bấm Accept?"


|             |           |
| ----------- | --------- |
| Thời gian   | 20 phút   |
| Cần deploy? | **Không** |


---

### Tóm tắt 3 cách


| Cách            | Làm gì               | Mất bao lâu   | Cần deploy? |
| --------------- | -------------------- | ------------- | ----------- |
| 1. Hỏi + so ảnh | Form + slide 2 cột   | ~1 giờ cả lớp | Không       |
| 2. Sửa hộ       | Nhận đoạn → trả diff | ~30 phút      | Không       |
| 3. Ngồi xem     | 1 bạn dùng live      | 20 phút       | Không       |


---

## Bước 4 — Prototype nhanh 3 cách đó

**Mở prototype:** `[prototype/index.html](prototype/index.html)` — 3 file HTML tương tác, không cần deploy.

### Cách 1 — Chuẩn bị 30 phút

**Prototype:** `[prototype/cach1-hoi-so-anh.html](prototype/cach1-hoi-so-anh.html)` — slide so sánh + Form 3 câu + bảng kết quả.

**Đoạn văn mẫu** (cố ý viết lủng củng):

```text
Gốc:
"The result show that our model is better. The accuracy is higher about 15%."

ChatGPT (copy-paste thẳng — không thấy sửa gì):
"The results demonstrate that our model performs better, with approximately 
15% higher accuracy."

Arionear (diff đỏ/xanh — thấy rõ sửa gì):
- đỏ: "The result show..."
- xanh: "The results demonstrate..."
```

**Google Form — 3 câu:**

1. Bạn tin output nào hơn? → ChatGPT / Arionear diff / Không tin cả hai
2. Bạn sẽ dán vào paper output nào? → ChatGPT / Arionear / Tự sửa
3. Bạn lo gì khi AI sửa paper? → (tự điền)

**Trong buổi lab:** Chiếu slide → 5 người điền Form → đếm kết quả 10 phút.

---

### Cách 2 — Prototype Concierge

**Prototype:** `[prototype/cach2-sua-ho.html](prototype/cach2-sua-ho.html)` — copy tin nhắn · nhận đoạn · mock Quick Edit · Accept/Reject.

---

### Cách 3 — Prototype Think-aloud

**Prototype:** `[prototype/cach3-ngoi-xem.html](prototype/cach3-ngoi-xem.html)` — mock editor · Quick Edit · checklist quan sát · 2 câu hỏi sau buổi.

---

### Cách 1 — Kết quả Form (5 người cùng bàn)


| Bạn        | Tin hơn?         | Sẽ dùng vào paper?      | Lo gì nhất khi AI sửa paper?                    |
| ---------- | ---------------- | ----------------------- | ----------------------------------------------- |
| Văn Dương  | Arionear diff    | Arionear                | "ChatGPT đổi số liệu mà mình không biết"        |
| Thái Dương | Arionear diff    | Tự sửa (tham khảo diff) | "Không thấy AI sửa chỗ nào thì không dám paste" |
| Minh Anh   | Không tin cả hai | Tự sửa                  | "Cả hai đều có thể paraphrase làm lệch ý"       |
| Lan        | Arionear diff    | Arionear                | "Sợ AI thêm claim mới"                          |
| Tài        | Arionear diff    | Arionear                | "Copy ChatGPT xong mới đọc lại — muộn"          |


**Tổng Cách 1:** **4/5** tin diff hơn · **3/5** sẽ dùng Arionear vào paper

---

### Cách 2 — Kết quả sửa hộ (3 bạn)

Tin nhắn đã gửi:

> Gửi mình 1 đoạn tiếng Anh trong paper bạn đang viết (3–5 câu). Mình sửa bằng Arionear, trả lại ảnh diff — bạn chọn **Đồng ý** hay **Không**.


| Bạn       | Đoạn gửi                             | Accept?  | Lý do                                                                      |
| --------- | ------------------------------------ | -------- | -------------------------------------------------------------------------- |
| Minh Anh  | Đoạn Discussion — kết quả thí nghiệm | ✅ Accept | "Thấy rõ chỗ sửa, số 15% vẫn giữ nguyên — yên tâm hơn ChatGPT"             |
| Văn Dương | Abstract viết vội                    | ✅ Accept | "Văn phong học thuật hơn, diff cho biết AI không đổi ý chính"              |
| Lan       | Introduction đoạn 2                  | ❌ Reject | "Diff sửa quá nhiều chỗ nhỏ — muốn tự chọn từng câu, không Accept cả khối" |


**Tổng Cách 2:** **2/3** Accept

---

### Cách 3 — Kết quả ngồi xem (Thái Dương)


| Quan sát               | Ghi chú                                                                                                            |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Có đọc phần đỏ/xanh?   | ✅ Có — đọc kỹ phần xanh trước, quay lại đỏ để so                                                                   |
| Bấm Accept hay Reject? | ✅ Accept sau ~45 giây                                                                                              |
| Nói gì về ChatGPT?     | *"ChatGPT paste xong mới hoảng — diff này thấy trước nên yên tâm hơn. Nhưng vẫn đọc lại 1 lần vì không tin 100%."* |


**Tổng Cách 3:** **1/1** tin diff hơn · **1/1** Accept

---

### Tổng hợp 3 cách


| Cách            | Số người | Tin diff hơn ChatGPT | Accept diff |
| --------------- | -------- | -------------------- | ----------- |
| 1. Hỏi + so ảnh | 5        | **4/5**              | **3/5**     |
| 2. Sửa hộ       | 3        | —                    | **2/3**     |
| 3. Ngồi xem     | 1        | **1/1**              | **1/1**     |


**Pattern lặp lại:**

1. **Lo #1:** AI đổi số liệu / claim mà user không biết (4/5 người nhắc)
2. **Diff giúp:** thấy trước khi apply → yên tâm hơn ChatGPT (4/5 + 2/3 Accept)
3. **Ngoại lệ:** Minh Anh không tin cả hai — cần đọc lại tay; Lan Reject vì muốn control từng câu

**Kết luận:**

- **Đúng** — đa số tin diff hơn ChatGPT; fear "AI làm bậy" là thật → tiếp tục build Arionear với diff + human gate
- **Sai**
- **Chưa rõ**

**Điều cần sửa sau test:** Cho phép Accept **từng câu** trong diff (Lan Reject vì không muốn apply cả khối) — không phải sửa hypothesis, mà sửa UX.

---

## Bước 5 — Present nhóm (~90 giây)

### Nói gì?

**1. Hypothesis (20s)**  

> "Chúng tôi giả định: sinh viên sửa paper **sợ ChatGPT đổi số liệu/ý chính**. Họ cần **nhìn thấy AI sửa chỗ nào** (diff đỏ/xanh) mới tin."

**2. Cách đắt (15s)**  

> "Cách cũ: đợi user dùng app vài tuần, đếm Accept/Reject — mất 2–4 tuần."

**3. 3 cách rẻ (30s)**  

> "Hôm nay test rẻ: (1) cho xem ảnh ChatGPT vs diff + Form 3 câu; (2) nhờ sửa hộ 3 đoạn, hỏi Accept không; (3) ngồi xem 1 bạn dùng live. Không cần deploy."

**4. Kết quả (15s)**  

> "4/5 tin diff hơn ChatGPT. 2/3 Accept khi sửa hộ. Người được xem live nói: *'diff thấy trước nên yên tâm hơn paste ChatGPT.'* Lo chung nhất: AI đổi số liệu mà không biết."

**5. Bước tiếp (10s)**  

> "Giữ hướng diff + guardrail. Bước tiếp: thêm Accept từng câu (1 bạn Reject vì không muốn apply cả khối), rồi mới đo analytics production."

### Slide 1 trang

```
┌──────────────────────────────────────────────┐
│  H1: User sợ AI sửa paper "làm bậy"          │
│      → Cần diff đỏ/xanh để tin?              │
├──────────────────────────────────────────────┤
│  Đắt:  Đợi user dùng app vài tuần            │
│  Rẻ:   ① So ảnh + Form  ② Sửa hộ  ③ Xem live │
├──────────────────────────────────────────────┤
│  Kết quả: 4/5 tin diff · 2/3 Accept          │
│  [x] Đúng  [ ] Sai  [ ] Chưa rõ             │
│  Next: Accept từng câu trong diff            │
└──────────────────────────────────────────────┘
```

---

## Ghi nhớ

**Hypothesis đơn giản = dễ test rẻ.**

Không cần đợi app hoàn hảo mới hỏi user — hỏi bằng ảnh diff + Form cũng đủ để biết hướng đi đúng hay sai.