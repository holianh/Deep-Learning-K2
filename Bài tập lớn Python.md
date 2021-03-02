# Bài tập lớn kết thúc Python
Đây là bài tập tổng hợp, vượt qua bài này thì có thể chuyển sang học bài kế tiếp. Yêu cầu tự làm, không sao chép đáp án. Sau khi tự làm, hoàn thiện như yêu cầu, học viên (HV) up bài lên github và gửi link cho thầy giáo.
Ưu tiên làm trên colab (phần crawl data có thể chạy riêng)

## Mục tiêu:
-	Tạo và duyệt file, có nội dung là data và label của data đó, nội dung chỉ cần đơn giản, tạo file tự động bằng các crawl data trên mạng về. 
-	Xử lý // để giải bài toán đơn giản dựa trên data đó.
-	Khi đang xử lý // có thể nhấn ctr-c để thoát
-	Gọi hàm // phải có tham số truyền vào và nhận giá trị về, hiển thị và ghi vào file
-	Tất cả các mục xử lý song song hoặc tuần tự bằng vòng for đối với data cần có tqdm (thanh hiển thị tiến trình xử lý), vì nó sẽ có thể có rất nhiều, xử lý có thể rất lâu, nên cần tqdm để người xem đỡ sốt ruột

## Đề bài: 
Viết chương trình thực hiện công việc sau có thể chạy trên local và colab, data tự sinh trong quá trình chạy code, hoặc tải về từ địa chỉ có sẵn. 
Tự chọn một trong số các nhãn, số lượng nhãn và số lượng mẫu:
-	Thể loại, <The_loai>: [“các loại hoa”, “các biển số xe”, “các khuôn mặt”, “các vân tay”, “các bài thơ”, “các loại lá cây”, “các đồ vật”, “các đoạn audio”, “các loại quần áo”, “các loại xe hơi”, “các loại hàng tạp hoá”, “ kết quả ]
-	Số lượng nhãn, <nNhan>: ít nhất 5 nhãn
-	Số lượng mẫu, <nMau>: ít nhất 1000 mẫu

### 1.	Tạo data: 
Dùng Python lập trình tự động tìm kiếm và tải về <The_loai> và nhãn của nó, ghi vào thư mục có tên thư mục hợp lý, con người dễ kiểm soát, mỗi mẫu data/label đều được định danh bằng ID chung. Số lượng ít nhất <nNhan>, mỗi nhãn ít nhất <nMau>
Nếu việc sinh data bắt buộc phải chạy riêng trên local, thì bài cần đính kèm code và cách dùng (có mô tả và hdsd sao cho không cần hiểu, chỉ cần làm theo là có data như ý), trong main code cần tự động tải data (đã chạy trên local) về, tự giải nén để có folder như ý cho các phần tiếp theo; 
Nếu data tự sinh trong quá trình chạy code trên colab được thì main code chạy để sinh data. 

### 2.	Đọc dữ liệu: 
Viết hàm đọc một mẫu, cho ID, tìm data tương ứng để đọc ra kết quả
input là ID của mẫu, 
output có dạng: [data, label], trong đó kích thước data có thể nhiều chiều dữ liệu gốc dạng số/xâu/…, label 1 chiều/số/xâu/…

### 3.	Chuẩn hoá: 
Viết hàm số hoá dữ liệu của bước 2, 
đầu vào là [data, label] dạng thô, 
đầu ra là [data,label] đã được số hoá và chuẩn hoá về [0..1]

### 4.	Xử lý: 
Viết hàm hiển thị các thông tin quan trọng của data lên màn hình, vd: kích thước data/label, mean, min, max, histogram, …
đầu vào là data, label 
đầu ra là list các thông tin quan trọng cần xem, ảnh histogram của các đặc trưng, ảnh histogram của labels

### 5.	main code:
Viết hàm xử lý các tác vụ bên trên một cách song song, có hiển thị trạng thái tiến trình đang xử lý bằng tqdm (lồng nhau nếu cần) hoặc tương đương.
Đầu vào phần song song là n_CPU, data path
Đầu ra: in thông tin lên màn hình, trả tất cả kết quả về biến, duyệt biến và lưu tất cả kết quả vào 1 file npz/pickel/HDF5

Chú ý, nếu chạy trên Ipython hoặc Colab, tất cả các mục hiển thị ra màn hình thay bằng in ra output cell.
