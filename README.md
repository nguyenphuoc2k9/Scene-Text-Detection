
# Nhận dạng Văn bản trong Ảnh (Scene Text Recognition)

## Giới thiệu
Dự án này nhằm xây dựng một hệ thống nhận dạng văn bản trong ảnh từ môi trường thực tế. Mục tiêu chính là phát triển một pipeline kết hợp YOLOv11 (phát hiện văn bản) và CRNN (nhận diện văn bản). 

### Ứng dụng
- Nhận diện văn bản từ tài liệu, báo chí, biển hiệu, v.v.
- Tìm kiếm thông tin từ hình ảnh.
- Tự động hóa quy trình xử lý dữ liệu, ví dụ: đơn hàng, thanh toán.

---

## Quy trình
Pipeline gồm 2 giai đoạn chính:
1. **Phát hiện văn bản (Text Detection):** Sử dụng YOLOv11 để xác định vị trí các khối văn bản.
2. **Nhận diện văn bản (Text Recognition):** Sử dụng CRNN để trích xuất nội dung văn bản.

---

## Thiết lập và Triển khai
### 1. Cài đặt môi trường
- Cài đặt các thư viện cần thiết:
  ```bash
  pip install ultralytics torch torchvision timm
  ```
  
- Chuẩn bị dữ liệu từ bộ **ICDAR2003**. 

### 2. Huấn luyện
- **Phát hiện văn bản:** Huấn luyện YOLOv11 với dữ liệu được định dạng đúng.
- **Nhận diện văn bản:** Sử dụng mô hình CRNN với hàm mất mát CTC Loss để huấn luyện.

### 3. Đánh giá
- Đánh giá mô hình trên tập validation và test, sau đó lưu mô hình đã huấn luyện.

---

## Hướng dẫn sử dụng
### 1. Nhận diện văn bản từ ảnh
- Chạy hàm `predict()` để sử dụng pipeline kết hợp YOLOv11 và CRNN:
  ```python
  from pipeline import predict
  
  predictions = predict('path/to/image.jpg', data_transforms, yolo_model, crnn_model, idx_to_char, device)
  print(predictions)
  ```

### 2. Trực quan hóa kết quả
- Sử dụng hàm `visualize_detections()` để hiển thị các kết quả dự đoán trên ảnh.

---

## Thư viện và Công cụ sử dụng
- **YOLOv11:** Phát hiện văn bản.
- **CRNN:** Nhận diện văn bản.
- **PyTorch:** Thư viện deep learning chính.
- **Ultralytics:** Hỗ trợ YOLOv11.

---