# ĐKMH-UTE
> Script nhỏ hỗ trợ đăng kí môn học nhanh **hơn chút xíu**
> 
> **Lưu ý: script này chỉ đăng kí được các môn ở trong phần `Đăng kí ngoài kế hoạch`**

## Chuẩn bị
> Ở đây mình hướng dẫn cho trình duyệt Edge. Tuy vậy nhưng các bước cũng rất giống trên các trình duyệt khác

### Tạo Bookmark

Vào bất cứ trang web nào sau đó nhìn lên góc cuối phía bên phải của thanh địa chỉ sẽ thấy hình ngôi sao. Click vào và nhấn `Done`
   
### Chỉnh sửa Bookmark

> Lưu ý: Nếu không thấy dưới thanh địa chỉ có gì mới xuất hiện thì vào `Setting` tìm chỗ `Show favories bar` và chọn `Always`

Sau khi tạo xong bookmark sẽ thấy bên dưới thanh địa chỉ xuất hiện tên và biểu tượng của trang vừa thêm. 
   
Chuột phải vào nó và chọn `Edit`. Lúc này sẽ xuất hiện 1 hộp thoại.

   * Mục `Name` ghi tùy ý

   * Mục `URL` xóa tất cả và pass đoạn code dưới đây vào và nhấn `Done`
```javascript
javascript:(() => { if (!location.href.includes("dkmh.hcmute.edu.vn")) return void alert("Bạn hãy đăng nhập vào trang dkmh.hcmute.edu.vn trước khi chạy script này"); if (null == document.querySelector("#id_menu2")) return void alert("Hãy đăng nhập trước khi chạy script"); let n = prompt("Nhập năm bắt đầu học và học kì.\nVí dụ: năm 2021, kì 2 thì nhập 212"); if (null == n || "" == n) return; let h = prompt("Nhập mã môn học. Nếu nhập nhiều môn thì phân cách nhau bằng khoảng trắng"); if (null == h || "" == h) return; h =  h.replace(/\s+/g, " ").trim().split(" "); for (let e = 0; e < h.length; e++) PopupDanhSachLop(n + h[e], h[e]) })();
```

## Sử dụng

Sau khi hoàn thành các bước trên thì bạn chỉ cần vào `Đăng nhập` vào trang [Đăng Kí Môn Học](https://dkmh.hcmute.edu.vn/) và click vào bookmark bạn vừa thêm.

**Chúc các bạn đăng kí môn học thành công 👍**
