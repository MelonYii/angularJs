* 使用ng-bind-html-unsafe指令,我们会得到浏览器解析的标记的HTML片段.
```
<td nowrap="nowrap" title="'参与规则详情'" ng-bind-html="data.rules_desc"></td>
```

* 通过ajax 获取的数据 注入到 input 中 类型一定要正确，不然报错
```
_CallbackData.data['money_total'] = (parseFloat(_CallbackData.data['money_total']));
```

* $http 服务 加上头
```
var req = {
               method: 'POST',
               url: 'manage/sqpaper/enter',
               headers: {
                   'Content-Type': 'application/x-www-form-urlencoded;charset=utf-8',
                   'X-Requested-With': 'XMLHttpRequest' //判断是否ajax
               },
               data:  $.param({
                   'limit': 10,
                   'page': 1,
                   'option': 'getList'
               }),
               params : {
                   'limit': 10,
                   'page': 1,
                   'option': 'getList'
               }
           };
           $http(req).then(function (response) {
               console.log(response.data);
           });
```
