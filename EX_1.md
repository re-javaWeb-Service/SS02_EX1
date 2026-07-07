# Bài 1: Phân tích & Lựa chọn

## 1. Đáp án lựa chọn

Chọn **phương án B**.

## 2. Vì sao phương án B tối ưu nhất?

Phương án B là prompt tối ưu nhất vì có đầy đủ 5 thành phần quan trọng của một prompt hiệu quả:

### Vai trò

Prompt yêu cầu AI: **"Hãy đóng vai trò là một Java Senior Developer"**.

Điều này giúp AI hiểu rằng câu trả lời cần theo góc nhìn của một lập trình viên Java có kinh nghiệm, biết về Clean Code, refactor và bảo toàn logic nghiệp vụ.

### Mục tiêu

Mục tiêu được nêu rất rõ:

> Tái cấu trúc logic rẽ nhánh lồng nhau phức tạp của class DiscountService thành các câu lệnh điều kiện bảo vệ.

Nhờ đó AI biết chính xác cần làm gì: không phải viết lại toàn bộ chương trình, không phải đổi thuật toán tính chiết khấu, mà là refactor nested if-else sang guard clauses.

### Ngữ cảnh

Prompt gắn trực tiếp với class **DiscountService** và logic tính chiết khấu hiện có. AI có đủ bối cảnh để hiểu đoạn mã đang xử lý nghiệp vụ gì và cần giữ nguyên hành vi nào.

### Ràng buộc

Phương án B đưa ra các ràng buộc rất quan trọng:

- Giữ nguyên logic nghiệp vụ tính chiết khấu ban đầu.
- Không thay đổi kiểu dữ liệu đầu vào/đầu ra.
- Sử dụng Java 11.
- Dùng guard clauses / return sớm.

Các ràng buộc này giúp hạn chế nguy cơ AI tự ý đổi logic, đổi chữ ký hàm hoặc dùng cú pháp không phù hợp.

### Định dạng đầu ra

Prompt yêu cầu:

> Trình bày kết quả dưới dạng khối mã nguồn Java hoàn chỉnh kèm giải thích ngắn bằng tiếng Việt.

Đây là yêu cầu định dạng rõ ràng, giúp đầu ra dễ đọc, dễ kiểm tra và dễ nộp bài.

## 3. Mã Java minh họa sau khi refactor

```java
public class DiscountService {

    public double calculateDiscount(String type, double amount, boolean isHoliday) {
        if ("VIP".equals(type)) {
            if (amount <= 1000) {
                return amount * 0.15;
            }

            if (isHoliday) {
                return amount * 0.25;
            }

            return amount * 0.20;
        }

        if (amount <= 500) {
            return 0;
        }

        if (isHoliday) {
            return amount * 0.10;
        }

        return amount * 0.05;
    }
}
```

Đoạn mã trên vẫn giữ nguyên nghiệp vụ cũ nhưng giảm mức độ lồng nhau của `if-else`, giúp code dễ đọc và dễ bảo trì hơn.

## 4. Lý do loại trừ các phương án còn lại

### Phương án A

Prompt A: **"Tái cấu trúc code Java trên để nó đẹp hơn."**

Nhược điểm:

- Quá chung chung, không nêu rõ "đẹp hơn" là theo tiêu chí nào.
- Không yêu cầu sử dụng guard clauses.
- Không có ràng buộc giữ nguyên logic nghiệp vụ.
- Không nêu phiên bản Java.
- Không yêu cầu định dạng đầu ra cụ thể.

Vì vậy AI có thể sửa code theo nhiều hướng khác nhau, thậm chí thay đổi logic tính chiết khấu.

### Phương án C

Prompt C: **"Hãy sửa code Java này, bỏ bớt if-else lồng nhau đi và sử dụng cấu trúc Java Stream API để viết ngắn gọn nhất có thể."**

Nhược điểm:

- Yêu cầu dùng Java Stream API không phù hợp với bài toán rẽ nhánh điều kiện đơn giản.
- Mục tiêu "viết ngắn gọn nhất có thể" có thể làm code khó đọc hơn.
- Dễ khiến AI tạo ra giải pháp phức tạp không cần thiết.
- Không nhấn mạnh việc bảo toàn nghiệp vụ cũ.
- Không đúng trọng tâm đề bài là dùng guard clauses.

Vì vậy phương án C có nguy cơ làm sai yêu cầu hoặc tạo ra đoạn code khó bảo trì hơn.
