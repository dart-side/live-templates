# Шаблоны для Stateless виджетов
  
  
| Name   | Expression   | Default value                                       | Skip if defined |
|--------|--------------|-----------------------------------------------------|-----------------|
| `NAME` | ``           | `capitalize(camelCase(fileNameWithoutExtension()))` | ``              |
  
---
  
`stless`
```dart
@immutable
class $NAME$ extends StatelessWidget {
  const $NAME$({
    Key key,
  })  : super(key: key);
  @override
  Widget build(BuildContext context) =>
    const Placeholder();$END$
}
```
---
  
`stlessWithChild`
```dart
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
}
```
  