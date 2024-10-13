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
  ]}
  + tạo jsconfig.json
  + bỏ vô
  + {
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "*": ["src/*"]
    }
  }
}
+ bỏ này vào file config-overrides.js
+ const { override , useBabelRc} = require("customize-cra");
module.exports = override(useBabelRc());

##### khi npm start thì nó sẽ vào package.json chạy r mốc qua config-overrides.js để nhận cấu hình thư viện webpack để ghi đè cái mà đc ẩn đi bởi create react app => override trong hàm trên là để trả lại cấu hình của webpack cái mà đc ẩn sau đó export ra ngoài đẻ chạy lên, overrride đc hổ trợ bởi customize-cra 
### Cài đặt và cấu hình Prettier trên VS Code
+ tạo file tên prettierrc và patse
+ {
  "arrowParens": "always",
  "bracketSameLine": false,
  "bracketSpacing": true,
  "embeddedLanguageFormatting": "auto",
  "htmlWhitespaceSensitivity": "css",
  "insertPragma": false,
  "jsxSingleQuote": false,
  "printWidth": 120,
  "proseWrap": "preserve",
  "quoteProps": "as-needed",
  "requirePragma": false,
  "semi": true,
  "singleQuote": true,
  "tabWidth": 4,
  "trailingComma": "all",
  "useTabs": false,
  "vueIndentScriptAndStyle": false
}
+ tạo folder .vscode => tạo file settings.json rồi bỏ vào: 
+ {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"

} 
### Cấu hình sử dụng CSS, SASS
+ tạo folder globalStyles với code
+ improt file đó vào file index.js
+ root.render(
  <React.StrictMode>
    <GlobalStyles>
      <App />
    </GlobalStyles>
  </React.StrictMode>,

); 
+ sao đó install sass : npm i -D sass
+ reset css => tải thư viện : npm install --save normalize.css
  => normalize.css là một tệp CSS phổ biến dùng để làm đồng nhất các kiểu mặc định của trình duyệt trên các trình duyệt khác nhau. Các trình duyệt như Chrome, Firefox, Safari, Edge, và Internet Explorer có các kiểu mặc định riêng cho các phần tử HTML (như margin, padding, font, và kích thước chữ). 
+ default css: trong file GloablStyes.scss
### Cài đặt và cấu hình Router | Xây dựng cơ chế tải Layout 
+ cài đặt react-router-dom: npm i react-router-dom
+ import { BrowserRouter as Router, Routes, Route } from 'react-router-dom'; => vào App.js
### Cài 1 số thư viện
+ Tippy
+ Axios
