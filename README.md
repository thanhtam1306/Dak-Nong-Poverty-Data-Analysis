# Phân tích mối tương quan giữa cơ cấu độ tuổi và phân loại hộ nghèo tại tỉnh Đắk Nông phục vụ mục tiêu giảm nghèo bền vững

README này hướng dẫn cài đặt môi trường, chạy lại chương trình phân tích dữ liệu và kiểm tra các kết quả đầu ra của dự án.

## 1. Tổng quan

Dự án phân tích dữ liệu hộ nghèo và hộ cận nghèo tại tỉnh Đắk Nông từ các file Excel cấp huyện/xã. Quy trình bao gồm làm sạch dữ liệu, chuẩn hóa dữ liệu, tạo đặc trưng cấp hộ, phân tích khám phá, phân cụm hộ dân, phân tích chẩn đoán, xây dựng mô hình dự đoán và trực quan hóa kết quả bằng PowerBI.

Mục tiêu chính của dự án là hỗ trợ nhận diện đặc điểm nhân khẩu, địa bàn, dân tộc, cơ cấu lao động và các nhóm hộ có rủi ro cao để phục vụ phân tích và gợi ý chính sách.

## 2. Công nghệ và thư viện sử dụng

- **Ngôn ngữ:** Python
- **Môi trường chạy:** Jupyter Notebook (`.ipynb`) trên Visual Studio Code
- **Xử lý dữ liệu:** pandas, numpy, openpyxl
- **Trực quan hóa:** matplotlib, seaborn
- **Thống kê và kiểm định:** scipy, statsmodels
- **Machine Learning:** scikit-learn, xgboost
- **Dashboard:** Microsoft PowerBI
- **Định dạng dữ liệu:** Excel `.xlsx`

## 3. Quy trình xử lý và phân tích dữ liệu

Quy trình xử lý và phân tích dữ liệu của dự án:

```text
Excel raw data
      |
      v
Data Understanding
      |
      v
Data Preprocessing
      |
      v
Data Comparison & Quality Check
      |
      v
Feature Engineering
      |
      v
EDA + Diagnostic Analysis
      |
      v
Clustering + Predictive Modeling
      |
      v
Policy Area Validation
      |
      v
PowerBI Sync Source + Dashboard
```

## 4. Kết quả nổi bật

- Chuẩn hóa dữ liệu hộ nghèo/cận nghèo từ nhiều file Excel cấp huyện.
- Tạo bộ dữ liệu cấp hộ phục vụ phân tích, phân cụm và mô hình dự đoán.
- Xây dựng các phân tích theo địa bàn, dân tộc, độ tuổi, lao động và nhóm phụ thuộc.
- Phân cụm hộ dân bằng K-Means để nhận diện các nhóm hộ có đặc điểm tương đồng.
- Huấn luyện và so sánh mô hình Random Forest, XGBoost cho bài toán dự đoán tình trạng hộ.
- Tạo file `PowerBI_Sync_Source.xlsx` để đồng bộ dữ liệu cho dashboard PowerBI.

## 5. Dashboard và hình ảnh kết quả

File dashboard chính nằm tại:

```text
output/powerbi/Dashboard.pbix
```

Nguồn dữ liệu dùng để refresh dashboard:

```text
output/powerbi/sync_sources/PowerBI_Sync_Source.xlsx
```

Ban đầu dashboard PowerBI sử dụng trực tiếp một số dữ liệu gốc và dữ liệu sau xử lý. Sau khi bổ sung kết quả phân cụm, dự báo và đối chiếu chính sách, dự án tạo thêm file `PowerBI_Sync_Source.xlsx` như một lớp dữ liệu trung gian để gom phần lớn các bảng cần dùng cho dashboard vào cùng một workbook. Trong quá trình xây dựng dashboard, một số bảng/visual sử dụng dữ liệu đã được gom trong file sync này, đồng thời vẫn có một số phần sử dụng các trường dữ liệu từ dữ liệu gốc hoặc dữ liệu đã chuẩn hóa để giữ lại thông tin chi tiết cần thiết.

Một số hình ảnh dashboard PowerBI:

![Tổng quan](<output/image/tổng quan.png>)

![Hồ sơ nhân khẩu](<output/image/hồ sơ nhân khẩu.png>)

![Phân cụm và đặc trưng hộ](<output/image/phân cụm và đặc trưng hộ.png>)

![Phân tích chẩn đoán](<output/image/phân tích chẩn đoán.png>)

![Dự báo nghèo và ưu tiên rà soát](<output/image/dự báo nghèo và ưu tiên rà soát.png>)

![Tra cứu hộ](<output/image/tra cứu hộ.png>)

![Chính sách theo địa bàn](<output/image/chính sách theo địa bàn.png>)

![Chi tiết chính sách theo địa bàn](<output/image/chi tiết chính sách theo địa bàn.png>)

![Đánh giá chất lượng](<output/image/đánh giá chất lượng.png>)

## 6. Yêu cầu môi trường

Máy cần cài sẵn:

- Python 3.10 trở lên.
- Visual Studio Code.
- Extension Python và Jupyter trên Visual Studio Code.
- Microsoft PowerBI Desktop nếu muốn mở file dashboard `.pbix`.

Thư viện Python cần thiết được liệt kê trong file `requirements.txt`.

## 7. Cấu trúc thư mục

```text
NguyenHoangThanhTam/
|
|-- data/
|   |-- raw/                  # Dữ liệu Excel gốc theo huyện
|   |-- clean/                # Dữ liệu đã chuẩn hóa
|   |-- comparition/          # Kết quả so sánh dữ liệu
|   |-- feature_audit/        # Kết quả kiểm tra chất lượng feature
|   |-- model/                # Feature, clustering, diagnostic, predictive outputs
|   |-- review/               # File kiểm tra chất lượng dữ liệu
|
|-- notebooks/
|   |-- data_understanding.ipynb
|   |-- data_preprocessing.ipynb
|   |-- data_comparison.ipynb
|   |-- feature_audit.ipynb
|   |-- feature_engineering.ipynb
|   |-- eda.ipynb
|   |-- clustering.ipynb
|   |-- diagnostic_analysis.ipynb
|   |-- predictive_analysis.ipynb
|   |-- policy_area_validation.ipynb
|
|-- output/
|   |-- image/
|   |-- powerbi/
|   |   |-- Dashboard.pbix
|   |   |-- sync_sources/
|   |   |   |-- PowerBI_Sync_Source.xlsx
|
|-- 3122410371-Nguyễn Hoàng Thanh Tâm-Báo cáo thực tập tốt nghiệp.pdf
|-- Nguyen Hoang Thanh Tam_BaoCao.pptx
|-- note.ipynb
|-- README.md
|-- requirements.txt
```

## 8. Dữ liệu đầu vào

Đặt các file Excel gốc trong thư mục `data/raw`:

- `TP GIA NGHĨA.xlsx`
- `HUYỆN CƯ JUT.xlsx`
- `HUYỆN DAK MIL.xlsx`
- `HUYỆN KRÔNG NÔ.xlsx`
- `HUYỆN TUY ĐỨC.xlsx`
- `Huyện Đắk Glong.xlsx`
- `HUYỆN ĐẮK RLẤP.xlsx`
- `HUYỆN ĐẮK SONG.xlsx`
- `tổng hợp.xlsx`

Lưu ý: không đổi tên file hoặc thay đổi cấu trúc thư mục nếu chưa cập nhật lại đường dẫn trong notebook.

## 9. Cài đặt và chạy chương trình

Mở terminal tại thư mục gốc dự án:

Tạo môi trường ảo:

```bash
python -m venv .venv
```

Kích hoạt môi trường ảo trên Windows:

```bash
.venv\Scripts\activate
```

Kích hoạt môi trường ảo trên macOS/Linux:

```bash
source .venv/bin/activate
```

Cài đặt các thư viện cần thiết:

```bash
pip install -r requirements.txt
```

Mở dự án bằng Visual Studio Code:

```bash
code .
```

Trong Visual Studio Code:

1. Mở thư mục `notebooks`.
2. Mở từng file `.ipynb` theo đúng thứ tự ở mục 10.
3. Chọn kernel Python từ môi trường ảo `.venv`.
4. Chạy lần lượt các cell trong từng notebook.

## 10. Thứ tự chạy notebook

Chạy từng notebook theo thứ tự sau để tạo đầy đủ dữ liệu trung gian và kết quả cuối:

1. `notebooks/data_understanding.ipynb`
   - Đọc và tìm hiểu dữ liệu gốc.

2. `notebooks/data_preprocessing.ipynb`
   - Làm sạch, chuẩn hóa và gom dữ liệu các huyện.
   - Output chính: `data/clean/`.

3. `notebooks/data_comparison.ipynb`
   - So sánh dữ liệu trước và sau xử lý.
   - Output chính: `data/comparition/data_comparison_detailed.xlsx`.

4. `notebooks/feature_audit.ipynb`
   - Kiểm tra chất lượng biến và dữ liệu đầu vào cho mô hình.
   - Output chính: `data/feature_audit/feature_audit.xlsx`.

5. `notebooks/feature_engineering.ipynb`
   - Tạo bộ đặc trưng cấp hộ.
   - Output chính: `data/model/household_featured.xlsx`.

6. `notebooks/eda.ipynb`
   - Phân tích khám phá dữ liệu và trực quan hóa.

7. `notebooks/clustering.ipynb`
   - Phân cụm hộ dân bằng K-Means.
   - Output chính: `data/model/household_clustered.xlsx`, `data/model/cluster_profile.xlsx`.

8. `notebooks/diagnostic_analysis.ipynb`
   - Phân tích các yếu tố liên quan đến tình trạng nghèo/cận nghèo.
   - Output chính: `data/model/diagnostic_results.xlsx`.

9. `notebooks/predictive_analysis.ipynb`
   - Huấn luyện và đánh giá mô hình Random Forest, XGBoost.
   - Output chính: `data/model/random_forest_results.xlsx`, `data/model/xgboost_results.xlsx`.

10. `notebooks/policy_area_validation.ipynb`
    - Đối chiếu kết quả phân tích/mô hình với địa bàn và chính sách.
    - Output chính: `data/model/province_policy_lookup.xlsx`.

## 11. Kết quả đầu ra

Sau khi chạy xong, các kết quả chính nằm tại:

- `data/clean/`: dữ liệu đã chuẩn hóa.
- `data/comparition/`: kết quả so sánh dữ liệu.
- `data/feature_audit/`: kết quả kiểm tra feature.
- `data/model/`: feature cấp hộ, kết quả phân cụm, chẩn đoán, mô hình dự đoán và đối chiếu chính sách.
- `data/review/`: file kiểm tra chất lượng.
- `output/image/`: ảnh dashboard PowerBI và hình ảnh báo cáo/phụ trợ.
- `output/powerbi/sync_sources/PowerBI_Sync_Source.xlsx`: file dữ liệu trung gian gom các bảng cần dùng để đồng bộ PowerBI.
- `output/powerbi/Dashboard.pbix`: dashboard PowerBI.

## 12. Mở Dashboard PowerBI

Nếu chỉ cần xem dashboard:

1. Mở `output/powerbi/Dashboard.pbix` bằng PowerBI Desktop.
2. Kiểm tra nguồn dữ liệu đang trỏ đến `output/powerbi/sync_sources/PowerBI_Sync_Source.xlsx`.
3. Bấm Refresh để cập nhật dashboard nếu đã chạy lại các notebook.

## 13. Lỗi thường gặp

Nếu gặp lỗi thiếu thư viện, chạy lại:

```bash
pip install -r requirements.txt
```

Nếu notebook không đọc được file Excel, kiểm tra:

- File đã nằm đúng trong `data/raw`.
- Tên file không bị đổi so với đường dẫn trong notebook.
- File Excel không đang được mở và khóa bởi Microsoft Excel.

Nếu PowerBI không refresh được:

- Kiểm tra file `output/powerbi/sync_sources/PowerBI_Sync_Source.xlsx` có tồn tại.
- Cập nhật lại đường dẫn nguồn dữ liệu trong PowerBI nếu thư mục dự án bị di chuyển.

## 14. Ghi chú

- Kết quả phân tích chỉ đóng vai trò hỗ trợ ra quyết định, không thay thế khảo sát thực địa hoặc đánh giá chính sách chính thức.
- Khi cập nhật dữ liệu mới, cần chạy lại toàn bộ notebook theo đúng thứ tự trong mục 10.
- Nên đóng các file Excel đầu ra trước khi chạy lại notebook để tránh lỗi ghi file.
- Dự án được phát triển trên môi trường cục bộ và một số notebook hiện sử dụng đường dẫn tuyệt đối (Absolute Path) để đọc/ghi dữ liệu.
- Khi chạy trên máy tính khác hoặc sau khi thay đổi vị trí thư mục dự án, cần cập nhật lại các biến đường dẫn (ví dụ: `INPUT_DIR`, `OUTPUT_DIR`, `BASE_DIR`,...) trong notebook cho phù hợp.

## 15. Tác giả

Nguyễn Hoàng Thanh Tâm  
Data Analyst Intern  
Saigon University

Đề tài thực hiện trong thời gian thực tập tại Công ty TNHH Công nghệ Quốc tế VNA.

## 16. Mục đích sử dụng

Dự án này được thực hiện trong quá trình thực tập, nhằm phục vụ mục đích học tập, nghiên cứu và ứng dụng phân tích dữ liệu.

## 17. Liên hệ

**Nguyễn Hoàng Thanh Tâm**  
**Email:** tamnguyen130620004@gmail.com
