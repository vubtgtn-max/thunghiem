# Hồ sơ tổng hợp – UBND xã Lãnh Ngọc

Ứng dụng web chạy ngay trên trình duyệt (một file `index.html`, không cần máy chủ) để nhập một lần dữ liệu hồ sơ đất đai và xuất các biểu mẫu Word: thừa kế, hồ sơ đất đai, niêm yết GCN, xử phạt VPHC và **chuyển mục đích sử dụng đất (Tờ trình, Quyết định)**.

Phiên bản hiện tại: **v1.8.1**

## Đưa lên GitHub Pages (dùng chung cho nhiều máy)

1. Đăng nhập GitHub, chọn **New repository**, đặt tên (ví dụ `ho-so-lanh-ngoc`), chọn **Public**, bấm **Create repository**.
2. Bấm **uploading an existing file**, kéo thả hai file `index.html` và `README.md` vào, bấm **Commit changes**. (File `.nojekyll` đã có sẵn trong gói; nếu GitHub không cho tải file bắt đầu bằng dấu chấm thì bỏ qua, không ảnh hưởng.)
3. Vào **Settings → Pages**. Ở mục *Build and deployment*, chọn **Deploy from a branch**, nhánh **main**, thư mục **/ (root)**, bấm **Save**.
4. Đợi 1–2 phút, mở đường dẫn GitHub hiển thị ở đầu trang Pages (dạng `https://<tên-tài-khoản>.github.io/ho-so-lanh-ngoc/`) bằng **Chrome hoặc Edge**.
5. Gửi đường dẫn này cho các máy cùng dùng. Cập nhật phiên bản mới: vào kho, chọn `index.html` → biểu tượng bút chì hoặc **Add file → Upload files** để ghi đè.

> **Quan trọng – dữ liệu cá nhân:** kho GitHub Pages miễn phí là kho công khai. Chỉ đưa **file ứng dụng** lên kho. **Không** tải lên kho bất kỳ hồ sơ, ảnh CCCD, file scan, file `.json` sao lưu nào.

## Dữ liệu được lưu ở đâu

- Dữ liệu hồ sơ và tệp đính kèm lưu **ngay trong trình duyệt của từng máy** (không gửi lên GitHub hay máy chủ nào).
- Mỗi máy/trình duyệt có dữ liệu riêng. Chuyển hồ sơ giữa các máy bằng **Xuất .json** rồi **Nhập .json** (file `.json` chứa dữ liệu cá nhân – chỉ gửi qua kênh nội bộ).
- Xóa dữ liệu duyệt web hoặc dùng chế độ ẩn danh sẽ làm mất hồ sơ chưa sao lưu. Hãy sao lưu thường xuyên.

## Tab Chuyển mục đích (6)

- Dùng chung người sử dụng đất và thửa đất ở tab 1 · Data (chọn chế độ nhập *6 · Chuyển mục đích*).
- Nhập thêm: diện tích chuyển, loại đất sau chuyển, hành lang giao thông, tỷ lệ sử dụng, nguồn gốc theo tờ khai, số và ngày Trích lục / Tờ trình / Quyết định (để trống thì file Word chừa chỗ điền tay).
- Cảnh báo tự động: chuyển nhiều hơn diện tích thửa, phần ngoài hành lang không đủ, nguồn gốc đất khác nhau giữa GCN và tờ khai, thiếu tỷ lệ khi nhiều người, CCCD không đủ 12 số, đất trồng lúa, thửa đã có đất ở, ngày ký sau 28/02/2027.
- Xuất Tờ trình và Quyết định (.docx) theo thể thức Nghị định 30/2020/NĐ-CP.
- **Cần kiểm tra trước khi trình ký:** người ký, nơi nhận, danh sách căn cứ pháp lý và đoạn "phù hợp quy hoạch, khu dân cư hiện trạng" là nội dung cố định trong khuôn. Quyết định 91/2026/QĐ-UBND chỉ có hiệu lực đến hết 28/02/2027 – xem lại căn cứ khi hết hạn.

## Tab Tệp & trích xuất (8)

1. Tải tệp của hồ sơ lên (PDF hoặc ảnh).
2. Bấm **Đọc tất cả tệp**: app bỏ trang trắng, nhận dạng loại giấy tờ (đơn, GCN, CCCD, tờ khai tiền sử dụng đất, tờ khai trước bạ, tờ khai PNN), đọc QR CCCD, chữ trong PDF và OCR cho trang scan.
3. Xem **bảng đối chiếu** giữa các giấy tờ, tích "đã xác nhận".
4. Bấm **Điền vào hồ sơ…**, kiểm tra từng dòng trong hộp duyệt rồi xác nhận.
5. Mục "Chữ app đọc được từng trang" giúp kiểm tra khi đọc sai.

Lưu ý:
- OCR chỉ chạy khi app nằm trên GitHub Pages (hoặc mở `index.html` từ máy bằng Chrome/Edge) và cần Internet ở lần đầu để tải dữ liệu OCR. Trong khung xem trước của Claude, OCR bị chặn.
- Chữ viết tay (nhất là ghi chú biến động ở mục IV của GCN) và ảnh mờ đọc kém – luôn đối chiếu bản gốc. Scan từ 200 dpi trở lên cho kết quả tốt hơn.
- Có thể dùng nút **Dán kết quả đọc (JSON)** để nạp kết quả đã trích bằng công cụ khác.

## OCR không chạy được – cách xử lý

Bấm **🩺 Kiểm tra kết nối OCR** (tab Tệp & trích xuất). App thử tải từng tệp OCR từ 4 nguồn (thư mục `ocr/` của app, jsDelivr, unpkg, cdnjs/projectnaptha) và báo nguồn nào được, nguồn nào bị chặn. App tự dùng nguồn nào chạy được. Nếu mạng của xã chặn mọi nguồn CDN, đặt 4 tệp sau vào thư mục `ocr/` ngay cạnh `index.html` trong kho GitHub (tải về từ máy có Internet rồi tải lên):

- `tesseract.min.js` – https://cdn.jsdelivr.net/npm/tesseract.js@5.1.1/dist/tesseract.min.js
- `worker.min.js` – https://cdn.jsdelivr.net/npm/tesseract.js@5.1.1/dist/worker.min.js
- `tesseract-core-simd-lstm.wasm.js` (và `tesseract-core-lstm.wasm.js` cho máy cũ) – https://cdn.jsdelivr.net/npm/tesseract.js-core@5.1.0/
- `vie.traineddata.gz` – https://cdn.jsdelivr.net/npm/@tesseract.js-data/vie/4.0.0_best_int/vie.traineddata.gz

(Tên tệp có thể khác theo phiên bản – dùng nút kiểm tra để xác nhận app tìm thấy tệp.) Khi OCR lỗi, app hiện nguyên văn lỗi của từng nguồn; chép nội dung đó (hoặc kết quả bảng kiểm tra kết nối) để được hỗ trợ.

## Sự cố thường gặp

| Hiện tượng | Cách xử lý |
|---|---|
| "OCR không chạy được… khung đang mở app chặn bộ OCR" | Mở app bằng đường dẫn GitHub Pages hoặc mở file từ máy bằng Chrome/Edge, không mở trong khung xem trước. |
| Không tải được thư viện | Cần Internet ở lần đầu (OCR, đọc PDF). Kiểm tra mạng hoặc tường lửa chặn `cdnjs.cloudflare.com`, `cdn.jsdelivr.net`. |
| Mở file thấy trống / không lưu được tệp | Không dùng chế độ ẩn danh; dùng Chrome/Edge mới. |
| Mất hồ sơ | Dữ liệu nằm trong trình duyệt – khôi phục bằng file `.json` đã sao lưu. |

## Ghi chú phiên bản

- **v1.8.1**: OCR thử nhiều nguồn (thư mục `ocr/`, jsDelivr, unpkg, cdnjs), hiện lỗi thật của từng nguồn, thêm nút kiểm tra kết nối OCR; tự thử chế độ không dùng bộ nhớ đệm.
- **v1.8.0**: bộ đọc hồ sơ chịu được lỗi OCR (nhãn gần đúng, bám mã [NN] của tờ khai, bỏ chữ rác); chuẩn hóa loại đất theo danh mục (không còn chép chữ OCR lỗi vào văn bản); thêm trường GCN (số vào sổ, cơ quan cấp, diện tích/mục đích/địa chỉ ghi trên GCN, tờ bản đồ cũ, số trích đo, vị trí thửa) và điện thoại; đọc tỷ lệ sở hữu; ưu tiên dữ liệu QR/CCCD; hộp duyệt hiện cảnh báo từng trường; tab Chuyển mục đích hỏi lại trước khi xuất nếu thiếu hoặc loại đất không hợp lệ; chẩn đoán rõ khi OCR chưa chạy.

- **v1.7.0**: đọc toàn bộ hồ sơ, nhận dạng theo loại giấy tờ, bảng đối chiếu, chẩn đoán chữ đọc được, dán kết quả JSON.
- **v1.6.0**: thêm tab Chuyển mục đích (Tờ trình, Quyết định) và cảnh báo số liệu; căn cứ có Quyết định 91/2026 và 135/2026/QĐ-UBND.
