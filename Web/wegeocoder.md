# WeGeocoder

Plugin Geocoding API cho bản đồ WeMap GL JS.  

Các tính năng nổi bật:   

- Khung hiển thị danh sách kết quả tìm kiếm trực quan và được sắp xếp
- Nút chuyển đổi giữa hai tính năng tìm kiếm và chỉ đường  
- Khung hiển thị thông tin chi tiết của một kết quả tìm kiếm  

## Các tham số

- `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 
    - `options.key` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)**  Plugin sẽ sử dụng key này để sử dụng API tìm kiếm.
    - `options.engine` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Engine tìm kiếm. Các lựa chọn: `default`, `pelias`. (Mặc định là `default`)
    - `options.suggestion` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** `{min_char: <number>}` Số ký tự tối thiểu để bắt đầu tính năng auto-complete.
    - `options.removeDuplicates` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Loại bỏ trùng lặp dựa trên toạ độ.
    - `options.flyTo` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** Chọn Fly-to hoặc Jump-to khi kết quả được chọn. Các lựa chọn: `true`, `false`, `hybrid`
    - `options.url` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Url của máy chủ Geocoder.
    - `options.placeholder` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Tuỳ biến placeholder của phần tử input.
    - `options.params` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** Các tham số tuỳ chọn để thêm vào request.
    - `options.sources` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)** hoặc **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Chọn các nguồn cụ thể để request. Các lựa chọn: `oa`, `osm`, `wof`, `gn`
    - `options.onSubmitOnly` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Gửi request chỉ khi ấn phím Enter.
    - `options.marker` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** or **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Add marker to show results. Thêm marker khi hiển thị các kết quả. Marker phải nằm trong các sprite kiểu dáng của bạn.
    - `options.wof` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** or **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Thêm polygon cho các đối tượng vị trí từ wof.
    - `options.customAttribution` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Thêm bản quyền tuỳ ý (CÓ thể là mã HTML).

### Ví dụ
```javascript
// định nghĩa
var geocoder = new wemapgl.WeGeocoder({
        flyTo: 'hybrid',
        key: 'YOUR-WEMAP-KEY-HERE',
        engine: 'default',
        suggestion: {
            min_char: 4
        }
});
// thêm vào bản đồ
map.addControl(geocoder);
```

Trả về **[WeGeocoder](#wegeocoder)** `this`