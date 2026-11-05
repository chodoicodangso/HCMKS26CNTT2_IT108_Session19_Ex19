**Phần 1: Báo cáo phân tích kiến trúc an ninh mật khẩu**  
**Nguy hiểm của việc lưu mật khẩu trên Chrome (tệp** Login Data**):** Chrome lưu mật khẩu cục bộ và sử dụng chính thông tin đăng nhập hệ điều hành (Windows/macOS) làm khóa mã hóa. Mã độc Infostealer khi lây nhiễm có thể dễ dàng trích xuất tệp Login Data cùng với khóa cục bộ này để giải mã và đánh cắp toàn bộ mật khẩu trong nháy mắt.  
**Zero-Knowledge, Client-side Decryption & Sự cố máy chủ:**  
**Zero-Knowledge:** Nhà cung cấp (như Bitwarden) không hề biết Master Password của bạn, họ chỉ lưu trữ dữ liệu đã bị mã hóa.  
**Client-side Decryption:** Việc giải mã dữ liệu diễn ra hoàn toàn trên thiết bị của người dùng (máy tính/điện thoại) bằng Master Password, trước khi gửi lên mạng chỉ có dữ liệu đã mã hóa.  
**Nếu Bitwarden bị hack:** Dữ liệu Két sắt vẫn an toàn. Hacker chỉ đánh cắp được các đoạn mã lộn xộn.Không có Master Password không thể giải mã được.  
**Phần 2: Thiết kế Chính sách & Kịch bản Chuyển đổi**  
**Thiết kế Master Passphrase:**  
**Phương pháp:** Sử dụng kỹ thuật Diceware (ghép 4-5 từ ngẫu nhiên không liên quan logic lại với nhau, phân cách bằng dấu gạch ngang hoặc khoảng trắng). Cách này dễ nhớ với con người nhưng độ entropy rất cao, vô hiệu hóa hoàn toàn Brute-Force.  
**Cấu hình chuẩn cho công cụ Generator (40 tài khoản):**  
**Độ dài:** 32 ký tự (tối đa theo ràng buộc yêu cầu để bảo mật cao nhất).  
**Quy định loại ký tự:** Bật (ON) toàn bộ:  
Chữ hoa (A-Z)  
Chữ thường (a-z)  
Chữ số (0-9)  
Ký tự đặc biệt (\!@\#\$%^&\*)  
**Hiệu quả chống Phishing của tính năng Tự động Điền (Auto-fill):** Con người dễ bị lừa bởi các ký tự vi đồng hình (homoglyph) như githúb.com hay domain phụ steampowered.xyz. Tuy nhiên, trình quản lý mật khẩu chỉ đối chiếu chính xác chuỗi URL/URI. Nếu URL sai lệch dù chỉ 1 ký tự so với gốc (github.com), Auto-fill sẽ "mù" và từ chối điền mật khẩu, giúp chặn đứng ngay lập tức nỗ lực Phishing.  
**Quy trình lưu trữ Khóa Cấp cứu (Emergency Kit):**  
**Bước 1:** Trưởng phòng Kỹ thuật xuất/in Emergency Kit (chứa Email, Master Password gốc, và mã dự phòng 2FA) ra bản giấy (hardcopy). Không lưu bản rõ trên bất kỳ máy tính nào.  
**Bước 2:** Cho bản giấy vào phong bì, niêm phong và ký giáp lai.  
**Bước 3:** Cất phong bì này vào két sắt vật lý của Studio (chỉ Giám đốc hoặc người đại diện pháp luật giữ chìa/mã).  
**Bước 4:** Khi có sự cố đột xuất, Trưởng nhóm cùng Giám đốc lập biên bản mở két, sử dụng bộ kit để khôi phục quyền quản trị.