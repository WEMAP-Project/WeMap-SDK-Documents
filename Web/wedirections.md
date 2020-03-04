# WeDirections

Plugin điều khiển chỉ đường cho bản đồ WeMap GL JS.  

Các tính năng nổi bật:  

- Cho phép lựa chọn engine chỉ đường
- Bật / Tắt tính năng reverse, nút chuyển sang tìm kiếm, hoán đổi điểm bắt đầu và điểm đến
- Tìm kiếm điểm bắt đầu và kết thúc bằng tên, toạ độ ...

### Các tham số khởi tạo

-   `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 
    - `options.key` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Plugin sẽ sử dụng key này để sử dụng API chỉ đường.
    - `options.engine` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Chỉ định dịch vụ tìm đường được sử dụng. Các lưạ chọn: `default`, `osrm`, `graphhopper`, `mapbox`. (tuỳ chọn, mặc định là `default`, tương đương với `osrm`)
    -   `options.styles` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)?** Ghi đè các thuộc tính của lớp mặc định của plugin. Tài liệu cho từng thuộc tính được mô tả tại [Tham khảo về Kiểu dáng của WeMap GL](#).
    -   `options.interactive` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Bật/Tắt tính năng tương tác bằng chuột hoặc cảm ứng từ plugin (tuỳ chọn, mặc định là `false`)
    -   `options.mode` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Cấu hình chỉ đường được sử dụng. Các lựa chọn: `traffic`, `driving`, `walking`, `cycling` (tuỳ chọn, mặc định là `"driving"`)
    -   `options.alternatives` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Bật hoặc tắt tính năng đường đi tương tự. (tuỳ chọn, mặc định là `false`)
    -   `options.congestion` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Bật hoặc tắt tính năng tắc nghẽn trên đường đi. (tuỳ chọn, mặc định là `false`)
    -   `options.unit` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Hệ đo lường được sử dụng trong hướng dẫn chỉ đường. Các lựa chọn: `imperial`, `metric` (tuỳ chọn, mặc định là `"metric"`)
    -   `options.compile` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)** Đưa vào một hàm để tạo ra hướng dẫn chỉ đường, tương thích với osrm-text-instructions. (tuỳ chọn, mặc định là `null`)
    -   `options.geocoder` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** Nhận một đối tượng chứa các tham số truy vấn được [mô tả tại đây](https://www.mapbox.com/api-documentation/#search-for-places). Mặc định là `"default"`, tương đương với `"pelias"`.
    -   `options.controls` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** 
        -   `options.controls.inputs` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Ẩn hoặc hiển thị các khung đầu vào. (tuỳ chọn, mặc định là `true`)
        -   `options.controls.instructions` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Ẩn hoặc hiển thị khung hướng dẫn chỉ đường. (tuỳ chọn, mặc định là `true`)
        -   `options.controls.profileSwitcher` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Ẩn hoặc hiển thị bộ chuyển đổi giữa các cấu hình chỉ đường mặc định với các lựa chọn cho mật độ phương tiện, lái xe, đi bộ và phương tiện hai bánh. (tuỳ chọn, mặc định là `true`)
    -   `options.zoom` **[Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** Nếu không có bbox tồn tại trong kết quả trả về từ geocoder, độ phóng đại được đặt ở đây sẽ được sử dụng cho tính năng flyTo. (tuỳ chọn, mặc định là `16`)
    -   `options.placeholderOrigin` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Nếu được đặt, chuỗi ký tự này sẽ là thuộc tính placeholder cho phần tử input của điểm bắt đầu. (tuỳ chọn, mặc định là `"Chọn điểm bắt đầu"`)
    -   `options.placeholderDestination` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Nếu được đặt, chuỗi ký tự này sẽ là thuộc tính placeholder cho phần tử input của điểm đến. (tuỳ chọn, mặc định là `"Chọn điểm kết thúc"`)
    -   `options.flyTo` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Nếu `false`, tắt đi tính năng hoạt ảnh bản đồ tới một kết quả được chọn. (tuỳ chọn, mặc định là `true`)
    -   `options.exclude` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Bỏ đi một loại đường ra khỏi tuyến đường. Các lựa chọn: `ferry`, `toll`, `motorway` (tuỳ chọn, mặc định là `null`)

**Ví dụ**

```javascript
// định nghĩa plugin
var directions = new WeDirections({
  key: 'YOUR-WEMAP-ACCESS-TOKEN',
});
// thêm plugin vào bản đồ
map.addControl(directions);
```

Trả về **[WeDirections](#wedirections)** `this`

### Các hàm
---

### onRemove

Xoá bộ điều khiển từ bản đồ mà nó đã được thêm vào. Được gọi bởi `map.removeControl`, là phương thức được khuyến khích để loại bỏ các bộ điều khiển.

**Các tham số**

-   `map`  

Trả về **Control** `this`

### interactive

Bật hoặc tắt sự tương tác

**Các tham số**

-   `state` **[Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** đặt sự tương tác dựa trên một trạng thái `true` hoặc `false`.

Trả về **[WeDirections](#wedirections)** `this`

---

### getOrigin

Trả về điểm bắt đầu của tuyến đường hiện tại.

Trả về **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** `origin`

---

### setOrigin

Đặt điểm bắt đầu. _Chú ý:_ lời gọi phương thức này yêu cầu [sự kiện tải bản đồ](https://www.mapbox.com/mapbox-gl-js/api/#Map.load)
để có thể khởi chạy.

**Các tham số**

-   `query` **([Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)> | [String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String))** Một mảng của toạ độ [lng, lat] hoặc chuỗi ký tự thể hiện một địa điểm.

Trả về **[WeDirections](#wedirections)** `this`

---

### getDestination

Trả về điểm đến của tuyến đường hiện tại.

Trả về **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** `destination`

---

### setDestination

Đặt điểm đến. _Chú ý:_ lời gọi phương thức này yêu cầu [sự kiện tải bản đồ](https://www.mapbox.com/mapbox-gl-js/api/#Map.load)
để có thể khởi chạy.

**Các tham số**

-   `query` **([Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)> | [String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String))** Một mảng của toạ độ [lng, lat] hoặc chuỗi ký tự thể hiện một địa điểm.

Trả về **[WeDirections](#wedirections)** `this`


---

### reverse

Hoán đổi điểm bắt đầu và điểm đến.

Trả về **[WeDirections](#wedirections)** `this`


---

### addWaypoint

Thêm điểm ghé qua vào tuyến đường. _Chú ý:_ lời gọi phương thức này yêu cầu [sự kiện tải bản đồ](https://www.mapbox.com/mapbox-gl-js/api/#Map.load)
để có thể khởi chạy.

**Các tham số**

-   `index` **[Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** vị trí của điểm ghé qua cần được đặt trong mảng các điểm ghé qua
-   `waypoint` **([Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)> | Point)**  có thể là một GeoJSON Point Feature hoặc toạ độ [lng, lat].

Trả về **[WeDirections](#wedirections)** `this`;


---

### setWaypoint

Thay đổi điểm ghé qua của tuyến đường tại một chỉ số cho trước. _Chú ý:_ lời gọi phương thức này yêu cầu [sự kiện tải bản đồ](https://www.mapbox.com/mapbox-gl-js/api/#Map.load) để có thể khởi chạy.

**Các tham số**

-   `index` **[Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** chỉ số của điểm ghé qua cần thay đổi
-   `waypoint` **([Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)> | Point)** có thể là một GeoJSON Point Feature hoặc toạ độ [lng, lat].

Trả về **[WeDirections](#wedirections)** `this`;


---

### removeWaypoint

Xoá một điểm ghé qua trong tuyến đường.

**Các tham số**

-   `index` **[Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** vị trí trong mảng các điểm ghé qua.

Trả về **[WeDirections](#wedirections)** `this`;


---

### getWaypoints

Lấy ra tất cả các điểm ghé qua trong tuyến đường.

Trả về **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)** `waypoints`


---

### removeRoutes

Xoá bỏ tất cả các tuyến đường cùng với các điểm ghé qua trong bản đồ.

Trả về **[WeDirections](#wedirections)** `this`;

### on

Đăng ký theo dõi các sự kiện xảy ra trong plugin.

**Các tham số**

-   `type` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** tên của sự kiện. Các sự kiện và dữ liệu truyền vào tương ứng là:-   
    -   **clear** `{ type: } Type có thể là một trong 'origin' hoặc 'destination'`
    -   **loading** `{ type: } Type có thể là một 'origin' trong 'destination'`
    -   **profile** `{ profile } Profile có thể là một trong 'driving', 'walking', hoặc 'cycling'`
    -   **origin** `{ feature } Được gọi khi điểm bắt đầu được đặt`
    -   **destination** `{ feature } Được gọi khi điểm đến được đặt`
    -   **route** `{ route } Được gọi khi một tuyến đường được cập nhật`
    -   **error** `{ error } Error là một chuỗi ký tự`
-   `fn` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)** Hàm được gọi khi sự kiện xảy ra.

Trả về **[WeDirections](#wedirections)** `this`;
