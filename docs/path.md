# 路径别名

系统对一些基础的路径定义了别名，这样就可以文件中直接调用。

具体配置请参考如下。

``` javascript
configureWebpack: {
  resolve: {
    alias: {
      '@': path.resolve(__dirname, 'src/'),
      '@components': path.resolve(__dirname, 'src/components/'),
      '@common': path.resolve(__dirname, 'src/js/common/'),
      '@model': path.resolve(__dirname, 'src/js/model/'),
      '@js': path.resolve(__dirname, 'src/js/')
    }
  },
}
```

### @js

定义为：`src/js/`

系统中直接调用:

``` javascript
import initHeyui from '@js/config/heyui-config';
```
### @components

定义为：`src/components/`

系统中直接调用:

``` javascript
import AccountInfoShow from '@components/demo-components/modules/account-info-show';
```
### @model

定义为：`src/js/model`

系统中直接调用:

``` javascript
import Login from '@model/login/Login';
```

如果你需要再添加其他的路径别名，请参考脚手架的文档，自行配置。