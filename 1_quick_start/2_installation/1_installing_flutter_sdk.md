# 安装Flutter SDK

## 下载Flutter SDK

在计划存放Flutter SDK的目录运行

```shell
git clone -b stable https://mirrors.tuna.tsinghua.edu.cn/git/flutter-sdk.git
```

## 配置环境变量

```shell
export FLUTTER_STORAGE_BASE_URL="https://mirrors.tuna.tsinghua.edu.cn/flutter"
export PUB_HOSTED_URL="https://mirrors.tuna.tsinghua.edu.cn/dart-pub"
export FLUTTER_GIT_URL="https://mirrors.tuna.tsinghua.edu.cn/git/flutter-sdk.git"
```

### Windows

（TODO：张玉佳补充）

https://docs.flutter.dev/get-started/install/windows#update-your-path

### macOS

https://docs.flutter.dev/get-started/install/macos#update-your-path

## 检查Flutter配置

```shell
flutter doctor
```

## 参考资料

- 清华大学开源软件镜像站提供的[Flutter镜像安装帮助](https://mirrors.tuna.tsinghua.edu.cn/help/flutter/)
