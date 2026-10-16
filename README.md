# HCM_KS26_CNTT2_IT108_Session10_Ex05
##  Phần 1. Phân tích Input/Output và phần cứng

### 1. Mô hình IPO

| Thành phần | Nội dung |
|---|---|
| Input | Nhiệt độ, độ ẩm đất, độ ẩm không khí từ cảm biến |
| Process | SoC xử lý dữ liệu, so sánh với ngưỡng cài đặt và quyết định tưới |
| Output | Bật/tắt máy bơm, hiển thị thông số và lưu nhật ký |

### 2. Sơ đồ phối hợp phần cứng

| Cảm biến IoT | SoC / Bộ điều khiển | Màn hình | Máy bơm |
|---|---|---|---|
| Nhiệt độ · Độ ẩm đất | Thu thập và xử lý dữ liệu | Hiển thị thông số | Tưới nước tự động |

- **SoC (System on a Chip):** Bộ xử lý tích hợp các thành phần cần thiết trên một chip.
- **IPO:** Dữ liệu đầu vào → xử lý → kết quả đầu ra.
- **DIKW:** Dữ liệu → Thông tin → Tri thức → Hành động/quyết định.

---

##  Phần 2. File README.md hoàn chỉnh

#  Smart-Farm – Hệ thống nông trại thông minh

Smart-Farm là hệ thống IoT giúp theo dõi môi trường và tự động tưới nước cho trang trại Lan, tiết kiệm thời gian và tài nguyên.

### 1. Giới thiệu dự án

Hệ thống sử dụng cảm biến để thu thập dữ liệu nhiệt độ, độ ẩm đất và ánh sáng. Bộ điều khiển xử lý dữ liệu, sau đó quyết định bật hoặc tắt máy bơm.

**Mục tiêu**

- Theo dõi điều kiện môi trường.
- Tự động tưới Lan khi đất khô.
- Lưu dữ liệu để theo dõi và phân tích.

### 2. Sơ đồ hệ thống


**Nguyên lý hoạt động:**

1. Cảm biến thu thập dữ liệu môi trường.
2. SoC nhận và xử lý dữ liệu.
3. Bộ điều khiển ra lệnh bật/tắt máy bơm.
4. Hệ thống lưu nhật ký và hiển thị kết quả.

### 3. Hướng dẫn cài đặt

**Yêu cầu:** Python đã được cài đặt và thiết bị đã kết nối đúng.

```bash
# Tải mã nguồn dự án
git clone <URL_REPOSITORY>
cd smart-farm

# Cài đặt thư viện nếu có file requirements.txt
pip install -r requirements.txt

# Chạy chương trình
python main.py
```

### 4. Tính năng chính

- Thu thập dữ liệu cảm biến.
- Theo dõi nhiệt độ và độ ẩm đất.
- Tự động điều khiển máy bơm.
- Lưu và xem nhật ký hoạt động.
- Cảnh báo khi cảm biến gặp sự cố.

### 5. Bảng thông số kỹ thuật

| Thiết bị | Chức năng | Thông số tham khảo |
|---|---|---|
| DHT22 | Đo nhiệt độ, độ ẩm không khí | Độ chính xác nhiệt độ khoảng ±0,5°C |
| YL-69 | Đo độ ẩm đất | Cần hiệu chuẩn theo loại đất |
| ESP32 | Bộ điều khiển SoC/MCU | Hỗ trợ Wi-Fi, Bluetooth tùy phiên bản |
| Máy bơm DC | Tưới nước | Chọn theo điện áp và lưu lượng yêu cầu |
| Nguồn điện | Cấp nguồn | Phù hợp với từng thiết bị |

> **Lưu ý:** Thông số trên mang tính tham khảo, cần kiểm tra tài liệu của thiết bị thực tế.

### 6. Mô hình IPO

| Thành phần | Nội dung |
|---|---|
| Input | Nhiệt độ, độ ẩm đất, dữ liệu cảm biến |
| Process | SoC xử lý dữ liệu và so sánh với ngưỡng cài đặt |
| Output | Lệnh bật/tắt máy bơm, thông báo và nhật ký |

### 7. Chu kỳ Fetch – Decode – Execute

- **Fetch:** CPU lấy lệnh tưới từ bộ nhớ.
- **Decode:** CPU giải mã lệnh và xác định thao tác cần thực hiện.
- **Execute:** CPU thực hiện thao tác, gửi tín hiệu điều khiển máy bơm thông qua bộ điều khiển phù hợp.

### 8. Mô hình DIKW – Từ dữ liệu đến hành động

| Cấp độ | Ví dụ trong Smart-Farm |
|---|---|
| D – Data (Dữ liệu) | Cảm biến ghi nhận độ ẩm đất 25% |
| I – Information (Thông tin) | Độ ẩm đất đang thấp hơn ngưỡng 30% |
| K – Knowledge (Tri thức) | Đất khô có thể cần được tưới |
| W – Wisdom (Quyết định) | Kiểm tra điều kiện an toàn và bật máy bơm nếu cần |

**Quy trình:** Dữ liệu → Thông tin → Tri thức → Quyết định.

### 9. Lưu ý an toàn khi RAM đầy nhật ký

Khi nhật ký chiếm nhiều bộ nhớ, hệ thống có thể chạy chậm hoặc bị treo. Cần xử lý theo các bước sau:

1. Kiểm tra dung lượng RAM và dung lượng ổ đĩa.
2. Xác định các file nhật ký lớn, kiểm tra nội dung trước khi xử lý.
3. Sao lưu nhật ký quan trọng sang nơi lưu trữ khác.
4. Thiết lập cơ chế xoay vòng nhật ký (log rotation), giới hạn dung lượng và thời gian lưu.
5. Chỉ xóa các nhật ký cũ đã được xác nhận không còn cần thiết.
6. Nếu hệ thống vẫn bị treo, dừng dịch vụ theo quy trình an toàn trước khi khởi động lại.

### 10. Kết luận

Smart-Farm giúp người nông dân theo dõi môi trường và tưới Lan hiệu quả hơn. Cần kiểm tra cảm biến, nguồn điện và hệ thống điều khiển định kỳ để đảm bảo vận hành ổn định.

---

##  Phần 3. Kiểm thử tình huống RAM đầy

Khi RAM bị đầy do nhật ký, cần phân biệt RAM đầy với ổ đĩa đầy. File log thường chiếm dung lượng ổ đĩa; tuy nhiên, chương trình đọc hoặc giữ quá nhiều nhật ký trong bộ nhớ cũng có thể làm RAM đầy.

Cách xử lý an toàn là kiểm tra tài nguyên, sao lưu log quan trọng, giới hạn dung lượng và cấu hình xoay vòng nhật ký trước khi xóa dữ liệu.
