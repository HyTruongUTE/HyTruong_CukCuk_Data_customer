# Dự Án Thu Thập Dữ Liệu Khách Hàng Ngành Nhà Hàng & Dịch Vụ Ăn Uống

## Giới thiệu

Đây là tool tự động cào dữ liệu khách hàng thuộc nhóm ngành **Nhà hàng và các dịch vụ ăn uống phục vụ lưu động** từ trang **Infocom** để hỗ trợ **telesale cho team Cukcuk** của công ty MISA. Công cụ này giúp tối ưu hóa quy trình thu thập thông tin, giúp đội ngũ telesale tiếp cận khách hàng một cách nhanh chóng và hiệu quả.

## Công nghệ sử dụng

- **GitHub Actions**: Tự động hóa việc thu thập dữ liệu, đảm bảo lịch sử thay đổi minh bạch
- **Python**: Ngôn ngữ lập trình chính để crawl dữ liệu
- **Playwright**: Công cụ hỗ trợ tự động hóa trình duyệt
- **Excel**: Định dạng lưu trữ dữ liệu, dễ dàng xử lý và phân tích

## Cấu trúc dữ liệu

Dữ liệu được lưu trữ trong các file Excel và cập nhật định kỳ. Bạn có thể tìm thấy dữ liệu tại thư mục `result/`.

### Nguyên lý hoạt động

Dự án sử dụng bot tự động để thu thập dữ liệu từ trang web **[Infocom](https://infocom.vn/ma-nganh-nghe/5610/trang-1)** với tần suất **mỗi ngày 2 lần** vào **8h sáng và 1h chiều** (GMT+7). Các thông tin được thu thập bao gồm:

- **Tên khách hàng** (được làm sạch, loại bỏ số thứ tự dư thừa)
- **Mã số thuế** (được làm sạch, loại bỏ chữ "Copy" nếu có)
- **Số điện thoại**
- **Email**
- **Địa chỉ** (được phân tách thành Tỉnh/Thành phố, Quận/Huyện, Phường/Xã, Số nhà & Đường phố)
- **Ngành nghề kinh doanh**

### Cấu trúc thư mục dữ liệu
```
result/
├── infocom_data/
│   ├── data_customer_01-01-2024_1.xlsx
│   ├── data_customer_01-01-2024_2.xlsx
│   ├── data_customer_02-01-2024_1.xlsx
│   ├── ...
```
Mỗi file Excel chứa các cột dữ liệu:
- **Mã số thuế**
- **Tên khách hàng**
- **Điện thoại**
- **Email**
- **Địa chỉ (Tỉnh/Thành phố, Quận/Huyện, Phường/Xã, Số nhà & Đường phố)**
- **Ngành nghề**

## Hướng dẫn sử dụng

Dữ liệu thô được lưu trong thư mục `result/` dưới định dạng Excel. Bạn có thể sử dụng các công cụ như **Excel, Power BI, Python, R** để phân tích và trực quan hóa dữ liệu phục vụ cho mục đích telesale.

## Hướng dẫn cài đặt và chạy dự án

### Yêu cầu hệ thống
- **Python 3.8 trở lên**
- **pip** (Python package installer)
- **Chromium browser** (sẽ được cài đặt tự động)

### Các bước cài đặt

1. **Cài đặt các thư viện cần thiết:**
   ```sh
   pip install -r requirements.txt
   ```

2. **Cài đặt Chromium cho Playwright:**
   ```sh
   playwright install chromium
   ```

### Chạy dự án

1. **Chạy script crawl dữ liệu:**
   ```sh
   python crawl_datacustomer.py
   ```
2. **Dữ liệu sau khi crawl sẽ được lưu vào thư mục `result/` dưới dạng file Excel.**

### Lưu ý
- Script được thiết kế để **chạy tự động mỗi ngày 2 lần** thông qua **GitHub Actions**.
- Bạn có thể **tùy chỉnh tần suất cập nhật** trong file `.github/workflows/crawl.yml`.
- Đảm bảo có **kết nối internet** để script có thể lấy dữ liệu từ trang web.

## Tần suất cập nhật

Dữ liệu được cập nhật tự động **mỗi ngày 2 lần** vào **8h sáng và 1h chiều** thông qua **GitHub Actions**, đảm bảo tính liên tục và độ tin cậy của dữ liệu.

