# Tìm hiểu một số loại mật mã học cổ điển

| Thuật toán | Thuộc loại                  | Giải thích                    |
| ---------- | --------------------------- | ----------------------------- |
| Caesar     | Substitution                | Dịch chữ cái cố định          |
| Affine     | Substitution                | Công thức toán học tuyến tính |
| Vigenère   | Polyalphabetic Substitution | Dùng nhiều bảng Caesar        |
| Playfair   | Digraph Substitution        | Mã hóa theo cặp chữ cái       |
| Hill       | Matrix-based Substitution   | Thay thế dựa trên ma trận     |

Chúng ta sẽ tìm hiểu 5 loại thuật toán này dựa trên các tiêu chí sau:

* Nguyên lý hoạt động
* Cách thức mã hóa – giải mã
* Các điểm yếu bảo mật

---

## 1. Caesar Cipher

### 🔹 Nguyên lý hoạt động

Caesar là thuật toán **thay thế đơn bảng (monoalphabetic substitution)**. Mỗi chữ cái trong bản rõ được dịch đi một số bước cố định trong bảng chữ cái.

### 🔹 Mã hóa – Giải mã

* Mã hóa:
  [ E(x) = (x + k) \bmod 26 ]
* Giải mã:
  [ D(x) = (x - k) \bmod 26 ]

Ví dụ với k = 3:
A → D, B → E, C → F

### 🔹 Điểm yếu bảo mật

* Không gian khóa rất nhỏ (25 khóa)
* Dễ bị brute-force
* Phân tích tần suất phá được ngay

---

## 2. Affine Cipher

### 🔹 Nguyên lý hoạt động

Affine là mở rộng của Caesar, sử dụng hàm tuyến tính để thay thế ký tự.

### 🔹 Mã hóa – Giải mã

* Mã hóa:
  [ E(x) = (a \cdot x + b) \bmod 26 ]
* Giải mã:
  [ D(x) = a^{-1}(x - b) \bmod 26 ]

Trong đó:

* a phải **nguyên tố cùng nhau với 26**

### 🔹 Điểm yếu bảo mật

* Vẫn là thay thế đơn bảng
* Bị phá bằng phân tích tần suất
* Không an toàn khi biết một vài cặp plaintext–ciphertext

---

## 3. Vigenère Cipher

### 🔹 Nguyên lý hoạt động

Vigenère là thuật toán **đa bảng (polyalphabetic substitution)**, dùng một từ khóa để thay đổi bảng Caesar theo từng ký tự.

### 🔹 Mã hóa – Giải mã

* Mỗi ký tự plaintext được mã hóa bằng một Caesar Cipher khác nhau
* Khóa được lặp lại cho đến khi đủ độ dài bản rõ

Ví dụ:
Plaintext: ATTACK
Key:       LEMONL

### 🔹 Điểm yếu bảo mật

* Có chu kỳ khóa
* Bị phá bằng **Kasiski Examination** hoặc **Index of Coincidence**
* Không an toàn trước máy tính hiện đại

---

## 4. Playfair Cipher

### 🔹 Nguyên lý hoạt động

Playfair mã hóa **theo cặp chữ cái (digraph)** bằng cách sử dụng bảng 5×5 (gộp I/J).

### 🔹 Mã hóa – Giải mã

* Chia plaintext thành các cặp ký tự
* Áp dụng 3 quy tắc:

  * Cùng hàng
  * Cùng cột
  * Hình chữ nhật

### 🔹 Điểm yếu bảo mật

* Không mã hóa từng ký tự đơn
* Dễ bị phá với ciphertext dài
* Không phù hợp cho dữ liệu nhị phân

---

## 5. Hill Cipher

### 🔹 Nguyên lý hoạt động

Hill Cipher sử dụng **đại số tuyến tính**, mã hóa theo khối ký tự bằng phép nhân ma trận.

### 🔹 Mã hóa – Giải mã

* Mã hóa:
  [ C = K \cdot P \bmod 26 ]
* Giải mã:
  [ P = K^{-1} \cdot C \bmod 26 ]

Trong đó K là ma trận khóa khả nghịch.

### 🔹 Điểm yếu bảo mật

* Dễ bị tấn công nếu biết plaintext
* Không có tính ngẫu nhiên
* Không chống được known-plaintext attack

---

## 📌 Nhận xét chung

* Các thuật toán mật mã cổ điển **không còn an toàn** trong thực tế
* Có giá trị lớn trong **giảng dạy và nghiên cứu nền tảng mật mã học**
* Là tiền đề cho các thuật toán mật mã hiện đại như AES, RSA
