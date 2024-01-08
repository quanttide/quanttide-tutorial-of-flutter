# 部署

- 路径设置：由于`url_strategy`的引入，`<base>`标签不可以设置相对路径。
- 云端部署：设置为根目录，云端部署在对象存储的存储桶根目录，云开发静态网站托管不放在根目录会异常。
- 运行服务：编译在根目录下进行，本地运行`python -m http.server 8000`必须在build/web/目录下启动。

## 压缩包体积

基于`qlevar_router`的middleware机制。

详见：https://medium.com/@SchabanBo/reduce-your-flutter-web-app-loading-time-8018d8f442
