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
javascript:(()=>{if(!location.href.includes("dkmh.hcmute.edu.vn"))return void alert("B\u1EA1n h\xE3y \u0111\u0103ng nh\u1EADp v\xE0o trang dkmh.hcmute.edu.vn tr\u01B0\u1EDBc khi ch\u1EA1y script n\xE0y");if(null==document.querySelector("#id_menu2"))return void alert("H\xE3y \u0111\u0103ng nh\u1EADp tr\u01B0\u1EDBc khi ch\u1EA1y script");let a=prompt("Nh\u1EADp n\u0103m b\u1EAFt \u0111\u1EA7u h\u1ECDc v\xE0 h\u1ECDc k\xEC.\nV\xED d\u1EE5: n\u0103m h\u1ECDc l\xE0 2021-2022 v\xE0 \u0111ang l\xE0 k\xEC 2 th\xEC nh\u1EADp 212",localStorage.getItem("term")??"");if(null==a||""==a)return;localStorage.setItem("term",a);let b=prompt("Nh\u1EADp m\xE3 m\xF4n h\u1ECDc. N\u1EBFu nh\u1EADp nhi\u1EC1u m\xF4n th\xEC ph\xE2n c\xE1ch nhau b\u1EB1ng kho\u1EA3ng tr\u1EAFng. V\xED d\u1EE5: ADNT330580 ADPL331379");if(null!=b&&""!=b){b=b.replace(/\s+/g," ").trim().split(" ");for(let c=0;c<b.length;c++)PopupDanhSachLop(a+b[c],b[c])}})();
```

## Sử dụng

Sau khi hoàn thành các bước trên thì bạn chỉ cần vào `Đăng nhập` vào trang [Đăng Kí Môn Học](https://dkmh.hcmute.edu.vn/) và click vào bookmark bạn vừa thêm sẽ xuất hiện 1 hộp thoại.

* Nhập năm bắt đầu học và học kì. **Ví dụ: nếu năm học là 2021-2022 và đang là kì 2 thì nhập 212**

* Nhập mã môn học. Nếu nhập nhiều môn thì phân cách nhau bằng khoảng trắng. **Ví dụ: ADNT330580 ADPL331379**

**Chúc các bạn đăng kí môn học thành công 👍**
