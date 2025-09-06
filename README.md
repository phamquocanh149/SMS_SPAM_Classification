
# 📱 SMS Spam Classification

## 📌 Giới thiệu
Trong thời đại điện thoại di động và Internet phát triển mạnh mẽ, **tin nhắn rác (SMS Spam)** trở thành một vấn đề phổ biến.  
- Người dùng thường xuyên nhận những tin nhắn quảng cáo, lừa đảo hoặc chứa nội dung không mong muốn.  
- Những tin nhắn này gây **phiền toái**, thậm chí có thể **đe dọa đến an toàn thông tin cá nhân**.  

👉 Vì vậy, việc xây dựng hệ thống **phân loại SMS** để **tự động phát hiện và loại bỏ spam** là một bài toán quan trọng trong lĩnh vực **Xử lý ngôn ngữ tự nhiên (NLP)** và **An ninh mạng**.  

Mục tiêu của dự án này là:  
- Xây dựng mô hình **phân loại SMS thành HAM (hợp lệ) và SPAM (rác)**.  
- So sánh hiệu quả giữa các phương pháp từ **truyền thống (BoW, TF-IDF + ML)** đến **mạng nơ-ron (RNN)**.  
- Đánh giá xem mô hình nào phù hợp hơn với **tập dữ liệu nhỏ và mất cân bằng** như SMS spam.

---

## 🔹 1. Bag of Words (BoW) + Logistic Regression / Random Forest
- Biến đổi tin nhắn thành vector đặc trưng bằng **CountVectorizer (BoW)**.  
- Huấn luyện với **Logistic Regression** và **Random Forest**.  
- ✅ Kết quả:  
  - Logistic Regression: **Accuracy = 0.98**, Precision (SPAM) = **0.99**  
  - Random Forest: **Accuracy = 0.97**, Precision (SPAM) = **1.00**  
- → Cả hai mô hình đều có khả năng **sàng lọc spam rất tốt**, đặc biệt là precision cao, cho thấy mô hình gần như không bỏ sót tin nhắn spam.

---

## 🔹 2. TF-IDF + Logistic Regression
- Sử dụng **Tf-idfVectorizer** để biểu diễn văn bản.  
- Huấn luyện với **Logistic Regression**.  
- ✅ Kết quả:  
  - **Accuracy = 0.98**  
  - Mô hình phân loại SPAM tốt, bắt đúng hầu hết tin nhắn rác.  

---

## 🔹 3. RNN (Recurrent Neural Network)
- Sử dụng **Embedding + RNN** để học ngữ cảnh.  
- Ban đầu chọn `max_len` lớn → mô hình học quá nhiều **padding**, dẫn đến kết quả không tốt.  
- Sau khi điều chỉnh `max_len = 20` (dựa theo phân bố độ dài câu), kết quả cải thiện:  
  - **Accuracy ≈ 0.82**  
  - Tuy nhiên, **Precision (SPAM) = 0.39**, cho thấy khả năng nhận diện spam còn kém.  
- ⚠️ Lý do: dữ liệu bị **chênh lệch giữa số lượng HAM và SPAM**, dẫn đến mô hình **thiên về HAM**.  
- Giải pháp cải thiện: áp dụng **sampling (oversampling/undersampling)** hoặc **class weight balancing** để giảm mất cân bằng dữ liệu.

---

## 📊 So sánh nhanh
| Phương pháp              | Accuracy       | Precision (SPAM) | Hiệu quả nhận diện SPAM |
|---------------------------|----------------|------------------|--------------------------|
| BoW + (LR / RF)          | 0.97 – 0.98    | 0.99 – 1.00      | Rất tốt ✅               |
| TF-IDF + Logistic Reg.   | 0.98           | ~0.98            | Rất tốt ✅               |
| RNN                      | 0.82           | 0.39             | Rất kém ❌               |

---

## 📌 Kết luận
- Với dữ liệu SMS nhỏ gọn và mất cân bằng, **BoW/TF-IDF + Logistic Regression hoặc Random Forest** cho thấy **hiệu quả vượt trội**, đặc biệt là ở **precision SPAM rất cao** → mô hình lọc spam cực kỳ đáng tin cậy.  
- RNN cần nhiều dữ liệu hơn và kỹ thuật xử lý mất cân bằng để đạt kết quả tốt hơn.  



