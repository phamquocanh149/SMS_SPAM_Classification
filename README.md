# 📱 SMS Spam Classification

Dự án này thực hiện phân loại tin nhắn SMS thành **SPAM** hoặc **HAM** bằng hai kỹ thuật khác nhau:

---

## 🔹 1. TF-IDF + Logistic Regression
- Sử dụng **Tf-idfVectorizer** để biến đổi tin nhắn thành vector đặc trưng.  
- Huấn luyện bằng **Logistic Regression**.  
- ✅ Kết quả:  
  - Độ chính xác (**Accuracy**) đạt tới **0.98**.  
  - Mô hình phân loại SPAM tốt, bắt đúng hầu hết các tin nhắn rác.  

---

## 🔹 2. RNN (Recurrent Neural Network)
- Sử dụng **Embedding + RNN** để học biểu diễn từ và ngữ cảnh.  
- Huấn luyện trên cùng tập dữ liệu.  
- ⚠️ Kết quả:  
  - Độ chính xác (**Accuracy**) chỉ khoảng **0.88**.  
  - Mô hình **hầu như dự đoán sai toàn bộ các tin nhắn SPAM**, chỉ nhận diện HAM tốt.  

---

## 📊 So sánh nhanh
| Phương pháp              | Accuracy | Hiệu quả nhận diện SPAM |
|---------------------------|----------|--------------------------|
| TF-IDF + Logistic Reg.   | 0.98     | Rất tốt ✅               |
| RNN                      | 0.88     | Rất kém ❌               |

---

## 📌 Kết luận
- Với dữ liệu SMS spam nhỏ gọn, **TF-IDF + Logistic Regression** tỏ ra **hiệu quả vượt trội** so với RNN.  
- RNN cần nhiều dữ liệu hơn và tinh chỉnh tốt hơn để đạt kết quả khả quan.  
