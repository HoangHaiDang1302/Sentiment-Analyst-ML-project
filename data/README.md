# 📂 Thư mục Data - UIT-VSFC Dataset

## Mô tả

Thư mục này chứa bộ dữ liệu **UIT-VSFC** (Vietnamese Students' Feedback Corpus) dùng cho bài toán phân tích cảm xúc văn bản tiếng Việt.

## Cấu trúc dữ liệu

```
data/
├── UIT-VSFC-train.json         # Tập huấn luyện
├── UIT-VSFC-train-segment.json # Tập huấn luyện (đã tách từ)
├── UIT-VSFC-dev.json           # Tập validation
├── UIT-VSFC-dev-segment.json   # Tập validation (đã tách từ)
├── UIT-VSFC-test.json          # Tập kiểm tra
├── UIT-VSFC-test-segment.json  # Tập kiểm tra (đã tách từ)
├── vietnamese-stopwords.txt    # Danh sách stopwords tiếng Việt
└── vietnamese-semtimentwords.txt # Danh sách từ cảm xúc tiếng Việt
```

## Định dạng dữ liệu

Mỗi file JSON chứa một mảng các đối tượng với cấu trúc:

```json
{
  "sentence": "Văn bản phản hồi của sinh viên",
  "topic": "Chủ đề (lecturer/program/facility)",
  "sentiment": "Nhãn cảm xúc (positive/negative/neutral)"
}
```

## Tải dữ liệu

Nếu bạn cần tải lại dữ liệu gốc, có thể download từ:

- **Nguồn chính**: [UIT NLP Lab](https://nlp.uit.edu.vn/datasets/)
- **Kaggle**: Tìm kiếm "UIT-VSFC" trên Kaggle

## Thống kê dữ liệu

| Tập dữ liệu | Số lượng mẫu |
| ----------- | ------------ |
| Train       | ~11,000      |
| Dev         | ~1,500       |
| Test        | ~3,000       |

## Lưu ý

⚠️ **Không commit dữ liệu lớn lên Git!**

Nếu dữ liệu quá lớn, hãy:

1. Thêm các file JSON vào `.gitignore`
2. Chỉ giữ lại file README này và file mẫu nhỏ
3. Hướng dẫn người dùng tải dữ liệu từ nguồn chính
