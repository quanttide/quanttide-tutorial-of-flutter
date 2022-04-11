# 异步

同步写法：

```dart
// This example uses the Google Books API to search
// for books about HTTP. For details, see
// https://developers.google.com/books/docs/overview
final url = Uri.https(
  'www.googleapis.com',
  '/books/v1/volumes',
  {'q': '{http}'},
);

// Await the HTTP GET response
// and print the response body.
http.get(url).then((result)=>print(result.body));
```

修改自[DartPad提供的样例](https://dartpad.cn/?id=4a68e553746602d851ab3da6aeafc3dd)。

## Flutter

https://api.flutter.dev/flutter/widgets/FutureBuilder-class.html

```dart
Widget buildOutput(input){
  return FutureBuilder(
    // https://api.flutter.dev/flutter/widgets/FutureBuilder-class.html
    future: executor.execute(input),
    builder: (BuildContext context, AsyncSnapshot<dynamic> snapshot) {
    if (snapshot.connectionState == ConnectionState.done) {
        // 请求已结束
        if (snapshot.hasError) {
        // 请求失败，显示错误
        return Text("Error: ${snapshot.error}");
        } else {
        // 请求成功，显示数据
        return Text("${snapshot.data}");
        }
    } else {
        // 请求未结束，显示正在加载的状态
        return const Text('代码运行中...');
    }
    },
  );
}
```
