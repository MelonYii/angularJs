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

* directive 小例 单机图片 放大缩小
```
angular.module('app').register.directive('imgBigger', function () {
    return {
        restrict: 'AE',
        replace: 'true',
        link: function (scope, elem, attrs) {
            elem.bind('click', function () {
                if (elem.height()>200){
                    elem.height(100)
                }else{
                    elem.height(500)
                }
            });
        }
    }
});
```

* 通过angularjs  $http 服务的ajax 服务，then 方法会自动进行脏值检测。不需要再调用$scope.$apply方法

* 一个page中如果有有两个form 其脏值检测可能会有冲突

* ng-show 中写表达式 表达式中不能出现空格
```
<div ng-show="check_status=='123' || check_status=='2'" class="text-center"> right
<div ng-show="check_status == '123' || check_status == '2'" class="text-center">
error
```
