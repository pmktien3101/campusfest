# cài 1 số thư viện như customize-cra tuỳ chỉnh cấu hình Webpack
### Lợi ích khi sử dụng customize-cra:
Không cần eject: Bạn có thể tuỳ chỉnh cấu hình Webpack mà không cần eject, giữ cho dự án dễ dàng cập nhật và bảo trì.
Tập trung vào những tuỳ chỉnh cần thiết: Bạn chỉ cần tuỳ chỉnh những phần cần thiết thay vì phải quản lý toàn bộ cấu hình Webpack.
### cách install customize-cra: 
+ chạy câu lệnh: npm i customize-cra react-app-rewired -D
+ tạo file config-overrides.js
+  bỏ đoạn code vào file vừa tạo : module.exports = function override(config, env) {
                                    //do stuff with the webpack config...
                                    return config;
                                    }
+ trong package.json phần scripts đổi thành react-app-rewired

# Cài đặt babel plugin module resolver 
### Lợi ích khi sử dụng bable plugin module resolver:
một plugin giúp bạn định nghĩa alias (đường dẫn rút gọn) cho các module trong dự án, thay vì phải sử dụng các đường dẫn tương đối dài dòng. Điều này giúp mã nguồn của bạn dễ đọc và bảo trì hơn.
### cách install :
+ npm install --save-dev babel-plugin-module-resolver
+ tạo file babelrc
+ bỏ đoạn code vào
+ {
  "plugins": [
    ["module-resolver", {
      "root": ["./src"],
      "alias": {
        "test": "./test",
        "underscore": "lodash"
      }
    }]
  ]
}
### cấu hình lại file babelrc: 
+ xóa "root": ["./src"],
+ thêm ~ trong alias như vậy:
+ {
    "plugins": [
      ["module-resolver", {
        "alias": {
          "~": "./src"
        }
      }]
    ]
  }
