# ng-admin介绍

使用ng-admin配合RESTFul风格的后端API可以马上得到一个完整的管理界面，功能包括：数据表格（datagrid）、过滤器（filters）、复杂的表单控件（complex form widgets）、多模型关系（multi-model relationships）和仪表盘/概览（dashboard）。不仅仅是简单的增删该查（CRUD）功能，ng-admin将帮助你构建一个复杂的图形用户界面，无需你动手。

* [在线例子](http://marmelab.com/ng-admin-demo/#/dashboard)([源码](https://github.com/marmelab/ng-admin-demo))
* [英文文档](http://ng-admin-book.marmelab.com/)

## 1.安装
当前的ng-admin版本（master分支）基于Angular.js 1.4。如果你需要兼容Angular 1.3，请使用ng-admin 0.9。

使用包管理工具npm或bower获取ng-admin：

```sh
npm install ng-admin —save
# or
bower install ng-admin —save
```

将ng-admin.min.css和ng-admin.min.js添加到HTML，增加一个<div ui-view>，然后配置这个admin：

```html
<!doctype html>
<html lang=“en”>
  <head>
    <title>My First Admin</title>
    <link rel=“stylesheet” href=“node_modules/ng-admin/build/ng-admin.min.css”>
  </head>
  <body ng-app=“myApp”>
    <div ui-view></div>
    <script src=“node_modules/ng-admin/build/ng-admin.min.js”></script>
    <script type=“text/javascript”>
    var myApp = angular.module(‘myApp’, [‘ng-admin’]);
    myApp.config([‘NgAdminConfigurationProvider’, function(NgAdminConfigurationProvider) {
        var nga = NgAdminConfigurationProvider;
        // 创建一个管理应用
        var admin = nga.application(‘My First Admin’);
        // 之后的更多配置
        // ...
        // 将管理应用连接到DOM并运行它
        nga.configure(admin);
    }]);
    </script>
  </body>
</html>
```

## 2.入门（Getting Started）

## 3.用法示例（Usage Examples）

## 4.配置参考（Configuration Reference）

## 5.关系（Relationships）

## 6.菜单配置（Menu Configuration）

## 7.仪表盘/概览配置（Dashboard Configuration）

## 8.自定义API映射（Customizing the API Mapping）

## 9.主题修改（Theming）

## 10.翻译（Translation）

## 11.增加自定义页面（Adding Custom Pages）

## 12.增加自定义类型（Adding Custom Types）

## 13.为生产做准备（Getting Ready For Production）

## 14.信息（News）

## 15.支持（Support）

## 16.贡献（Contributing）

## 17.版权申明（License）