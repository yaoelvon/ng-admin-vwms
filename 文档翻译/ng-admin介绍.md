# ng-admin介绍

使用ng-admin配合RESTFul风格的后端API可以马上得到一个完整的管理界面，功能包括：数据表格（datagrid）、过滤器（filters）、复杂的表单控件（complex form widgets）、多模型关系（multi-model relationships）和仪表盘/概览（dashboard）。它不仅仅拥有简单的增删该查（CRUD）功能，在不影响其他开发进度的情况下，ng-admin能够很快帮助你构建一个复杂的图形用户界面。

* [在线例子](http://marmelab.com/ng-admin-demo/#/dashboard)([例子源码](https://github.com/marmelab/ng-admin-demo))
* [英文文档](http://ng-admin-book.marmelab.com/)

## 安装

当前的ng-admin版本（master分支）基于Angular.js 1.4。如果你需要兼容Angular 1.3，请使用ng-admin 0.9。

使用包管理工具npm或bower获取ng-admin：

```sh
npm install ng-admin —save
# 或
bower install ng-admin —save
```

将库文件ng-admin.min.css和ng-admin.min.js添加到HTML中，然后在`<body></body>中`增加`<div ui-view>`，最后对admin进行配置：

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
        // 将管理应用连接到DOM中，然后运行它
        nga.configure(admin);
    }]);
    </script>
  </body>
</html>
```

## 入门（Getting Started）

如果是初次接触ng-admin，请仔细阅读章节[入门](文档翻译/入门.md)。

## 用法示例（Usage Examples）

* 在[博客管理示例](http://ng-admin.marmelab.com/#/dashboard)([源码](examples/blog/config.js))中，你能看到一个简单的配置，里面的实体（entities)有发帖(posts)、评论（comments)和标签（tags）。同时使用FakeRest在浏览器中模拟后端REST API。
* [Posters Galore demo](http://marmelab.com/ng-admin-demo/) ([source](https://github.com/marmelab/ng-admin-demo)) 是一个更完整的电子商务管理页面，包含自定义认证、页面、指令和模块，并使用WebPack组织良好。同时使用[FakeRest](https://github.com/marmelab/FakeRest)在浏览器中模拟后端REST API。


## 配置参考（Configuration Reference）

在ng-admin中，一个管理工具是由包含多个*实体（entities)*的*应用*组成。每个实体（entity)拥有5种*视图*，每个视图拥有很多*字段（fields）*。

```
application
 |-header
 |-menu
 |-dashboard
 |-entity[]
    |-creationView
    |-editionView
    |-deletionView
    |-showView
    |-listView
        |-field[]
           |-name
           |-type
```

有关更多详细信息，请参阅[配置API参考](文档翻译/配置API参考.md)专用章节。

**提示**:您在ng-admin项目中将找不到相关的类。 实际上，管理配置API有一个独立、框架无关的库，称为[admin-config](https://github.com/marmelab/admin-config)。 不要犹豫，浏览该库的代码以了解更多。

## 关联（Relationships）

Ng-admin的读写视图实体之间支持‘关联’。它提供了特定的字段类型来实现这些‘关联’：`reference`, `referenced_list`, `reference_many`, 和 `embedded_list`。[关联参考章节](文档翻译/关联.md)中使用例子描述了更多的字段类型。

另外，[配置API参考章节](文档翻译/配置API参考.md)的字段部分具有所有字段类型的列表。

## 菜单配置（Menu Configuration）

默认情况下，ng-admin创建一个侧边栏菜单，每个实体有一个条目。 如果要自定义侧边栏（标签，图标，顺序，添加子菜单等），则必须手动定义菜单。

请参见[菜单配置](文档翻译/菜单配置.md)专用章节。

## 仪表板配置（Dashboard Configuration）

ng-admin应用程序的主页被称为仪表板。 使用它向最终用户显示重要的信息，例如最新条目或图表。

请参阅[仪表板配置](文档翻译/仪表板配置.md)专用章节。

## 定制API映射（Customizing the API Mapping）

ng-admin对REST API所做的所有HTTP请求都是由[Restangular](https://github.com/mgonto/restangular)执行的。

REST规范没有提供足够的详细信息来涵盖管理GUI的所有需求。 ng-admin对如何设计您的API进行了一些假设。 所有这些假设都可以通过[Restangular的请求和响应拦截器](https://github.com/mgonto/restangular#addresponseinterceptor)来覆盖。

这意味着你不需要为了ng-admin而调整你的API; ng-admin可以适应任何REST API，这要归功于Restangular的灵活性。

请参阅[定制API映射](文档翻译/定制API映射.md)专用章节。

## 主题（Theming）

你可以在不同的级别覆盖几乎所有ng-admin生成的HTML。

参见[主题](文档翻译/主题.md)专门章节。

## 添加自定义页面（Adding Custom Pages）

对于每个实体，ng-admin创建用于'创建'，'检索'，'更新'和'删除'（CRUD）此实体的必要页面。 当您需要在实体上实现更特定的操作时，您必须添加自定义页面，例如要求向一个电子邮件地址发送消息的页面。 如何路由到特定页面并在ng-admin布局中显示它？

请参阅[添加自定义页面](文档翻译/添加自定义页面.md)专用章节。

## 添加自定义类型（Adding Custom Types）

当您在REST API的响应信息和ng-admin之间映射字段时，您需要为其指定类型。 这个类型会确定如何显示和编辑这些数据。 自定义现有的ng-admin类型和添加新的ng-admin类型非常容易。

请参阅[添加自定义类型](文档翻译/添加自定义页面.md)专用章节。

## 生产准备（Getting Ready For Production）

要构建具有所需依赖关系的ng-admin源，并获得关于性能提升的提示，请参阅[生产准备](文档翻译/生产准备.md)专用章节。

## 信息（News）

关于ng-admin（教程，插件，新版本等）的新闻，请按照[marmelab博客](http://marmelab.com/blog/)。

您还应该观看[gitHub上的ng-admin发布页面](https://github.com/marmelab/ng-admin/releases)以获取有关新发布的公告以及完成更新日志。

## 支持（Support）

Ng-admin是一个开源项目，并且社区越来越大。 您可以通过在以下任何渠道询求帮助：

* [StackOverflow](http://stackoverflow.com/questions/tagged/ng-admin)
* Gitter (live chat)](https://gitter.im/marmelab/ng-admin) [![Join the chat at https://gitter.im/marmelab/ng-admin](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/marmelab/ng-admin?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

请尽可能多地提供上下文，包括和管理配置的代码段，以及您映射的API的响应。

## 贡献（Contributing）

在您的特定环境中的使用ng-admin的反馈是有价值的，不要犹豫[打开GitHub的issue](https://github.com/marmelab/ng-admin/issues)提出任何你想问的问题。

