# Key Card Match - Custom Grid

Một ứng dụng web đơn file (`index.html`), tương tự [keycardmatch.netlify.app](https://keycardmatch.netlify.app/), có thêm phần **cấu hình thẻ (cards)**: bạn có thể tạo thêm thẻ mới với **màu nền tuỳ chọn** và/hoặc **icon** lấy từ **Font Awesome Free** (qua CDN).

## Tính năng

- Chỉnh số dòng (Rows) / cột (Cols), bấm **Apply** để cập nhật lưới (tối đa 20x20).
- Bộ 9 thẻ mặc định giống bản gốc (gem, anchor, music, drink, sailboat, wheel, movie, magic, search).
- **Thêm thẻ mới** (nút `+ Card`):
  - Chọn **kiểu thẻ**: chỉ Màu / chỉ Icon / Cả hai.
  - Chọn màu nền bằng color picker hoặc nhập mã hex.
  - Chọn icon từ thư viện icon dựng sẵn (Font Awesome Free Solid) hoặc gõ trực tiếp class FA (ví dụ `fa-solid fa-anchor`) để dùng bất kỳ icon free nào.
  - Chọn màu icon riêng.
  - Xem trước thẻ trước khi lưu.
- **Chỉnh sửa / xoá** thẻ bất kỳ (bấm icon bút chì khi hover vào thẻ).
- Nút khôi phục bộ thẻ mặc định.
- Kéo-thả (drag & drop) thẻ vào ô lưới. Trên di động: bấm chọn thẻ rồi bấm vào ô để đặt.
- Bấm vào ô để gạch chéo + xoá thẻ; bấm lại để xoá dấu gạch; bấm đúp để xoá hoàn toàn ô.
- Chế độ **Sáng / Tối** (góc phải trên).
- Tự động lưu toàn bộ cấu hình (thẻ, kích thước lưới, trạng thái các ô, theme) vào `localStorage` của trình duyệt — refresh trang không bị mất dữ liệu.

Toàn bộ code, biến và comment trong file đều bằng tiếng Anh theo yêu cầu; chỉ phần văn bản hiển thị cho người dùng là tiếng Việt.

## Cách deploy lên Netlify

### Cách 1: Kéo-thả (nhanh nhất, không cần Git)

1. Vào [https://app.netlify.com](https://app.netlify.com) và đăng nhập.
2. Vào mục **Sites** → kéo thả **thư mục chứa file `index.html`** (chỉ cần file này, không cần file nào khác) vào vùng "Drag and drop your site output folder here".
3. Netlify sẽ build và cấp cho bạn 1 URL dạng `https://random-name-123.netlify.app`.
4. (Tuỳ chọn) Vào **Site settings → Change site name** để đổi tên URL.

### Cách 2: Qua Git (GitHub/GitLab/Bitbucket) — dễ cập nhật sau này

1. Tạo một repository mới, đẩy (push) file `index.html` (và `README.md` nếu muốn) lên.
2. Vào Netlify → **Add new site → Import an existing project** → chọn repo vừa tạo.
3. Vì đây chỉ là 1 file HTML tĩnh, **không cần build command**, để **Publish directory** là `.` (thư mục gốc, nơi chứa `index.html`).
4. Bấm **Deploy site**.

### Cách 3: Netlify CLI

```bash
npm install -g netlify-cli
cd thu-muc-chua-index-html
netlify deploy --prod
```

## Lưu ý

- Icon dùng từ CDN Font Awesome Free 6.5.2 (`cdnjs.cloudflare.com`), không cần API key. Bạn có thể nhập bất kỳ class icon **Free** nào (solid `fa-solid`, regular `fa-regular`, brands `fa-brands`) ở ô "nhập class FA" trong khung Thêm/Sửa thẻ — chỉ những icon thuộc gói **Free** mới hiển thị được mà không cần Pro Kit.
- Dữ liệu lưu trong `localStorage` là **riêng theo từng trình duyệt/thiết bị**, không đồng bộ giữa nhiều người dùng. Nếu cần chia sẻ cấu hình thẻ giữa nhiều người, có thể export/import thủ công nội dung `localStorage` (key: `kcm_state_v1`) qua DevTools.
