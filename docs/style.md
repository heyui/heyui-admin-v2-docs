# 样式

```
- css
  - app.less / 系统的所有样式引用
  - common.less / 全局使用的样式
  - frame.less / 系统框架使用的样式
  - fonts / 字体库
  - markdown.less / Markdown插件的样式
  - overwrite.less / 对于组件库样式做自定义覆盖
  - richtext-editor.less / 富文本编辑器
  - var.js / 全局变量定义，提供给vue-cli
  - var.less / 全局变量定义，提供给hey-cli
```

## 组件库主题 / 全局变量

### vue-cli

通过修改  `var.js` 自定义主题。

``` javascript
const vars = require('heyui/themes/var.js');
Object.assign(vars, {
  'primary-color': '#3788ee',
  'link-color': '#3788ee',
  'blue-color': '#2d7bf4',
  'green-color': '#0acf97',
  'yellow-color': '#f9bc0b',
  'red-color': '#f1556c',
  'hover-background-color': '#f8f8f8',
  'input-height': '32px',
  'layout-header-height': '60px',
  'layout-sider-width': '240px',
  'layout-sider-collapse-width': '70px',
  'menu-dark-color': '#001529',
  'menu-white-background-color': '#ecf8f2',
  'sys-tabs-height': '50px'
});
module.exports = vars;

```

通过`vue.config.js`配置全局样式：  

```javascript
const globalVars = require('./src/css/var.js');

css: {
  loaderOptions: {
    less: {
      lessOptions: { globalVars }
    }
  }
},
```

如果是更加细化的调整，建议在 `overwrite.less` 文件中，对样式进行覆盖。

## 自定义样式

如果你还需要做更多的样式定义，建议新增less文件，并在app.less中引用。

例：自定义Form附加样式

在 css 文件夹中新增 form.less 文件

``` css
.form-section {
  .fort-section-title {

  }
}
```

在 app.less 中引入 form.less 文件

``` css
@import (less) "./form.less";
```



