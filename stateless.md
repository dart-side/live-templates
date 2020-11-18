# Шаблоны для Stateless виджетов
  
  
| Name   | Expression   | Default value                                       | Skip if defined |
|--------|--------------|-----------------------------------------------------|-----------------|
| `NAME` |              | `capitalize(camelCase(fileNameWithoutExtension()))` |                 |
  
---
  
`stless`
```dart
import 'package:flutter/widgets.dart';
import 'package:flutter/foundation.dart';

@immutable
class $NAME$ extends StatelessWidget {
  const $NAME$({
    Key key,
  })  : super(key: key);

  @override
  Widget build(BuildContext context) =>
    const Placeholder();$END$

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '$NAME$ StatelessWidget',
            ),
          ),
      );
}
```
---
  
`stlessWithChild`
```dart
import 'package:flutter/widgets.dart';
import 'package:flutter/foundation.dart';

@immutable
class $NAME$ extends StatelessWidget {
  final Widget child;
  const $NAME$({
    @required this.child,
    Key key,
  })  : assert(child != null, 'Field child in widget $NAME$ must not be null'),
        super(key: key);

  @override
  Widget build(BuildContext context) =>
    child;$END$

  @override
  void debugFillProperties(DiagnosticPropertiesBuilder properties) =>
      super.debugFillProperties(
        properties
          ..add(
            StringProperty(
              'description',
              '$NAME$ StatelessWidget',
            ),
          ),
      );
}
```
  