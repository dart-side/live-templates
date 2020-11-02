# Шаблоны для Stateful виджетов
  
  
| Name   | Expression   | Default value                                       | Skip if defined |
|--------|--------------|-----------------------------------------------------|-----------------|
| `NAME` |              | `capitalize(camelCase(fileNameWithoutExtension()))` |                 |
  
---
  
`stful`
```dart
@immutable
class $NAME$ extends StatefulWidget {
  const $NAME$({
    Key key,
  })  : super(key: key);
  @override
  State<$NAME$> createState() => _$NAME$State();
}

class _$NAME$State extends State<$NAME$> {

  @override
  void initState() {
    super.initState();
    // Первичная инициализация виджета
  }

  @override
  void didUpdateWidget($NAME$ oldWidget) {
    super.didUpdateWidget(oldWidget);
    // Конфигурация виджета изменилась
  }
  
  @override
  void didChangeDependencies() {
    super.didChangeDependencies();
    // Изменилась конфигурация InheritedWidget'ов
    // Также вызывается после initState, но до build'а
  }
  
  @override
  void dispose() {
    // Перманетное удаление стейта из дерева
    super.dispose();
  }
    
  @override
  Widget build(BuildContext context) =>
    const Placeholder();$END$
}
```
---
  
`stfulOfContextWithChild`
```dart
@immutable
class $NAME$ extends StatefulWidget {
  final Widget child;
  const $NAME$({
    @required this.child,
    Key key,
  })  : assert(child != null, 'Field child in widget $NAME$ must not be null'),
        super(key: key);
  /// Для поиска _$NAME$State в контексте
  static _$NAME$State of(BuildContext context) =>
    context.findAncestorStateOfType<_$NAME$State>();
  @override
  State<$NAME$> createState() => _$NAME$State();
}

class _$NAME$State extends State<$NAME$> {

  @override
  void initState() {
    super.initState();
    // Первичная инициализация виджета
  }

  @override
  void didUpdateWidget($NAME$ oldWidget) {
    super.didUpdateWidget(oldWidget);
    // Конфигурация виджета изменилась
  }
  
  @override
  void didChangeDependencies() {
    super.didChangeDependencies();
    // Изменилась конфигурация InheritedWidget'ов
    // Также вызывается после initState, но до build'а
  }
  
  @override
  void dispose() {
    // Перманетное удаление стейта из дерева
    super.dispose();
  }
  
  @override
  Widget build(BuildContext context) =>
    widget.child;$END$
}
```
---
  
`stfulWithChild`
```dart
@immutable
class $NAME$ extends StatefulWidget {
  final Widget child;
  const $NAME$({
    @required this.child,
    Key key,
  })  : assert(child != null, 'Field child in widget $NAME$ must not be null'),
        super(key: key);
  @override
  State<$NAME$> createState() => _$NAME$State();
}

class _$NAME$State extends State<$NAME$> {

  @override
  void initState() {
    super.initState();
    // Первичная инициализация виджета
  }

  @override
  void didUpdateWidget($NAME$ oldWidget) {
    super.didUpdateWidget(oldWidget);
    // Конфигурация виджета изменилась
  }
  
  @override
  void didChangeDependencies() {
    super.didChangeDependencies();
    // Изменилась конфигурация InheritedWidget'ов
    // Также вызывается после initState, но до build'а
  }
  
  @override
  void dispose() {
    // Перманетное удаление стейта из дерева
    super.dispose();
  }
  
  @override
  Widget build(BuildContext context) =>
    widget.child;$END$
}
```
---
  
`stfulWithStateScope`
```dart
import 'package:flutter/widgets.dart';

@immutable
class $NAME$ extends StatefulWidget {
  final Widget child;
  const $NAME$({
    @required this.child,
    Key key,
  })  : assert(child != null, 'Field child in widget $NAME$ must not be null'),
        super(key: key);
  static _$NAME$State of(BuildContext context) =>
      _$NAME$Scope.of(context)?.state;

  @override
  State<$NAME$> createState() => _$NAME$State();
}

class _$NAME$State extends State<$NAME$> {

  @override
  void initState() {
    super.initState();
    // Первичная инициализация виджета
  }

  @override
  void didUpdateWidget($NAME$ oldWidget) {
    super.didUpdateWidget(oldWidget);
    // Конфигурация виджета изменилась
  }
  
  @override
  void didChangeDependencies() {
    super.didChangeDependencies();
    // Изменилась конфигурация InheritedWidget'ов
    // Также вызывается после initState, но до build'а
  }
  
  @override
  void dispose() {
    // Перманетное удаление стейта из дерева
    super.dispose();
  }

  @override
  Widget build(BuildContext context) =>
      _$NAME$Scope(
        state: this,
        child: widget.child,
      );
}

@immutable
class _$NAME$Scope extends InheritedWidget {
  final _$NAME$State state;

  const _$NAME$Scope({
    @required Widget child,
    @required this.state,
    Key key,
  })
    : assert(child != null, 'Field child in widget _$NAME$Scope must not be null')
    , assert(state is _$NAME$State, '_$NAME$State must not be null')
    , super(key: key, child: child);

  /// Find _$NAME$Scope in BuildContext
  static _$NAME$Scope of(BuildContext context) =>
      context.dependOnInheritedWidgetOfExactType<_$NAME$Scope>();

  @override
  bool updateShouldNotify(_$NAME$Scope oldWidget) =>
      !identical(state, oldWidget.state)
      || state != oldWidget.state;
}
```
  