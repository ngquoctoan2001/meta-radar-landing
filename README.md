# META RADAR · Landing page

Trang giới thiệu kênh **META RADAR – Tốc Chiến** (link gắn ở bio TikTok) — đang chạy tại **https://meta-radar-landing.pages.dev**
Mỗi trang là **1 file HTML duy nhất** — CSS, JS và ảnh nền đều nhúng sẵn bên trong, chỉ tải thêm font từ Google Fonts.

```
meta-radar-landing/
├─ public/                  ← thư mục đem đi deploy
│  ├─ index.html            ← trang chính — đã chốt Mẫu 1 · RADAR, nhúng sẵn mã QR
│  ├─ og.jpg                ← ảnh xem trước khi share link lên Facebook / Zalo (1200×630)
│  ├─ apple-touch-icon.png  ← icon khi "Thêm vào màn hình chính" trên iPhone
│  ├─ qr.jpg                ← file tải về khi bấm "Tải mã QR"
│  └─ _headers              ← báo Cloudflare trả qr.jpg dạng tải về (không mở ảnh)
├─ mau/                     ← 5 mẫu ban đầu (bản nháp trước khi chốt, không deploy — xoá được)
│  ├─ mau-1-radar.html          Link-in-bio gọn nhất · Lee Sin Nộ Long Cước
│  ├─ mau-2-anh-bia.html        Giống ảnh bìa kênh · 3 lát Lee Sin / Yasuo / Yone
│  ├─ mau-3-ban-cap-nhat.html   Như ảnh patch · nút Q W E R · True Damage Yasuo
│  ├─ mau-4-sanh-cho.html       Như sảnh game · nhiệm vụ cộng đồng · Yone Trấn Hồn Sư
│  └─ mau-5-bento.html          Lưới ô hiện đại · Jhin Vũ Trụ Hắc Ám
└─ so-sanh-5-mau.jpg        ← ảnh so sánh 5 mẫu (điện thoại + máy tính)
```

## 1. Trang chính

Đã chốt **Mẫu 1 · RADAR** → `public/index.html`. Các file trong `mau/` là bản nháp lúc chọn mẫu (nội dung cũ), giữ để tham khảo hoặc xoá đi cũng được.

## 2. Mã QR ủng hộ

- Ảnh VietQR (MB · NGUYEN QUOC TOAN) hiển thị trên trang được **nhúng thẳng trong `index.html`**.
- Nút **Tải mã QR** là link tải thẳng file `qr.jpg` (lưu về máy với tên `meta-radar-qr.jpg`), không có popup.
- Đổi QR khác: thay cả ảnh nhúng trong `index.html` lẫn file `qr.jpg` (gửi ảnh mới cho Claude làm cho nhanh).
- (Tuỳ chọn) Muốn hiện thêm dòng ngân hàng + số tài khoản kèm nút **Chép**: điền `window.UNG_HO` ở cuối file. Để trống thì tự ẩn.

Mọi chỗ nên sửa trong file đều có dấu ✏️.

## 3. Đưa lên GitHub

```bash
git init
git add .
git commit -m "Landing page META RADAR"
git branch -M main
git remote add origin https://github.com/<tai-khoan>/meta-radar-landing.git
git push -u origin main
```

## 4. Deploy lên Cloudflare Pages

1. Cloudflare Dashboard → **Workers & Pages** → **Create** → tab **Pages** → **Connect to Git** → chọn repo vừa tạo.
2. Cấu hình build:
   - Framework preset: **None**
   - Build command: *(để trống)*
   - Build output directory: **`public`**
3. **Save and Deploy** → có link dạng `https://<ten-du-an>.pages.dev`. Từ giờ mỗi lần `git push` là Cloudflare tự cập nhật.

Không muốn dùng Git: ở bước 1 chọn **Upload assets** rồi kéo thả cả thư mục `public/` vào cũng được.

## 5. Sau khi có link

- **Ảnh xem trước khi share link**: đã gắn sẵn cho `https://meta-radar-landing.pages.dev` (thẻ `og:*` + `canonical` trong `<head>`). Đổi sang tên miền riêng thì sửa các link đó. Facebook còn hiện ảnh cũ thì vào [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) bấm **Scrape Again**.
- **Đếm lượt vào**: trong project Pages → **Metrics** → bật **Web Analytics** (miễn phí, không cần cookie) để biết bao nhiêu người bấm từ bio TikTok.
- **Gắn vào TikTok**: Hồ sơ → Sửa hồ sơ → **Trang web**. Nếu chưa thấy ô này thì tài khoản chưa đủ điều kiện (TikTok thường yêu cầu tài khoản Doanh nghiệp hoặc đủ số follower).
- **Tên miền riêng**: project Pages → **Custom domains** → thêm tên miền.

## Đổi thông tin nhanh

| Muốn đổi | Tìm trong `index.html` |
|---|---|
| Link TikTok | `tiktok.com/@meta.radar` |
| Link Facebook | `facebook.com/metaradar.wildrift` |
| Số Zalo | `0867804787` (link + nút chép) và `0867 804 787` (chữ hiển thị) |
| Ảnh nền | khối `<style id="anh-nhung">` cuối `<head>` (ảnh base64 — nhờ Claude đổi skin cho nhanh) |

Hình ảnh trang phục © Riot Games. META RADAR là kênh cộng đồng, không liên kết với Riot Games.
