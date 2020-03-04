# WeMap Web SDK

## Giới thiệu

Đây là trang đưa ra các **ví dụ**, **hướng dẫn** và **tài liệu** của [**WeMap Web SDK**](#) để bạn có thể bắt đầu sử dụng SDK của WeMap.

WeMap Web SDK hay WeMap GL JS là một thư viện JavaScript sử dụng WebGL để hiển thị bản đồ có tính tương tác từ các [vector tile](#) và [WeMap style](#). Nó là một phần của hệ sinh thái WeMap GL.

## Hướng dẫn cài đặt và sử dụng

Bạn có thể `clone` từ Github phiên bản mới nhất của thư viện [tại đây](https://github.com/WEMAP-Official/WeMap-Web-SDK-Release/tree/master/assets), sau đó nhúng vào trang web của bạn
```html
<script src="<đường dẫn tới repo>/WeMap-Web-SDK-Release/assets/js/wemap-gl.js" type="text/javascript"></script>
<link href="<đường dẫn tới repo>/WeMap-Web-SDK-Release/assets/css/wemap.min.css" rel="stylesheet" />
```
Bạn cũng có thể sử dụng [CDN](https://en.wikipedia.org/wiki/Content_delivery_network) mà không cần phải tải về
```html
<script src="https://raw.githubusercontent.com/WEMAP-Official/WeMap-Web-SDK-Release/master/assets/js/wemap-gl.js" type="text/javascript"><script>
<link href="https://raw.githubusercontent.com/WEMAP-Official/WeMap-Web-SDK-Release/master/assets/css/wemap.min.css" rel="stylesheet" />
```
Để sử dụng các dịch vụ của WeMap, bạn cần có một *key*. [Liên hệ]() để nhận một key.

## Cùng bắt đầu với một ví dụ đơn giản
- Thêm file `.js` và `.css` của thư viện vào header trang web của bạn giống như sau:  

```html
<script src="../wemapgl/js/wemap-gl.js" type="text/javascript"></script>
<link href="../wemapgl/css/wemap.min.css" rel="stylesheet" />
```
- Thêm một phần tử `div` với một `id` tại vị trí mà bạn muốn đặt bản đồ
```html
 <div id="map"></div>
```
- Hãy đảm bảo rằng phần tử `div` vừa thêm vào có thể hiển thị đúng cách
```html
<style>
    #map { width: 700px; height: 500px; }
</style>
```
- Khởi tạo và thêm bản đồ vào
```html
<script>
    var map = new wemapgl.WeMap({
            container: 'map',
            key: 'key-của-bạn'
    });
</script>
```
Như vậy, một bản đồ WeMap đã được thêm vào trang web của bạn. Hãy tận hưởng!

Để sử dụng nhiều tính năng hơn, hãy đọc thêm về *các thành phần cơ bản* dưới đây
## Các thành phần cơ bản

### [`wemapgl.WeMap`](./wemap.md)

Một đối tượng `WeMap` biểu diễn một bản đồ, cung cấp các giao diện lập trình để tạo ra các bản đồ có tính tương tác cao.

---

### [`wemapgl.WeGeocoder`](./wegeocoder.md)

Một plugin Geocoding cho bản đồ WeMap, cho phép lựa chọn engine tìm kiếm, lấy thông tin chi tiết của địa điểm ...

---

### [`wemapgl.WeDirections`](./wedirections.md)

Plugin cung cấp tính năng chỉ đường chất lượng cao cho bản đồ WeMap.


## Cách tài liệu này được tạo ra

Tài liệu này được ra với sự hỗ trợ của công cụ [MkDocs](https://www.mkdocs.org/).  
Định dạng `.md` của tài liệu có thể lấy [tại đây](https://github.com/WEMAP-Official/WeMap-SDK-Documents).

---

*Cập nhật ngày 04 tháng 03 năm 2020*

*Bản quyền thuộc về WeMap*
