# Nội Dung Slide Trình Bày

## Project: Phân Tích Cảm Xúc Văn Bản Tiếng Việt - UIT-VSFC Dataset

---

## Slide 1: Trang Bìa

**PHÂN TÍCH CẢM XÚC VĂN BẢN TIẾNG VIỆT**

_Vietnamese Sentiment Analysis using UIT-VSFC Dataset_

- Môn học: [Tên môn học]
- Giảng viên hướng dẫn: [Tên giảng viên]
- Học viên thực hiện: [Tên học viên]
- Ngày trình bày: [Ngày/Tháng/Năm]

---

## Slide 2: Mục Lục

1. Giới thiệu bài toán
2. Mô tả Dataset
3. Tiền xử lý dữ liệu (Preprocessing)
4. Phân tích khám phá dữ liệu (EDA)
5. Phương pháp biểu diễn văn bản
6. Mô hình Machine Learning
7. Kết quả thực nghiệm
8. Kết luận và hướng phát triển

---

## Slide 3: Giới Thiệu Bài Toán

### Sentiment Analysis là gì?

- Là bài toán **phân loại văn bản** dựa trên cảm xúc/thái độ
- Thuộc lĩnh vực **Xử lý Ngôn ngữ Tự nhiên (NLP)**

### Ứng dụng thực tế

- Phân tích phản hồi sinh viên về giảng viên
- Đánh giá sản phẩm/dịch vụ
- Theo dõi thương hiệu trên mạng xã hội

### Mục tiêu dự án

- Phân loại văn bản thành **2 lớp**:
  - ✅ **Positive** (Tích cực)
  - ❌ **Negative** (Tiêu cực)

---

## Slide 4: Mô Tả Dataset UIT-VSFC

### Thông tin chung

| Thuộc tính  | Giá trị                                         |
| ----------- | ----------------------------------------------- |
| Tên Dataset | UIT-VSFC (Vietnamese Students' Feedback Corpus) |
| Nguồn       | Trường ĐH CNTT - ĐHQG TP.HCM                    |
| Chủ đề      | Feedback về giảng viên (lecturer)               |
| Ngôn ngữ    | Tiếng Việt                                      |

### Phân chia dữ liệu

| Tập dữ liệu      | Số lượng mẫu |
| ---------------- | ------------ |
| Train            | 7,980        |
| Dev (Validation) | 1,119        |
| Test             | 2,216        |
| **Tổng cộng**    | **11,315**   |

### Phân bố nhãn (Training set)

- **Positive**: 5,071 mẫu (63.55%)
- **Negative**: 2,909 mẫu (36.45%)

_📊 Hình minh họa: Biểu đồ phân bố nhãn (từ notebook)_

---

## Slide 5: Tiền Xử Lý Dữ Liệu (Preprocessing)

### Các bước tiền xử lý

1. **Chuẩn hóa Unicode**

   - Chuyển về dạng NFC chuẩn
   - Xử lý các ký tự đặc biệt tiếng Việt

2. **Làm sạch văn bản**

   - Loại bỏ emoji, emoticons
   - Loại bỏ ký tự đặc biệt, số
   - Chuyển về chữ thường

3. **Tách từ (Word Tokenization)**

   - Sử dụng thư viện **Underthesea**
   - Ví dụ: "giảng viên nhiệt tình" → "giảng_viên nhiệt_tình"

4. **Loại bỏ Stopwords**

   - Các từ phổ biến không mang ý nghĩa: "và", "của", "là"...

5. **Label Encoding**
   - Positive → 1
   - Negative → 0

---

## Slide 6: Phân Tích Khám Phá Dữ Liệu (EDA) - Phần 1

### Phân bố nhãn Sentiment

_📊 Chèn hình: Biểu đồ cột phân bố nhãn_

**Nhận xét:**

- Dữ liệu **mất cân bằng** (imbalanced)
- Positive chiếm đa số (63.55%)
- Cần xem xét các kỹ thuật xử lý imbalanced data

### Phân bố độ dài câu

_📊 Chèn hình: Histogram phân bố số từ_

**Nhận xét:**

- Phần lớn câu có độ dài 5-20 từ
- Một số ít câu có độ dài > 50 từ

---

## Slide 7: Phân Tích Khám Phá Dữ Liệu (EDA) - Phần 2

### Độ dài câu theo nhãn Sentiment

_📊 Chèn hình: Box plot so sánh độ dài theo nhãn_

### Word Cloud - Từ phổ biến

_📊 Chèn hình: Word Cloud tổng thể_

_📊 Chèn hình: Word Cloud Positive vs Negative_

**Từ khóa nổi bật:**

- **Positive**: "tận tình", "nhiệt tình", "hay", "tốt", "vui tính"
- **Negative**: "chưa", "cần", "nên", "buồn ngủ"

---

## Slide 8: Phương Pháp Biểu Diễn Văn Bản

### TF-IDF (Term Frequency - Inverse Document Frequency)

**Công thức:**

```
TF-IDF(t, d) = TF(t, d) × IDF(t)
```

Trong đó:

- **TF(t, d)**: Tần suất từ t trong văn bản d
- **IDF(t)**: log(N / df(t)) - Nghịch đảo tần suất tài liệu

### Tham số sử dụng

| Tham số      | Giá trị            |
| ------------ | ------------------ |
| max_features | 5000 - 10000       |
| ngram_range  | (1, 1) hoặc (1, 2) |
| min_df       | 2 - 5              |
| max_df       | 0.95               |

### Ưu điểm

- Đơn giản, hiệu quả
- Giảm trọng số từ phổ biến
- Tăng trọng số từ đặc trưng

---

## Slide 9: Mô Hình Machine Learning

### Các mô hình sử dụng

| Mô hình                          | Mô tả                                      |
| -------------------------------- | ------------------------------------------ |
| **Logistic Regression**          | Mô hình tuyến tính đơn giản, hiệu quả      |
| **SVM (Support Vector Machine)** | Tìm siêu phẳng phân cách tối ưu            |
| **Random Forest**                | Ensemble learning với nhiều cây quyết định |

### Hyperparameter Tuning

- Sử dụng **GridSearchCV** / **RandomizedSearchCV**
- Cross-validation: 5-fold
- Metric tối ưu: F1-Score (macro)

### Pipeline

```
Text → TF-IDF Vectorizer → ML Model → Prediction
```

---

## Slide 10: Kết Quả Thực Nghiệm - Bảng So Sánh

### Hiệu suất các mô hình trên Test Set

| Mô hình             | Accuracy | Precision | Recall | F1-Score |
| ------------------- | -------- | --------- | ------ | -------- |
| Logistic Regression | XX.XX%   | XX.XX%    | XX.XX% | XX.XX%   |
| SVM                 | XX.XX%   | XX.XX%    | XX.XX% | XX.XX%   |
| Random Forest       | XX.XX%   | XX.XX%    | XX.XX% | XX.XX%   |

_📝 Lưu ý: Điền số liệu thực tế từ kết quả chạy notebook_

### Mô hình tốt nhất

- **[Tên mô hình]** đạt hiệu suất cao nhất
- F1-Score: **XX.XX%**

---

## Slide 11: Kết Quả Thực Nghiệm - Confusion Matrix

### Confusion Matrix - Mô hình tốt nhất

_📊 Chèn hình: Confusion Matrix từ notebook_

### Classification Report

```
              precision    recall  f1-score   support

    negative       X.XX      X.XX      X.XX       XXX
    positive       X.XX      X.XX      X.XX       XXX

    accuracy                           X.XX      XXXX
   macro avg       X.XX      X.XX      X.XX      XXXX
weighted avg       X.XX      X.XX      X.XX      XXXX
```

### Phân tích

- Nhãn **Positive** được dự đoán tốt hơn (do nhiều mẫu hơn)
- Một số trường hợp **False Negative** cần cải thiện

---

## Slide 12: Giảm Chiều và Trực Quan Hóa

### Các phương pháp giảm chiều

| Phương pháp | Mô tả                                                   |
| ----------- | ------------------------------------------------------- |
| **PCA**     | Principal Component Analysis - Giảm chiều tuyến tính    |
| **t-SNE**   | t-Distributed Stochastic Neighbor Embedding - Phi tuyến |
| **UMAP**    | Uniform Manifold Approximation and Projection           |

### Trực quan hóa không gian đặc trưng

_📊 Chèn hình: PCA 2D visualization_

_📊 Chèn hình: t-SNE visualization_

**Nhận xét:**

- Có sự phân tách rõ ràng giữa 2 lớp sentiment
- Một số điểm dữ liệu chồng chéo → khó phân loại

---

## Slide 13: Kết Luận

### Tóm tắt kết quả

✅ Xây dựng thành công pipeline phân tích sentiment tiếng Việt

✅ Tiền xử lý văn bản với các kỹ thuật NLP phù hợp

✅ So sánh nhiều mô hình Machine Learning

✅ Đạt được độ chính xác **XX%** trên tập test

### Thách thức gặp phải

- Dữ liệu mất cân bằng giữa các lớp
- Xử lý từ tiếng Việt đặc thù (teencode, từ lóng)
- Một số câu ngắn khó xác định sentiment

### Bài học kinh nghiệm

- Tiền xử lý đóng vai trò quan trọng
- Cần tune hyperparameter kỹ lưỡng
- TF-IDF vẫn hiệu quả cho bài toán phân loại văn bản

---

## Slide 14: Hướng Phát Triển

### Cải tiến ngắn hạn

- 🔧 Xử lý dữ liệu mất cân bằng (SMOTE, Class weights)
- 🔧 Thêm các n-gram features
- 🔧 Kết hợp với đặc trưng thủ công (hand-crafted features)

### Áp dụng Deep Learning

- 🚀 **LSTM / BiLSTM / GRU**
- 🚀 **CNN for Text Classification**
- 🚀 **Attention Mechanism**

### Fine-tune Pre-trained Models

- 🌟 **PhoBERT** - BERT cho tiếng Việt
- 🌟 **Qwen2.5** - Large Language Model
- 🌟 **mBERT** - Multilingual BERT

### Mở rộng phạm vi

- 📈 Áp dụng cho các chủ đề khác trong dataset
- 📈 Phân loại 3 lớp: Positive / Neutral / Negative
- 📈 Xây dựng ứng dụng demo thực tế

---

## Slide 15: Tài Liệu Tham Khảo

1. UIT-VSFC: Vietnamese Students' Feedback Corpus for Sentiment Analysis
2. Underthesea - Vietnamese NLP Toolkit
3. Scikit-learn: Machine Learning in Python
4. PhoBERT: Pre-trained language models for Vietnamese

---

## Slide 16: Q&A

# Cảm ơn đã lắng nghe!

**Câu hỏi và thảo luận**

📧 Email: [email]
📱 GitHub: [link repository]

---

# Phụ lục: Hướng dẫn sử dụng

## Các hình ảnh cần export từ notebook:

1. Biểu đồ phân bố nhãn (Slide 4, 6)
2. Histogram phân bố độ dài câu (Slide 6)
3. Box plot so sánh độ dài theo nhãn (Slide 7)
4. Word Cloud (Slide 7)
5. Confusion Matrix (Slide 11)
6. PCA/t-SNE visualization (Slide 12)

## Số liệu cần cập nhật:

- Accuracy, Precision, Recall, F1-Score từ kết quả thực nghiệm
- Thông số Confusion Matrix
- Classification Report

## Gợi ý thiết kế:

- Sử dụng template PowerPoint chuyên nghiệp
- Màu sắc nhất quán (2-3 màu chính)
- Font chữ: Roboto, Open Sans, hoặc Times New Roman
- Kích thước font: Tiêu đề 36-44pt, Nội dung 24-28pt
