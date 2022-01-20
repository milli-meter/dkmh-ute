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
javascript:(() => { if (!location.href.includes("dkmh.hcmute.edu.vn")) return void alert("Bạn hãy đăng nhập vào trang dkmh.hcmute.edu.vn trước khi chạy script này"); if (null == document.querySelector("#id_menu2")) return void alert("Hãy đăng nhập trước khi chạy script"); let n = prompt("Nhập năm bắt đầu học và học kì.\nVí dụ: năm học là 2021-2022 và đang là kì 2 thì nhập 212"); if (null == n || "" == n) return; let h = prompt("Nhập mã môn học. Nếu nhập nhiều môn thì phân cách nhau bằng khoảng trắng. Ví dụ: ADNT330580 ADPL331379"); if (null == h || "" == h) return; h =  h.replace(/\s+/g, " ").trim().split(" "); for (let e = 0; e < h.length; e++) PopupDanhSachLop(n + h[e], h[e]) })();
```

## Sử dụng

Sau khi hoàn thành các bước trên thì bạn chỉ cần vào `Đăng nhập` vào trang [Đăng Kí Môn Học](https://dkmh.hcmute.edu.vn/) và click vào bookmark bạn vừa thêm sẽ xuất hiện 1 hộp thoại.

* Nhập năm bắt đầu học và học kì. **Ví dụ: nếu năm học là 2021-2022 và đang là kì 2 thì nhập 212**

* Nhập mã môn học. Nếu nhập nhiều môn thì phân cách nhau bằng khoảng trắng. **Ví dụ: ADNT330580 ADPL331379**

**Chúc các bạn đăng kí môn học thành công 👍**

## Bonus
> Chức năng của code dưới đây là bạn nhập mã lớp học phần như là ADNT330580_01CLC thì nó đăng kí lớp này luôn cho bạn, khác với code trên là bạn chỉ nhập mã môn học và phải chọn lớp
>
> Lưu ý: code này chưa test kĩ 

```javascript
javascript: (() => {if (!location.href.includes("dkmh.hcmute.edu.vn")) return void alert("Bạn hãy đăng nhập vào trang dkmh.hcmute.edu.vn trước khi chạy script này"); if (null == document.querySelector("#id_menu2")) return void alert("Hãy đăng nhập trước khi chạy script"); let n = prompt("Nhập năm bắt đầu học và học kì.\nVí dụ: năm học 2021-2022, kì 2 thì nhập 211"); if (null == n || "" == n) return; let h = prompt("Nhập mã lớp học phần. Nếu nhập nhiều môn thì phân cách nhau bằng khoảng trắng. Ví dụ: ADNT330580_01CLC ADPL331379_03CLC"); if (null == h || "" == h) return; h = h.replace(/\s+/g, " ").trim().split(" "); for (let e = 0; e < h.length; e++) { getTrangChonMonHoc({ full: n + h[e].split("_")[0], curriculum: h[e].split("_")[0] }).then(text => { let domParser = new DOMParser(); let domParseString = domParser.parseFromString(text); let studyUnitID = domParseString.querySelector('#StudyUnitID').value let curriculumID = domParseString.querySelector('#CurriculumID').value let hdID, name let rows = domParseString.querySelectorAll('.trhover') let found = false; let danhsachhocphan = []; for (row of rows) { if (!row.querySelector('.classCheckChon').disabled) { if (found) break; let cells = row.querySelectorAll('td') danhsachhocphan.push(cells[2]) for (cell of cells) { if (cell.innerText == h[e]) { hdID = row.querySelector('.classCheckChon').id + '|' name = row.querySelector('.classCheckChon').name found = true; break; } } } } if (found) { postDangKiMonHoc({ name: name, curriculumID: curriculumID, studyUnitID: studyUnitID, hdID: hdID }).then(response => { console.log(response) if (response.url.includes('Login')) alert('Vui lòng đăng nhập lại') }).catch(error => { console.log(error) }) } else alert('Không tìm thấy học phần phù hợp, danh sách học phần có sẵn: ', danhsachhocphan.toString()) }) } async function getTrangChonMonHoc(pararam) { url = '/DangKiNgoaiKeHoach/DanhSachLopHocPhan/' + pararam.full + '?CurriculumID=' + pararam.curriculum + '&t=' + Math.random() let response = await fetch(url, { method: 'GET', credentials: 'same-origin', }); return response.text() } async function postDangKiMonHoc(data = {}) { return response = await fetch('/DangKiNgoaiKeHoach/DanhSachLopHocPhanPost?Length=18', { method: 'POST', credentials: 'same-origin', headers: { 'Content-Type': 'application/x-www-form-urlencoded' }, redirect: 'follow', body: new URLSearchParams({ 'CurriculumID': data.curriculumID, 'StudyUnitID': data.studyUnitID, 'hdID': data.hdID, [data.name]: 'on' }) }); }})();
```
