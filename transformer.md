# Шаблоны для StreamTransform
  
  
| Name               | Expression           | Default value                                       | Skip if defined |
|--------------------|----------------------|-----------------------------------------------------|-----------------|
| `NAME`             |                      | `capitalize(camelCase(fileNameWithoutExtension()))` |                 |
| `decapitalizeNAME` | `decapitalize(NAME)` | `""`                                                | `x`             |
| `FROM`             |                      | `"Object"`                                          |                 |
| `TO`               |                      | `"Object"`                                          |                 |
  
---
  
`transformer<S, T>`
```dart
@immutable
class $NAME$StreamTransformer<$FROM$, $TO$> extends StreamTransformerBase<$FROM$, $TO$> {

  const $NAME$StreamTransformer();

  @override
  Stream<$TO$> bind(Stream<$FROM$> stream) {
    StreamSubscription<$FROM$> sub;
    final sc = StreamController<$TO$>(
        onPause: () => sub.pause(),
        onResume: () => sub.resume(),
        onCancel: () => sub.cancel(),
        sync: true,
      ) as SynchronousStreamController<$TO$>;
    sub = stream.listen((value) {
        $END$
        sc.add(value as $TO$);
      },
      onDone: sc.close,
      onError: sc.addError,
      cancelOnError: true,
    );
    return stream.isBroadcast
      ? sc.stream.asBroadcastStream()
      : sc.stream;
  }
}

/// sourceStream.$decapitalizeNAME$<$TO$>()
extension $NAME$Extensions<$FROM$> on Stream<$FROM$> {
  Stream<$TO$> $decapitalizeNAME$<$TO$>() =>
    transform<$TO$>($NAME$StreamTransformer<$FROM$, $TO$>());
}
```