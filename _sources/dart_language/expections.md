---
author: 张果
created_at: 2021-11-12
updated_at: 2022-07-29
---
# 异常处理

## 理解异常信息

怎么读报错信息？怎么复现报错信息？

一个案例记录，之后考虑用个新案例替换。

报错信息：

```
Null check operator used on a null value

This error occurs when you use a bang operator (!) on a nullable instance which wasn't initialized.

  CourseWidget:file:///Users/zhangguo/QuantTide/qtclass-app/qtclass-client-flutter/test/course_route_test.dart:12:47
```

其中，"12: 47" 是行数+（maybe）字符数。

经过查找，错误原因是：Lectures属性实际上给了空值，!检查就会让它不通过。

## 变量作用域

如何解决变量在try里，后续识别不到导致的错误？

把变量的声明写到函数前面。本质上这是一个作用域的问题。比如

```dart
Response response;
try {
  response = <....>;
}
catch (e) {
  throw 'message';
}
return response.data;
```

## 自定义异常类

需要使用`implements`关键字，因为`Exception`是抽象类。另外两个和继承有关的关键字，`extends`是单继承，`with`是Mixin模式的多重继承。

一个Demo如下：

```dart
class QCloudVodPlayVideoApiException implements Exception {
  int code;
  String message, requestId;

  QCloudVodPlayVideoApiException({
    this.code,
    this.message,
    this.requestId,
  });

  QCloudVodPlayVideoApiException.fromMap(Map<String, dynamic> data){
    this.code = data['code'];
    this.message = data['message'];
    this.requestId = data['requestId'];
  }

  String toString(){
    return """云点播视频播放API请求异常。
  * 错误码：$code
  * 错误信息：$message
  * 腾讯云requestId：$requestId
  """;
  }
}
```

这里除了基本构造器，还参考Flutter和Dart官方接口风格实现了fromMap构造器以方便直接传入response.data数据。

`toString`方法类似于Python的`__str__`方法，可以改变print到控制台或者log中的格式。
