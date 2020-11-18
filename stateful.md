# Шаблоны для Stateful виджетов
  
  
| Name   | Expression   | Default value                                       | Skip if defined |
|--------|--------------|-----------------------------------------------------|-----------------|
| `NAME` |              | `capitalize(camelCase(fileNameWithoutExtension()))` |                 |
  
---
  
`stful`
```dart
import 'package:flutter/widgets.dart';
import 'package:flutter/foundation.dart';

@immutable
class $NAME$ extends StatefulWidget {
  const $NAME$({
    Key key,
  })  : super(key: key);

  @override
  State<$NAME$> createState() => _$NAME$State();

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '$NAME$ StatefulWidget',
            ),
          ),
      );
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
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '_$NAME$State State<$NAME$>',
            ),
          ),
      );

  @override
  Widget build(BuildContext context) =>
    const Placeholder();$END$
}
```
---
  
`stfulWithChild`
```dart
import 'package:flutter/widgets.dart';
import 'package:flutter/foundation.dart';

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

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '$NAME$ StatefulWidget',
            ),
          ),
      );
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
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '_$NAME$State State<$NAME$>',
            ),
          ),
      );
  
  @override
  Widget build(BuildContext context) =>
    widget.child;$END$
}
```
---
  
`stfulAnimation`
```dart
import 'package:flutter/widgets.dart';
import 'package:flutter/foundation.dart';

@immutable
class $NAME$ extends StatefulWidget {
  final Widget child;
  final Duration duration;
  const $NAME$({
    @required this.child,
    this.duration = const Duration(milliseconds: 250),
    Key key,
  })  : assert(child != null, 'Field child in widget $NAME$ must not be null'),
        assert(duration != null, 'Field duration in widget $NAME$ must not be null'),
        super(key: key);

  @override
  State<$NAME$> createState() => _$NAME$State();

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '$NAME$ StatefulWidget',
            ),
          ),
      );
}

class _$NAME$State extends State<$NAME$> with SingleTickerProviderStateMixin {

  AnimationController _animationController;

  @override
  void initState() {
    super.initState();
    _animationController = AnimationController(
      vsync: this,
      duration: widget.duration ?? const Duration(milliseconds: 250),
    );
    // Первичная инициализация виджета
  }

  @override
  void didUpdateWidget($NAME$ oldWidget) {
    super.didUpdateWidget(oldWidget);
    if (oldWidget.duration != widget.duration) {
      _animationController.duration = widget.duration ?? const Duration(milliseconds: 250);
    }
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
    _animationController?.dispose();
    super.dispose();
  }

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) => super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '_MyState State<My>',
            ),
          )
          ..add(
            FlagProperty(
              'currently animating',
              value: _animationController?.isAnimating,
              ifTrue: 'yes',
              ifFalse: 'no',
              showName: true,
            ),
          )
          ..add(
            StringProperty(
              'length of time this animation should last',
              _animationController?.duration?.toString(),
            ),
          )
          ..add(
            StringProperty(
              'current status of this animation',
              _animationController?.status?.toString(),
            ),
          )
          ..add(
            DoubleProperty(
              'current value of the animation',
              _animationController?.value,
            ),
          ),
      );
  
  @override
  Widget build(BuildContext context) => FadeTransition(
        opacity: Tween<double>(
          begin: 0,
          end: .75,
        ).animate(_animationController),
        child: ScaleTransition(
          scale: CurvedAnimation(
            parent: _animationController,
            curve: const Interval(
              0.5,
              1,
              curve: Curves.easeOut,
            ),
          ),
          child: RepaintBoundary(
            child: widget.child,$END$
          ),
        ),
      );

  Future<void> _reverse() async {
    if (_animationController.value == 0) return;
    try {
      await _animationController.reverse().orCancel;
    } on TickerCanceled {} // ignore: empty_catches
  }

  Future<void> _forward() async {
    if (_animationController.value == 1) return;
    try {
      await _animationController.forward().orCancel;
    } on TickerCanceled {} // ignore: empty_catches
  }
}
```
---
  
`stfulPopObserver`
```dart
import 'package:flutter/widgets.dart';
import 'package:flutter/foundation.dart';

@immutable
class $NAME$ extends StatefulWidget {
  final Widget child;
  final Duration duration;
  const $NAME$({
    @required this.child,
    this.duration = const Duration(milliseconds: 250),
    Key key,
  })  : assert(child != null, 'Field child in widget $NAME$ must not be null'),
        assert(duration != null, 'Field duration in widget $NAME$ must not be null'),
        super(key: key);

  @override
  State<$NAME$> createState() => _$NAME$State();

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '$NAME$ StatefulWidget',
            ),
          ),
      );
}

// ignore: prefer_mixin
class _$NAME$State extends State<$NAME$> with SingleTickerProviderStateMixin, WidgetsBindingObserver {
  bool get _canPop => (_animationController?.value ?? 0) > 0;
  AnimationController _animationController;

  @override
  void initState() {
    super.initState();
    _animationController = AnimationController(
      vsync: this,
      duration: widget.duration ?? const Duration(milliseconds: 250),
    )..addStatusListener((status) {
        if (status == AnimationStatus.dismissed) {
          WidgetsBinding.instance.removeObserver(this);
        } else {
          WidgetsBinding.instance.addObserver(this);
        }
      });
    // Первичная инициализация виджета
  }

  @override
  void didUpdateWidget(My oldWidget) {
    super.didUpdateWidget(oldWidget);
    if (oldWidget.duration != widget.duration) {
      _animationController.duration =
          widget.duration ?? const Duration(milliseconds: 250);
    }
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
    _animationController?.dispose();
    super.dispose();
  }

  /// Срабатывает при нажатии на кнопку "назад"
  /// Когда возвращается Future.value(true) - событие дальше не передается (например навигатору)
  @override
  Future<bool> didPopRoute() {
    if (_canPop) {
      _pop();
      return SynchronousFuture(true);
    } else {
      return SynchronousFuture(false);
    }
  }

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '_MyState State<My>',
            ),
          )
          ..add(
            FlagProperty(
              'can pop',
              value: _canPop,
              ifTrue: 'yes',
              ifFalse: 'no',
              showName: true,
            ),
          ),
      );

  @override
  Widget build(BuildContext context) => AnimatedBuilder(
        animation: _animationController,
        builder: (context, child) =>
            _animationController.value == 0 ? const SizedBox.shrink() : child,
        child: FadeTransition(
          opacity: Tween<double>(
            begin: 0,
            end: 1,
          ).animate(
            CurvedAnimation(
              parent: _animationController,
              curve: const Interval(
                0.25,
                1,
                curve: Curves.easeOut,
              ),
            ),
          ),
          child: GestureDetector(
            onTap: _pop,
            child: DecoratedBox(
              decoration: const BoxDecoration(
                color: Color(0x61000000),
              ),
              child: SizedBox.expand(
                child: widget.child,
              ),
            ),
          ),
        ),
      );

  Future<void> _reverse() async {
    if (_animationController.value == 0) return;
    try {
      await _animationController.reverse().orCancel;
    } on TickerCanceled {} // ignore: empty_catches
  }

  Future<void> _forward() async {
    if (_animationController.value == 1) return;
    try {
      await _animationController.forward().orCancel;
    } on TickerCanceled {} // ignore: empty_catches
  }

  void _pop() => _reverse();
}
```
---

`stfulWithStateScope`
```dart
import 'package:flutter/widgets.dart';
import 'package:flutter/foundation.dart';

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

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '$NAME$ StatefulWidget',
            ),
          ),
      );
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
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '_$NAME$State State<$NAME$>',
            ),
          ),
      );

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

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              'Scope of $NAME$',
            ),
          )
          ..add(
            ObjectFlagProperty<_KeyboardQueryState>(
              '_$NAME$State',
              state,
              ifNull: 'none',
            ),
          )
          ..defaultDiagnosticsTreeStyle = DiagnosticsTreeStyle.offstage,
      );
}
```
  