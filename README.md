# 前言

电商系统对逻辑要求比较高，也比较复杂，作为nodejs练习的项目，对提升nodejs帮助绝对是很大的。但nodejs并不适合作为此类后台系统，这只是一个单纯的练习项目，所以请不要用于商业用途，此项目是 [vue2-elm](https://github.com/bailicangdu/vue2-elm) 的后台系统，保持和官网一致的API接口。所有的接口都为开放接口，如果您也感兴趣，可以调用接口进行调试。


# 说明

>  nodejs + mongodb 构建的后台系统

>  如果对您对此项目有兴趣，可以点 "Star" 支持一下 谢谢！ ^_^

>  或者您可以 "follow" 一下，我会不断开源更多的有趣的项目

>  开发环境 macOS 10.12.4  nodejs 6.10.2

>  传送门：[前端项目地址](https://github.com/bailicangdu/vue2-elm) [后台管理系统地址](https://github.com/bailicangdu/back-manage)  [原生APP项目地址](https://github.com/bailicangdu/RN-elm)


## 技术栈

nodejs + express + mongodb + mongoose + es6/7 + mocha + bluebird + bootstrap


## 项目运行


```
git clone https://github.com/bailicangdu/node-elm  

cd node-elm

npm install

开启 mongodb

npm run dev 

访问: http://localhost:8001

```




## 目标功能

- [x] 定位功能
- [x] 城市列表
- [x] 搜索地址
- [ ] 添加商铺
- [ ] 搜索美食，餐馆
- [ ] 餐馆排序
- [ ] 添加食品列表
- [ ] 购物车功能
- [ ] 店铺评价
- [ ] 食品详情
- [ ] 商家详情
- [ ] 登录、注册
- [ ] 修改密码
- [ ] 用户信息
- [ ] 下单功能 
- [ ] 订单列表
- [ ] 订单详情
- [ ] 下载App
- [ ] 添加、删除、修改收货地址
- [ ] 帐户信息
- [ ] 服务中心
- [ ] 红包
- [ ] 上传头像
- [ ] 支付(支付宝，微信)
- [ ] 后台管理系统
- [ ] 部署上线





## 项目布局
```
.
├── config                                  // 配置文件目录
│   ├── default.js                          // 默认配置
│   └── production.js                       // 生产环节配置文件
├── controller                              // 负责路由操作的具体执行
│   ├── bos
│   ├── eus
│   ├── food.js
│   ├── member
│   ├── payapi
│   ├── promotion
│   ├── shopping
│   ├── ugc
│   ├── v1
│   ├── v2
│   ├── v3
│   └── v4
├── logs                                    // 日志文件
│   └── success.log
├── middlewares                             // 路由中间件
│   └── userStatus.js
├── models                                  // 数据模型
│   ├── bos
│   ├── eus
│   ├── food.js
│   ├── member
│   ├── payapi
│   ├── promotion
│   ├── shopping
│   ├── ugc
│   ├── v1
│   ├── v2
│   ├── v3
│   └── v4
├── mongodb                                  // 连接 mongodb
│   └── db.js
├── public                                   // 静态资源目录
│   ├── css
│   ├── elm                                  // 前端页面
│   ├── img
│   └── js
├── routes                                   // 路由控制中心
│   ├── bos.js
│   ├── eus.js
│   ├── home.js
│   ├── index.js
│   ├── member.js
│   ├── payapi.js
│   ├── promotion.js
│   ├── shopping.js
│   ├── ugc.js
│   ├── v1.js
│   ├── v2.js
│   ├── v3.js
│   └── v4.js
├─── test                                    // 测试
├─── views                                   // 后台管理系统页面
├── .babelrc                                 // 配置babel
├── .gitignore                               // 设置忽略文件
├── app.conf                                 // 百度BAE部署所需配置文件
├── app.js                                   // 基础配置
├── index.js                                 // 入口
├── package.json                             // 配置文件
.

```


# 接口文档

## 目录:
[1. 获取城市列表](#api_1) 

[2. 获取所选城市信息](#api_2) 

[3. 搜索地址](#api_3) 


```
说明：baseUrl: http:www.cangdu.org
```

### 1.获取城市列表

**请求URL**
> baseUrl + '/v1/cities'

**请求方式**
>**GET**

**请求参数**

|参数|是否必选|类型|说明|
|:-----|:-------:|:-----|:-----|
|type      |Y       |string  |类型  guess：定位城市，  hot：热门城市， group：所有城市 |

**返回示例**
>    
```javascript
{
  id: 1,
  name: "上海",
  abbr: "SH",
  area_code: "021",
  sort: 1,
  latitude: 31.23037,
  longitude: 121.473701,
  is_map: true,
  pinyin: "shanghai"
}
```

### 2.获取所选城市信息

**请求URL**
> baseUrl + '/v1/cities/:id'

**请求方式** 
>**GET**

**请求参数**

>
|参数|是否必选|类型|说明|
|:-----|:-------:|:-----|:-----|
|id      |Y       |int   |城市id |

**返回示例**
>    
```javascript
{
  id: 1,
  name: "上海",
  abbr: "SH",
  area_code: "021",
  sort: 1,
  latitude: 31.23037,
  longitude: 121.473701,
  is_map: true,
  pinyin: "shanghai"
}
```

### 3.搜索地址

**请求URL**
> baseUrl + '/v1/pois'

**请求方式** 
>**GET**

**请求参数**

>
|参数|是否必选|类型|说明|
|:-----|:-------:|:-----|:-----|
|city_id      |Y       |int   |城市id |
|keyword      |Y       |string   |搜索关键词 |
|type      |N       |string   |搜索类型，默认为search |

**返回示例**
>    
```javascript
[
    {
        name: "上海迪士尼乐园",
        address: "上海市浦东新区申迪西路753号",
        latitude: 31.14419,
        longitude: 121.66034,
        geohash: "31.14419,121.66034"
    },
    {
        name: "迪士尼",
        address: "上海市浦东新区妙境路1118号家乐福川沙店1层",
        latitude: 31.18183,
        longitude: 121.69279,
        geohash: "31.18183,121.69279"
    },
    ...  //共10个数据
]
```


## License

[MIT](https://mit-license.org/)
