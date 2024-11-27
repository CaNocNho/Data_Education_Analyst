# Hướng dẫn đọc dữ liệu chuẩn hóa

## I. Tổng quan về bộ dữ liệu
Bộ dữ liệu được thu thập từ **1.067 mẫu**, mỗi mẫu có **307 thuộc tính đặc trưng** thông qua các câu hỏi khảo sát chi tiết. Dữ liệu được thiết kế để phân tích các yếu tố ảnh hưởng đến sự phát triển cá nhân, nghề nghiệp và giáo dục từ thời điểm học **trung học cơ sở (THCS)** đến hiện tại. Bộ dữ liệu bao gồm:

- **Thông tin cá nhân**
- **Quá trình học tập**
- **Hoạt động hướng nghiệp**
- **Tác động từ môi trường giáo dục và gia đình**

---

### 1. Cấu trúc bộ dữ liệu
#### **a. Thông tin chung**
- **Câu 1 - Câu 7**: Thông tin cá nhân (trường học, loại hình trường/lớp, nguyên quán, giới tính, dân tộc, độ tuổi).
- **Câu 8 & 8a**: Hành trình sau THCS (học tiếp, đi làm) và nghề nghiệp ở các giai đoạn (THPT, trung cấp, cao đẳng, đại học).
- **Câu 9 - Câu 13a**: Nghề nghiệp hiện tại, thay đổi công việc, lý do thay đổi, nghề nghiệp của cha mẹ thời THCS, và điểm trung bình lớp 9.

#### **b. Kết quả học tập lớp 9**
- **Câu 14 - Câu 18**: 
  - Điểm trung bình lớp 9.
  - Môn học: 
    - Đạt kết quả cao nhất/thấp nhất.
    - Yêu thích nhất/không thích nhất.

#### **c. Hoạt động học nghề và hướng nghiệp tại THCS**
- **Câu 1 - Câu 1e**: Trải nghiệm học nghề (loại nghề, chứng chỉ, mức độ áp dụng thực tế).
- **Câu 2**: Hình thức tham gia hướng nghiệp (dạy môn khoa học cơ bản, sinh hoạt hướng nghiệp, tham quan làng nghề).
- **Câu 3 & 3a**: Học tập, thực hành kỹ năng tại trung tâm giáo dục hoặc làng nghề truyền thống.

#### **d. Các yếu tố ảnh hưởng đến định hướng nghề nghiệp**
- **Câu 4 & 4a**: Hoạt động tìm hiểu năng lực bản thân, thị trường lao động, tư vấn hướng nghiệp, tham quan thực tế.
- **Câu 5**: Đánh giá mức độ ảnh hưởng từ:
  - Sở thích cá nhân.
  - Tư vấn của giáo viên/gia đình.
  - Bạn bè.
  - Chính sách tuyển dụng.

## II. Phương thức chuẩn hóa dữ liệu
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



Xử lý chuẩn hóa về dạng số một số cột dữ liệu đặc biệt:
 - ***cột "Câu 7.   Tuổi của anh/chị ?"***:
    - Dữ liệu thô là dữ liệu chuỗi. Thực hiện lọc các giá trị số hoặc năm sinh của dữ liệu để tính tuổi hiện tại sau đó mã hóa theo nhóm tuổi
 - ***cột "Câu 10a.     Nếu có, Lý do Anh/chị đã từng thay đổi công việc?, Câu 7. Khi học THCS, anh/chị biết gì về yêu cầu của những nhóm nghề đó?
 [Kỹ năng thao tác khéo léo], ...  "***:
    - Dữ liệu thô là dữ liệu chuỗi tập hợp các lựa chọn. Thực hiện tách những lựa chọn thành 1 đặc trưng mới với kiểu dữ liệu binary 0 và 1
 - ***Các cột dữ liệu nghề nghiệp khác được nhập bằng tay sẽ không theo quy chuẩn nào. ví dụ như "Câu 10c.      Công việc mà anh/chị cho là thành công nhất nhờ việc hướng nghiệp ở THCS?, Câu 11a. Tên cụ thể nghề khác?, ...."***:
    - Dữ liệu thô là dữ liệu chuỗi nhập bằng tay của người khảo sát nên không có quy chuẩn. Thực hiện cụ thể hóa từng nhóm ngành chính lại với nhau dựa trên tất cả các dữ liệu người dùng đã nhập và chuẩn hóa về dữ liệu số.
 - ***Các cột dữ liệu khảo sát theo mẫu nhưng lại sai lệch kiểu mẫu. ví dụ như "Câu 5. Khi học THCS, anh/chị thấy những yếu tố sau có ảnh hưởng thế nào đến việc lựa chọn nghề tương lai của anh/chị? [Am hiểu về kiến thức, kỹ năng nghề nghiệp đó], ...."***:
    - Dữ liệu thô là dữ liệu chuỗi nhập bằng tay của người khảo sát nên không có quy chuẩn. Thực hiện cụ thể hóa từng nhóm ngành chính lại với nhau dựa trên tất cả các dữ liệu người dùng đã nhập và chuẩn hóa về dữ liệu số.
 

---

### 4. Dữ liệu nhị phân
Các cột dữ liệu có giá trị nhị phân khác trong tệp chuẩn hóa như (0 và 1) sẽ ngầm hiểu mang ý nghĩa:
- **1**: Có (hoặc đúng).
- **0**: Không (hoặc sai).


---

### 5. File sau khi chuẩn hóa là file 
**"Standardize.csv"**

