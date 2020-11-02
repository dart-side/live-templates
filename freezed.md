# Шаблоны для Freezed
  
  
| Name                       | Expression                   | Default value                                       | Skip if defined |
|----------------------------|------------------------------|-----------------------------------------------------|-----------------|
| `NAME`                     |                              | `capitalize(camelCase(fileNameWithoutExtension()))` |                 |
| `fileNameWithoutExtension` | `fileNameWithoutExtension()` | `""`                                                | `x`             |

  
---
  
`freezed`
```dart
import 'package:freezed_annotation/freezed_annotation.dart';

part '$fileNameWithoutExtension$.freezed.dart';

@freezed
abstract class $NAME$ with _$$$NAME$ {
  const factory $NAME$({
      @required int id,
      $END$
  }) = _$NAME$;
}
```
---
  
`freezedWithJSON`
```dart
import 'package:freezed_annotation/freezed_annotation.dart';

part '$fileNameWithoutExtension$.freezed.dart';
part '$fileNameWithoutExtension$.g.dart';

@freezed
abstract class $NAME$ with _$$$NAME$ {
  const factory $NAME$({
    @required @JsonKey(name: 'id', required: true, disallowNullValue: true) int id,
    $END$
  }) = _$NAME$;

  /// Generate Class from Map<String, dynamic>
  factory $NAME$.fromJson(Map<String, dynamic> json) => _$$$NAME$FromJson(json);
}
```
---
  
`freezedUnion`
```dart
import 'package:freezed_annotation/freezed_annotation.dart';

part '$fileNameWithoutExtension$.freezed.dart';
part '$fileNameWithoutExtension$.g.dart';

@freezed
abstract class $NAME$ with _$$$NAME$ {
  const $NAME$._();

  const factory $NAME$.a({
    @required @JsonKey(name: 'id', required: true, disallowNullValue: true) int id,
    $END$
  }) = $NAME$A;

  const factory $NAME$.b({
    @required @JsonKey(name: 'id', required: true, disallowNullValue: true) int id,
    $END$
  }) = $NAME$B;

  /// Generate Class from Map<String, dynamic>
  factory $NAME$.fromJson(Map<String, dynamic> json) => _$$$NAME$FromJson(json);
}
``` 