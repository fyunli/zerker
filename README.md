<div align=center><img src="https://github.com/flutterkit/zerkerdocs/blob/master/logo/logo.png?raw=true"/></div>

## What is Zerker

Zerker is a flexible and lightweight flutter canvas graphic animation library.

With `Zerker`, you can create a lot of seemingly cumbersome animation effects, such as animated animations, pop-up animations, scene transitions, icon effects, and more.

At the same time, you can create a lot of simple games with Zerker. Zerker contains elements such as sprites, scrolling backgrounds, and atlases, making it easy to create game worlds with them.

#### More detailed documentation about Zerker is here [https://flutterkit.github.io/zerkerdocs/](https://flutterkit.github.io/zerkerdocs/)

![An image](https://flutterkit.github.io/zerkerdocs/images/fp.png)

## Installation

Add this to your package's pubspec.yaml file, And execute the command`flutter pub get`:

```yaml
dependencies:
  zerker: <latest_version_here>
```

###### More detailed installation steps, you can refer to here. [https://pub.dev/packages/zerker#-installing-tab-](https://pub.dev/packages/zerker#-installing-tab-)

## Getting started

### Import the package
```
import 'package:zerker/zerker.dart';
```

### Useage

#### Create a zerker widget

```dart
class _MyHomePageState extends State<MyHomePage> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(
          title: Text(widget.title),
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Text(
                'The Zerker Demo',
              ),
              Container(
                color: Colors.amber[600],
                width: 360.0,
                height: 360.0,
                child: Zerker(app: MyZKApp()),
              ),
            ],
          ),
        ));
  }
}
```

#### Create your Zerker class inherited from ZKApp

```dart
class MyZKApp extends ZKApp {
  @override
  bool interactive = true;

  @override
  bool clip = true;

  @override
  init() {
    super.init();
    /// init zerker scene
  }

  @override
  update(int time) {
  	super.update(time);
  }
}
```

#### Initialize the scene and create elements in the init function

```dart
/// Create a zerker sprite
ZKSprite bigboy = ZKSprite(key: "bigboy")
	..position.x = size.width / 2
	..position.y = size.height / 2
	..animator.make("front", [0, 1, 2, 3, 4])
	..animator.make("left", ['5-9'])
	..animator.make("after", ['10-14'])
	..animator.make("right", ['15-19'])
	..onTapDown = (event) {
		bigboy.animator.play("right", 8, true);
   };
   
stage.addChild(bigboy);

/// Create a zerker text
ZKText  text = ZKText()
	..setPosition(100, 100)
	..text = "hello world"
	..setStyle(color: Colors.blueGrey, backgroundColor: Colors.red[50]);
	
stage.addChild(_text);
```


---

## License
Zerker is licensed under MIT license. View license. [https://github.com/flutterkit/zerker/blob/master/LICENSE](https://github.com/flutterkit/zerker/blob/master/LICENSE)