# 基础依赖

具体配置请参考脚手架配置。

### Utils
继承扩展hey-utils方法库，可以在 src/js/common/utils 扩展定义公共方法。

hey-utils: [https://www.npmjs.com/package/hey-utils](https://www.npmjs.com/package/hey-utils)

系统中直接调用:

``` javascript
import utils from '@common/utils';

let a = 1;
utils.isString(a)
// false
```

### HeyUI
heyui组件库  

系统中直接调用:

``` javascript
import { message } from 'heyui';

message.success("成功")
```

### Model
前端数据模型  
js-model：[https://www.npmjs.com/package/js-model](https://www.npmjs.com/package/js-model)


``` javascript
import Model from 'js-model';

export default new Model({
  username: '',
  password: ''
});

```


### Request
引用 src/js/common/request 文件，包含了前端所有的请求定义。

参考`app-frame.vue`文件中，直接引用接口请求

``` javascript
import Request from '@common/request';

Request.User.info().then((resp) => {
  if (resp.ok) {
    //
  }
})
```


`request.js`文件

``` javascript
import Ajax from './ajax';

const Request = {
  User: {
    info(){
      return Ajax.get('/account/info');
    }
  },
  Dict: {
    get(){
      return Ajax.get(`/dict`);
    },
  },
  Home: {
    getMessageList() {
      return Ajax.get(`/home/messages`);
    }
  },
  Login: {
    login(param){
      return Ajax.postJson("/login", param);
    },
    logout(param){
      return Ajax.post("/logout", param);
    }
  }
};

export default Request;
```