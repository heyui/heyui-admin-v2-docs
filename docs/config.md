# 系统参数配置

```
- config / 配置
  - router-config / 路由配置
  - heyui-config / heyui配置
  - dict-config / 字典配置
  - autocomplete-config / autocomplete配置
  - category-config / category配置
  - tree-config / 树配置
  - menu-config / 系统菜单配置
```


## heyui配置

参考 `heyui-config.js` 文件

``` javascript

import dictConfig from './dict-config';
import autocompleteConfig from './autocomplete-config';
import treeConfig from './tree-config';
import categoryConfig from './category-config';
import { heyuiConfig } from 'heyui';

const config = () => {
  // 将一些静态的字段定义到heyui中
  const staticDict = dictConfig();
  Object.keys(staticDict).forEach((key) => {
    heyuiConfig.addDict(key, staticDict[key]);
  });

  // 配置 autocomplete、tree、category
  heyuiConfig.config('autocomplete.configs', autocompleteConfig());
  heyuiConfig.config('tree.configs', treeConfig());
  heyuiConfig.config('category.configs', categoryConfig());

  // 配置 menu 参数
  heyuiConfig.config('menu', {
    keyName: 'key',
    titleName: 'title',
    childrenName: 'children'
  });
};

export default config;

```

tree-config, menu-config, autocomplete-config, category-config 请参考 heyui 官方文档。

## 路由配置

路由使用的是官方的： `vue-router`

vue-router 相关文档：[https://router.vuejs.org/zh](https://router.vuejs.org/zh/)

### Router定义

路由主要是定义系统中的所有router，目前系统中定义的都是异步加载的，建议系统主要的页面直接引用。

``` javascript
import Login from 'components/home/index';

{
  path: '/home',
  name: 'Home',
  // 异步加载
  component: () => import('@components/home/index'),
  // 直接引用
  component: Login,
  meta: {title: '首页', icon: 'icon-monitor'}
}
```
