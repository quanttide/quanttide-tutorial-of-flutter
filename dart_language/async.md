# 异步

同步写法

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

## Future vs Stream

单次 vs 多次

详见：https://www.digitalocean.com/community/tutorials/flutter-futures-and-streams-dart
