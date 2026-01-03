# 🎭 Vietnamese Sentiment Analysis - UIT-VSFC

Dự án phân tích cảm xúc (Sentiment Analysis) cho văn bản tiếng Việt sử dụng bộ dữ liệu **UIT-VSFC** (Vietnamese Students' Feedback Corpus).

## 📁 Cấu trúc thư mục

```
UIT-VSFC/
├── app/                    # Source code chính
│   ├── utils.py            # Các hàm tiền xử lý văn bản
│   └── models/             # Các model đã train
│       ├── sentiment_pipeline.pkl
│       ├── label_encoder.pkl
│       ├── model_metadata.pkl
│       └── stopwords.pkl
├── demo/                   # Demo và notebook
│   ├── demo_app.py         # Ứng dụng Streamlit demo
│   └── demo.ipynb          # Jupyter notebook demo đầy đủ
├── data/                   # Dữ liệu
│   ├── UIT-VSFC-train.json
│   ├── UIT-VSFC-dev.json
│   ├── UIT-VSFC-test.json
│   ├── vietnamese-stopwords.txt
│   └── vietnamese-semtimentwords.txt
├── reports/                # Báo cáo
│   └── Báo cáo machine learning.docx
├── slides/                 # Slide thuyết trình
│   └── slide_presentation.md
├── requirements.txt        # Dependencies
├── README.md               # File hướng dẫn này
└── .gitignore              # Git ignore file
```

## 🚀 Cài đặt

### 1. Clone repository

```bash
git clone <repository-url>
cd UIT-VSFC
```

### 2. Tạo virtual environment (khuyến nghị)

```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# hoặc
.\venv\Scripts\activate   # Windows
```

### 3. Cài đặt dependencies

```bash
pip install -r requirements.txt
```

## 💻 Sử dụng

### Chạy Demo Streamlit

```bash
cd demo
streamlit run demo_app.py
```

### Chạy Jupyter Notebook

```bash
jupyter notebook demo/demo.ipynb
```

## 📊 Mô tả dữ liệu

- **UIT-VSFC** (Vietnamese Students' Feedback Corpus) là bộ dữ liệu phản hồi của sinh viên Việt Nam
- Nhãn cảm xúc: `Positive` (Tích cực) và `Negative` (Tiêu cực)
- Các tập dữ liệu:
  - `train`: Tập huấn luyện
  - `dev`: Tập validation
  - `test`: Tập kiểm tra

## 🔧 Các chức năng chính

1. **Tiền xử lý văn bản tiếng Việt**

   - Chuẩn hóa Unicode
   - Loại bỏ dấu câu
   - Tokenize (tách từ)
   - Loại bỏ stopwords

2. **Huấn luyện model**

   - TF-IDF Vectorization
   - Machine Learning classifiers (SVM, Logistic Regression, etc.)

3. **Đánh giá model**
   - Accuracy, Precision, Recall, F1-Score
   - Confusion Matrix

## 📝 License

MIT License

## 👤 Tác giả

- [Tên của bạn]

## 📚 Tham khảo

- [UIT-VSFC Dataset](https://nlp.uit.edu.vn/datasets/)
