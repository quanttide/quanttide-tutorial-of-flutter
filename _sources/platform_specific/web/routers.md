---
author: 张果
created_at: 2022-04-12
updated_at: 2022-04-12
outlines:
  - 为什么使用页面路由。Web平台更接近普通网页应用，方便用户通过URL访问特定页面。
  - Hash模式 vs Path模式（即History模式）
  - 使用Fluro改造路由为RESTful标准。
notes:
  - 小标题都还需要斟酌。
---

# 页面路由设置

## 修改Web应用URL策略

[官方文档](https://flutter.dev/docs/development/ui/navigation/url-strategies)定义了两种模式：

- Hash模式：默认模式，带有"#"。
- Path模式：不带有"#"。

我们需要把默认的Hash模式改为更符合正常认知的Path模式。

最简单的办法是使用[url_strategies](https://pub.dev/packages/url_strategy)库完成。安装库以后如下使用：

```dart
import 'package:url_strategy/url_strategy.dart';

void main() {
  // Here we set the URL strategy for our web app.
  // It is safe to call this function when running on mobile or desktop as well.
  setPathUrlStrategy();
  runApp(MyApp());
}
```

关键是`setPathUrlStrategy()`，效果等同于官方文档的方法，并且不影响Mobile和Desktop应用。

## RESTful标准设置动态路由

需要路由的原因是，Web网站是以单页应用的形式上线的，要让它看起来像普通网页，可以用网址访问到具体资源，修改路由必不可少。

我们希望Flutter页面的表现尽可能符合[RESTful标准](https://restfulapi.net)。


我们使用[`fluro`](https://pub.dev/packages/fluro)。

[`qlevar_router`](https://pub.dev/packages/qlevar_router)作为备选。
