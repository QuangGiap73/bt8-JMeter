# Kiểm thử RESTful API với Apache JMeter
Tài liệu này hướng dẫn cách sử dụng Apache JMeter để thực hiện kiểm thử hiệu năng và chức năng cơ bản của RESTful API, bao gồm gửi request, kiểm tra phản hồi, thêm kiểm tra tự động (assertion), và xem kết quả.

## Mục tiêu
Thực hiện kiểm thử API công khai https://jsonplaceholder.typicode.com/posts bằng JMeter với các mục tiêu:

Gửi request HTTP GET

Xem phản hồi JSON từ server

Kiểm tra dữ liệu phản hồi

Mô phỏng nhiều người dùng gửi request đồng thời

Tạo báo cáo kết quả

## Yêu cầu hệ thống
Java JDK 8 trở lên

Apache JMeter 5.5 trở lên


## Tạo Test Plan đơn giản
1. Tạo cấu trúc Test Plan
Thành phần	Mô tả
Test Plan	Dự án kiểm thử chính
Thread Group	Mô phỏng người dùng
HTTP Request	Gửi API request
View Results Tree / Summary Report	Xem kết quả
Assertion	Kiểm tra tự động nội dung phản hồi

# 2. Các bước cụ thể:
 ## A. Thêm Thread Group
  Test Plan → Add → Threads (Users) → Thread Group

Cấu hình:

Number of Threads (Users): 5

Loop Count: 2

 Tổng: 5 users × 2 vòng = 10 request gửi đến API
![Ảnh chụp màn hình 2025-06-19 173038](https://github.com/user-attachments/assets/987433f5-2478-4065-87ee-dc0b00770230)


 ## B. Thêm HTTP Request (GET)
Chuột phải Thread Group → Add → Sampler → HTTP Request

Cấu hình:

Name: Get All Posts

Method: GET

Server Name or IP: jsonplaceholder.typicode.com

Path: /posts

Port: (để trống hoặc 443 nếu HTTPS)
![image](https://github.com/user-attachments/assets/b729904a-67b0-439f-9959-91f0f1b1169b)


 ## C. Thêm View Kết quả
Chuột phải Thread Group → Add → Listener:

View Results Tree

Summary Report

![Ảnh chụp màn hình 2025-06-19 173554](https://github.com/user-attachments/assets/b7be9af1-705c-400c-94ca-54c967803344)


 ## D. Thêm Response Assertion (kiểm tra dữ liệu phản hồi)
Chuột phải vào HTTP Request → Add → Assertions → Response Assertion

Chọn:

Field to Test: Text Response

Pattern Matching Rule: Contains

Patterns: "userId" hoặc "title"
![image](https://github.com/user-attachments/assets/583ea35a-36b9-42fd-b513-43509074305d)


 Chạy Test
Bấm nút Run (▶) để bắt đầu kiểm thử

Mở tab View Results Tree để xem chi tiết phản hồi từng request

Mở Summary Report để xem số lượng request, thời gian phản hồi, lỗi (nếu có)
![Ảnh chụp màn hình 2025-06-19 173814](https://github.com/user-attachments/assets/a3070a49-fc31-4d4f-8293-10aabeadbfa8)



✅ Kết luận
Apache JMeter là công cụ mạnh mẽ giúp bạn kiểm thử cả hiệu năng lẫn chức năng của API. Qua ví dụ trên, bạn đã học được cách:

Cấu hình một test đơn giản

Kiểm tra phản hồi

Mô phỏng nhiều người dùng

Tạo báo cáo kết quả
