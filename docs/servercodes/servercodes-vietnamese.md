# Mã Máy Chủ
Tài liệu này có sẵn bằng các ngôn ngữ sau: [English](servercodes-english.md), [简体中文](placeholder), [日本語](placeholder), [Tiếng Việt](servercodes-vietnamese.md)

Pineapple cung cấp một trình theo dõi mã máy chủ cho trò chơi trực tuyến [florr.io](https://florr.io) có thể hữu ích khi săn các quái Siêu Đẳng hoặc tìm máy chủ để cày. Sau đây là tổng quan về những chức năng của nó.

## Trình Theo Dõi Máy Chủ
Lệnh cơ bản của trình theo dõi máy chủ có thể được truy cập bằng `.servers`, viết tắt là `.sv`. Cú pháp lệnh là `.servers (map)`. Nếu bạn thích dùng các lệnh gạch chéo trong máy chủ của bạn, bạn cũng có thể truy cập tiện ích này bằng `/servercodes servers`, viết tắt là `/servers`. Có một số phím tắt cho các bản đồ khác nhau, được nêu dưới đây:
```
g → Khu Vườn
d → Sa Mạc
o → Đại Dương
j → Rừng Rậm
ah → Địa Ngục Kiến
h → Địa Ngục
sw → Cống Rãnh
bg → Chiến Trường
all → Tất Cả Máy Chủ
```
Lệnh này trả về mã máy chủ của tất cả các máy chủ nếu không có đối số nào được truyền vào hoặc `all` được chỉ định. Lệnh gạch chéo tương đương cũng có các lựa chọn qua Discord, nghĩa là bạn không bị giới hạn ở các phím tắt này và ứng dụng Discord của bạn sẽ thực hiện tốt nhất công việc của mình để suy ra bản đồ nào bạn đang cố gắng lựa chọn.

Mã máy chủ được cung cấp với mã lệnh `cp6.forceServerID` được điền sẵn và có nút sao chép ở góc hộp mã để dễ sao chép. Kể từ Pineapple v5.0.0, mã lệnh này có thể được dán trực tiếp vào Bảng Điều Khiển của florr.io; nó không còn chứa dữ liệu ANSI để tô màu văn bản nữa.

### Cảnh Báo Máy Chủ
Pineapple cũng theo dõi một số thuộc tính nhất định của máy chủ và chú thích vào mã lệnh `cp6.forceServerID` để đưa chúng vào khi cần.

| Cảnh Báo | Nghĩa |
| --- | --- |
| `CRASHED` | Máy chủ này đang ở phiên bản mà không tải đúng cách. Kết nối đến máy chủ này có thể sẽ rất có thể không thành công. |
| `REVERTED` | Máy chủ này đang ở phiên bản đã được hoàn nguyên, rất có thể đã xảy ra lỗi. Có thể kết nối với máy chủ này bằng cách buộc bạn phải vào. |
| `OLD` | Máy chủ này đang sử dụng phiên bản cũ và do đó không thể kết nối trực tiếp. Có thể kết nối với máy chủ này bằng cách buộc bạn phải vào. |
| `FULL` | Máy chủ này không thể kết nối được. Điều này rất có thể là do nó đã đầy, nhưng điều này đôi khi có thể xảy ra khi máy chủ thứ 2 hết hạn và ngừng hoạt động. |

Cảnh báo được hiển thị trong UI dưới dạng bình luận bên cạnh mã lệnh force-server, chẳng hạn như `cp6.forceServerID('code') // OLD`. Khi những bình luận này tồn tại, bạn không cần phải xóa bình luận khỏi mã lệnh. Theo mặc định, Bảng Điều Khiển của JavaScript sẽ bỏ qua cảnh báo.

![image](https://github.com/user-attachments/assets/ebcb4c34-a507-4adf-b18f-7b3078903c14)
| Vị trí | Nghĩa |
| --- | --- |
| `A` | Bản đồ mà lệnh đang cung cấp. |
| `B` | Nút sao chép (xuất hiện khi di chuột). |
| `C` | Mã máy chủ nguyên. |
| `D` | Lệnh buộc máy chủ (xem [Buộc Máy Chủ](#forcing-servers)). |

### Buộc Máy Chủ
#### Máy Chủ Hiện Tại
Có thể buộc máy chủ hiện tại bằng cách chạy mã lệnh `cp6.forceServerID` trong Bảng Điều Khiển JavaScript. Bạn có thể thực hiện việc này theo nhiều cách, nhưng cách phổ biến nhất là sử dụng Bảng Điều Khiển dành cho nhà phát triển ([Chrome & Chromium](https://developer.chrome.com/docs/devtools/open), [Safari](https://developer.apple.com/library/archive/documentation/NetworkingInternetWeb/Conceptual/Web_Inspector_Tutorial/EnableWebInspector/EnableWebInspector.html)).

Một cách nhanh hơn để thực hiện việc này mà không cần mở Công cụ dành cho nhà phát triển là chạy JavaScript trực tiếp trên thanh địa chỉ, loại bỏ việc mở Bảng Điều Khiển. Trên Chrome, chỉ cần thêm `javascript:` vào lệnh force-server, do đó hãy nhập `javascript:cp6.forceServerID('code')` vào thanh địa chỉ. Điều này yêu cầu bạn phải có quyền truy cập Bảng Điều Khiển và phải **gõ thủ công** phần `javascript:` của lệnh (đây là [tính năng bảo mật](https://stackoverflow.com/questions/7698009/why-is-javascript-pseudo-protocol-stripped-from-url-bar-when-pasted) trên Chrome). Đây cũng là lý do tại sao bot không đưa ra mã lệnh có `javascript:` đã được thêm vào trước.

#### Máy Chủ Cũ và Đã Hoàn Nguyên
Bạn có thể buộc vào các máy chủ cũ hoặc máy chủ đã hoàn nguyên bằng cách spam lệnh force-server **trong khi kết nối với bản đồ tương ứng trong phiên bản mới**. Thao tác này sẽ tải lại trang của bạn khi bạn được chuyển đến phiên bản trò chơi khác, bạn nên tiếp tục spam lệnh cho đến khi nút `Ready` xuất hiện. Lưu ý rằng sau một thời gian, các máy chủ cũ và đã hoàn nguyên sẽ đóng, vì vậy thông thường, bạn chỉ có thể kết nối với các máy chủ này trong vòng vài phút sau khi phiên bản trò chơi mới được đưa lên. Video hướng dẫn được đính kèm bên dưới.

![video](https://github.com/user-attachments/assets/ea61d092-31fa-4ff0-855b-0e6eae6ee8a4)
