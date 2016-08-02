# domTpl
基于 dom 的高性能模板引擎，

## 特性
* 基于dom而不是字符串
* 模板直接写在目标位置，无需 script 标签或字符串保存模板
* 简单高效
* 支持传参，模板内支持访问全局变量
* 有进行缓存、传参转为内部变量（不用 with）、过滤频繁更新dom的中间状态等方式优化性能
* 体积小， 仅 2k 多
* 支持 require.js, sea.js
* 兼容ie6+（下个版本）

## 如何使用

引入 domTpl.js
```javascript
<script src="../domTpl.js"></script>
```

编写模板
```html
<!DOCTYPE html>
<html>
  <head>
    <script src="../domTpl.js"></script>
  </head>
  <body>
    <ul>
      <li each="item in list">
        {{item.name}}
        <span if="item.age>=18">adult</span>
      </li>
    </ul>
  </body>
</html>
```

渲染
```javascript
var render = domTpl();
render({
  list:[
    {name:'tom', age:20},
    {name:'lily', age:17}
  ]
});
```


## API
```
domTpl(node, data)
```
```
node: 可选。默认为 html 节点
data: 可选。如果提供则直接渲染
return: 返回渲染函数 function(data){...}
  data: 可选。如不提供则使用 domTpl 的参数 data
```