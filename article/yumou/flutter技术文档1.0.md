Flutter 基础技术文档

🎯 核心概念

响应式框架

```dart
Widget build(BuildContext context) {
  return Widget; // 声明式UI，状态变化时自动重建
}
```

一切皆组件

· Widget：UI构建的基本单元
· 组合优于继承：通过组合简单Widget构建复杂UI
· 不可变性：Widget不可变，配置变化时重建

📱 核心组件

基础Widget

```dart
// 文本
Text('Hello', style: TextStyle(fontSize: 16))

// 按钮
ElevatedButton(onPressed: () {}, child: Text('按钮'))
TextButton(onPressed: () {}, child: Text('文本按钮'))

// 图片
Image.asset('assets/image.png')
Image.network('https://example.com/image.jpg')

// 图标
Icon(Icons.star, color: Colors.yellow)
```

布局Widget

```dart
// 线性布局
Column(children: [Widget1, Widget2]) // 垂直
Row(children: [Widget1, Widget2])    // 水平

// 弹性布局
Expanded(child: Widget) // 占用剩余空间
Flexible(fit: FlexFit.loose, child: Widget)

// 层叠布局
Stack(
  children: [
    Positioned(top: 10, child: Widget1),
    Align(alignment: Alignment.center, child: Widget2),
  ]
)

// 容器
Container(
  width: 100,
  height: 100,
  padding: EdgeInsets.all(10),
  margin: EdgeInsets.all(5),
  decoration: BoxDecoration(
    color: Colors.blue,
    borderRadius: BorderRadius.circular(8),
  ),
  child: ChildWidget,
)
```

列表与网格

```dart
// 简单列表
ListView(children: [Widget1, Widget2, Widget3])

// 动态列表
ListView.builder(
  itemCount: items.length,
  itemBuilder: (context, index) => ListTile(title: Text(items[index]))
)

// 网格
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2, // 每行2个
    crossAxisSpacing: 10,
    mainAxisSpacing: 10,
  ),
  itemCount: items.length,
  itemBuilder: (context, index) => ItemWidget(items[index]),
)
```

🎨 样式与主题

主题定义

```dart
MaterialApp(
  theme: ThemeData(
    primaryColor: Colors.blue,
    accentColor: Colors.orange,
    fontFamily: 'Roboto',
    textTheme: TextTheme(
      headline1: TextStyle(fontSize: 72, fontWeight: FontWeight.bold),
      bodyText1: TextStyle(fontSize: 14),
    ),
  ),
  home: HomePage(),
)
```

自定义样式

```dart
// 文本样式
TextStyle(
  color: Colors.black,
  fontSize: 16,
  fontWeight: FontWeight.bold,
  letterSpacing: 1.2,
)

// 边框与阴影
BoxDecoration(
  color: Colors.white,
  border: Border.all(color: Colors.grey, width: 1),
  borderRadius: BorderRadius.circular(8),
  boxShadow: [
    BoxShadow(
      color: Colors.black12,
      blurRadius: 4,
      offset: Offset(0, 2),
    )
  ],
)
```

📊 状态管理

有状态Widget

```dart
class CounterWidget extends StatefulWidget {
  @override
  _CounterWidgetState createState() => _CounterWidgetState();
}

class _CounterWidgetState extends State<CounterWidget> {
  int _counter = 0;
  
  void _increment() {
    setState(() {
      _counter++;
    });
  }
  
  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Count: $_counter'),
        ElevatedButton(onPressed: _increment, child: Text('增加')),
      ],
    );
  }
}
```

状态管理方案

1. setState：简单局部状态
2. InheritedWidget：跨Widget树状态共享
3. Provider：推荐的状态管理库（见常用库）
4. Riverpod：Provider的改进版
5. Bloc/RxDart：响应式状态管理

🛣️ 导航与路由

基本导航

```dart
// 跳转
Navigator.push(context, MaterialPageRoute(builder: (context) => NextPage()));

// 返回
Navigator.pop(context, '返回值');

// 命名路由
MaterialApp(
  routes: {
    '/': (context) => HomePage(),
    '/details': (context) => DetailsPage(),
  },
);

// 使用命名路由
Navigator.pushNamed(context, '/details', arguments: '参数');
```

路由参数

```dart
// 传递参数
Navigator.pushNamed(context, '/details', arguments: {'id': 123});

// 接收参数
ModalRoute.of(context)!.settings.arguments as Map<String, dynamic>;
```

📦 数据与存储

JSON处理

```dart
// 导入依赖
// flutter pub add dart:convert

// 解析JSON
Map<String, dynamic> user = jsonDecode(jsonString);
String name = user['name'];

// 生成JSON
String json = jsonEncode({'name': 'John', 'age': 30});

// 模型类转换
class User {
  final String name;
  final int age;
  
  User({required this.name, required this.age});
  
  factory User.fromJson(Map<String, dynamic> json) {
    return User(name: json['name'], age: json['age']);
  }
  
  Map<String, dynamic> toJson() => {'name': name, 'age': age};
}
```

本地存储

```dart
// 1. shared_preferences（键值对）
// flutter pub add shared_preferences

// 2. sqflite（SQLite数据库）
// flutter pub add sqflite

// 3. hive（高性能NoSQL）
// flutter pub add hive
```

网络请求

```dart
// http包
// flutter pub add http

import 'package:http/http.dart' as http;

Future<void> fetchData() async {
  final response = await http.get(Uri.parse('https://api.example.com/data'));
  if (response.statusCode == 200) {
    // 处理响应数据
  } else {
    // 处理错误
  }
}
```

📱 平台交互

平台通道

```dart
// Flutter调用原生代码
const platform = MethodChannel('com.example/channel');

Future<void> callNativeMethod() async {
  try {
    final result = await platform.invokeMethod('methodName', {'key': 'value'});
    print(result);
  } catch (e) {
    print('调用失败: $e');
  }
}
```

插件使用

```dart
// 添加插件到pubspec.yaml
dependencies:
  camera: ^0.9.4+5
  geolocator: ^8.2.0
  url_launcher: ^6.1.5
```

🎭 动画

隐式动画

```dart
AnimatedContainer(
  duration: Duration(seconds: 1),
  width: _selected ? 200 : 100,
  height: _selected ? 200 : 100,
  color: _selected ? Colors.red : Colors.blue,
)
```

显式动画

```dart
AnimationController controller;
Animation<double> animation;

@override
void initState() {
  super.initState();
  controller = AnimationController(
    duration: Duration(seconds: 2),
    vsync: this,
  );
  animation = Tween<double>(begin: 0, end: 300).animate(controller);
  controller.forward();
}

@override
Widget build(BuildContext context) {
  return AnimatedBuilder(
    animation: animation,
    builder: (context, child) {
      return Container(
        width: animation.value,
        height: animation.value,
        color: Colors.blue,
      );
    },
  );
}
```

🛠️ 调试与性能

调试工具

1. Flutter Inspector：检查Widget树
2. 性能面板：分析UI和GPU性能
3. 热重载：r键（保存时自动触发）
4. 热重启：R键
5. Dart DevTools：浏览器中的完整调试套件

性能优化

```dart
// 1. 使用const构造函数
const Text('静态文本')

// 2. 列表项使用Key
ListView.builder(itemBuilder: (context, index) => 
  ItemWidget(key: ValueKey(items[index].id), item: items[index])
)

// 3. 避免build方法中的重复计算
@override
Widget build(BuildContext context) {
  final expensiveValue = _calculateExpensiveValue(); // 错误：每次build都会计算
  
  return Widget;
}

// 正确做法：缓存计算结果
late final _expensiveValue = _calculateExpensiveValue();
```

📦 常用库

状态管理

· provider：推荐的状态管理方案
· riverpod：Provider的改进版，更安全
· flutter_bloc：BLoC模式实现
· mobx：响应式状态管理
· getx：轻量级但功能完整

网络与数据

· dio：强大的HTTP客户端
· http：官方HTTP包
· retrofit：类型安全的HTTP客户端生成器
· json_serializable：JSON序列化代码生成

UI与动画

· flutter_svg：SVG渲染
· cached_network_image：网络图片缓存
· carousel_slider：轮播图
· flutter_staggered_grid_view：瀑布流
· animations：预置动画效果

导航与路由

· go_router：声明式路由
· auto_route：类型安全路由生成
· fluro：灵活的路由框架

存储与数据库

· shared_preferences：键值对存储
· sqflite：SQLite数据库
· hive：高性能NoSQL数据库
· isar：跨平台数据库（替代sqflite）

工具与工具类

· intl：国际化与本地化
· url_launcher：打开URL/链接
· image_picker：选择图片
· permission_handler：权限处理
· flutter_local_notifications：本地通知

测试

· mockito：创建mock对象
· flutter_test：Flutter测试框架
· integration_test：集成测试

平台特定

· camera：相机访问
· geolocator：地理位置
· sensors：传感器数据
· webview_flutter：WebView组件

📝 最佳实践

1. Widget拆分：保持Widget小而专一
2. 代码格式化：使用dart format保持一致性
3. 类型安全：尽可能使用明确类型而非var
4. 错误处理：使用try/catch处理异步异常
5. 键的使用：列表项和需要维护状态的Widget使用Key
6. 常量优化：不变的Widget使用const构造函数
7. 异步处理：使用async/await而非嵌套回调
8. 空安全：充分利用Dart的空安全特性
