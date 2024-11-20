# Hướng dẫn đọc dữ liệu chuẩn hóa

### 1. Loại bỏ các cột không thể chuẩn hóa
Để đảm bảo dữ liệu dễ dàng chuẩn hóa, chúng tôi đã loại bỏ một số cột không thể thực hiện chuẩn hóa được, bao gồm:
- **Dấu thời gian**
- **Phần 1: NHỮNG THÔNG TIN CHUNG**
- **Câu 1: Anh/chị đã học trường THCS nào (Tên trường - Huyện - Tỉnh)?**
- **Câu 4: Nguyên quán/nơi sinh/nơi thường trú (khi anh/chị học THCS)?**

Các cột này bị loại bỏ vì:
- Có quá nhiều kiểu dữ liệu khác nhau.
- Có quá nhiều dữ liệu thiếu, không thể chuẩn hóa.

---

### 2. Đổi tên các cột dữ liệu
Các cột dữ liệu đã được đổi tên để thuận tiện cho việc chuẩn hóa. Danh sách các tên cột cũ và mới có thể tham khảo trong file **"rename_mapping.csv"** với định dạng:  
`Tên cũ, Tên mới`

---

### 3. Chuẩn hóa dữ liệu
Các cột dữ liệu đã được chuẩn hóa và chuyển về dạng số. Các tệp chuẩn hóa được lưu trong thư mục **`standardize`**, với tên tệp tương ứng với tên cột cần chuẩn hóa. Nếu có giá trị thiếu mặc định sẽ là **-1**

Mỗi tệp chuẩn hóa với định dạng:  
`Original Value,Mapped Value`


---

### 4. Dữ liệu nhị phân
Các cột dữ liệu có giá trị nhị phân (0 và 1) mang ý nghĩa:
- **1**: Có (hoặc đúng).
- **0**: Không (hoặc sai).


---

### 5. File sau khi chuẩn hóa là file 
**"Standardize.csv"**

