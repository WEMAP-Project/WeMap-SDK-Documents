# WeMap

Đối tượng WeMap biểu diễn một bản đồ. Bạn tạo một đối tượng WeMap với key để sử dụng API, chỉ định một phần tử HTML chứa bản đồ và các lựa chọn khác.  
WeMap GL JS khởi tạo bản đồ trên trang web và trả về đối tượng WeMap.

### Các tham số khởi tạo

`options` (**[Object]()**)

| Tên | Kiểu dữ liệu | Miêu tả | Giá trị mặc định | Bắt buộc có?
| ------------ | ------------ | ------------ | ------------ | ------------ 
| `options.key` | `string` | Bản đồ sẽ sử dụng key này. | | có
| `options.container` | [`HTMLElement`](https://developer.mozilla.org/docs/Web/HTML/Element) or [`string`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) | Phần tử HTML mà WeMap GL JS sẽ kết xuất bản đồ, hoặc `id` của phần tử đó. Phần tử này không được có phần tử con nào. | | có
| `options.style` | `string` | Kiểu dáng của bản đồ. Các lựa chọn: `default`, `bright`, `dark` | `default` | không
| `options.center` | `LngLatLike` | Điểm trung tâm khi khởi tạo của bản đồ. | `[105.8550736, 21.0283243]` (Toạ độ của Hà Nội) | không
| `options.zoom` | `number` | Độ phóng đại khi khởi tạo của bản đồ | `10` | no
| `options.reverse` | `boolean` | Nếu `true`, bật tính năng reverse khi nhấn chuột trái, bật tính năng menu khi nhấn chuột phải. Biểu tượng chuột sẽ thay đổi khi di chuyển chuột qua icon của các địa điểm POI và hiển thị thông tin chi tiết của địa điểm khi nhấn vào. | `false` | không
| `options.urlController` | `boolean` | Nếu `true`, tham số URL trên thanh địa chỉ sẽ được cập nhật tương ứng khi các tính năng hoạt động. | `true` | không

**Ví dụ**
```javascript
var wemap = new wemapgl.WeMap({
    container: 'map',
    key: 'YOUR-WEMAP-KEY-HERE',
    style: 'bright',
    center: [105.1, 21.0],
    zoom: 13,
    urlController: "true",
    reverse: "true"
});
```
### Các hàm

#### `addControl(control, position?)`  
Thêm một `IControl` vào bản đồ và thực hiện lời gọi `control.onAdd(this)`.  
**Các tham số**  
**`control`** ([`IControl`]()) `IControl` cần thêm vào.  
**`position`** ([`string`]()?) vị trí mà control sẽ được thêm vào. Các lựa chọn: `'top-left'` , `'top-right'` , `'bottom-left'` , và `'bottom-right'` . Mặc định là `'top-right'`.  
**Trả về**  
[`WeMap`](#wemap): `this`  
**Ví dụ**

```javascript
// Thêm một control vào bản đồ
map.addControl(new mapboxgl.NavigationControl());
```

---

#### `removeControl(control)`  
Removes the control from the map.  
**Các tham số**  
**`control`** ([`IControl`]()) The `IControl` to remove.
**Trả về**  
[`WeMap`](#wemap): `this`  
**Ví dụ**  

```javascript
// Định nghĩa một control
var navigation = new mapboxgl.NavigationControl();
// Thêm control này vào bản đồ
map.addControl(navigation);
// Xoá control này khỏi bản đò
map.removeControl(navigation);
```