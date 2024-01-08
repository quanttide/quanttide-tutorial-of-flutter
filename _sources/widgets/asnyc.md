# 异步组件

## FutureBuilder

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
