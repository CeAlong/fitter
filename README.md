# fitter
**中文** | **[EN](./README_EN.md)**

Flutter项目的多尺寸UI适配方案

## Getting Started

在项目中引入如下代码，可以达到类rem的适配效果：

```
import 'package:fitter/fitter.dart';

void main() {
    // maybe your old code here?
    // runApp(MyApp());

    // and just change your code as below
    InnerWidgetsFlutterBinding.ensureInitialized()
      ..attachRootWidget(new MyApp())
      ..scheduleWarmUpFrame();
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // another old code maybe
    // return new MaterialApp(

    // need to replace `MaterialApp` into `CustomMaterialApp` 
    return new CustomMaterialApp(
      home: new Scaffold(
        body: Text('Hello World!')
      ),
    );
  }
}
```
默认的设计分辨率为宽度375px，如果想要自定义设计分辨率，那么加一行代码:

```
...
void main() {
    // custom design resolution
    ViewAdapter.screenWidth = 375;
    
    InnerWidgetsFlutterBinding.ensureInitialized()
      ..attachRootWidget(new MyApp())
      ..scheduleWarmUpFrame();
}
...
```
## Old Versions

- 如果要支持旧版本flutter SDK, 设置引用的`fitter` 版本号为 `^0.1.0`
- `fitter` 的 `^1.0.0` 版本依赖 flutter sdk 版本大于等于  `1.2.0`

## Kown Bugs

* `UIKitView` 相关的组件(如`webview` 或 `video`..) 并不能适配尺寸，原因尚未弄清楚...
* Fitter 1.0+ 版本依赖 `flutter sdk` 1.2+ 版本, 低版本会报错, 如要支持1.2以下版本，请使用 0.1.x版本的 Fitter

## Thanks To

思路来源于 [@genius158](https://github.com/genius158/FlutterTest/blob/master/lib/main.dart) 的文章 [post](https://juejin.im/post/5cb49e306fb9a068a3729b41)。感谢！