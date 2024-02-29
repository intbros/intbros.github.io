---
title: "flutter riverpod provider"
date: "2023-11-08 20:42:06"
tags: ["flutter", "riverpod"]
---



# provider ref
- ref.watch = 프로바이더의 값을 취득하고 변화를 구독합니다. 값의 변경이 발생하면, 위젯(widget)을 다시 빌드하거나 값을 구독(subscribed)하고 있는 위치에 상태 값을 전달 및 제공합니다.
- ref.listen = 프로바이더의 상태 값을 구독하거나 상태값이 변했을때 어떠한 행위를 취해야할 경우 사용합니다.
- ref.read = 프로바이더의 상태값을 취득합니다. 이벤트 콜백함수에 사용하기 유용한데 예를들어 버튼의 onPressed 콜백 함수에서 프로바이더의 필요한 상태값을 얻기위해서 사용할 수 있습니다.
> watch메소드는 비동기처리(asynchronously)에 호출하지 마세요.<br>
예를 들어 ElevatedButton의 onPressed 콜백 함수 안이나 initState 그리고 다른 State의 생명주기 안에서는 watch메소드를 호출하면 안됩니다.
이때는 ref.watch대신 ref.read메소드를 사용하는 것을 권장합니다.
<br>

# ref.watch와 ref.listen의 주요한 차이점
ref.watch와 ref.listen의 주요한 차이점은 ref.watch는 프로바이더 상태값이 변경이되면 widget/provider을 다시 빌드하지만 ref.listen은 함수를 호출한다는 점입니다. 함수는 커스텀된 함수이며 사용자에 따라 다르게 정의해서 사용할 수 있습니다.
> ElevatedButton의 onPressed 콜백함수 내부, initState 내부 그리고 다른 상태주기의 State상에서와 같이 listen메소드 또한 비동기(asynchronously)로 호출 가능한 곳에서는 사용을 피해야합니다.

# ref.read를 build 메소드 안에서 사용하지 마세요.
ref.read 메소드는 어떠한 부가적인 효과 없이 프로바이더의 상태를 얻기위한 방법을 제공합니다.
ref.read는 일반적으로 사용자 상호작용으로 발생가능한 트리거 함수내부에서 주로 사용합니다. 예를들어 버튼을 눌렀을떄 카운터의 값이 증가시키고 싶을때 ref.read메소드를 사용할 수 있습니다.

```
final counterProvider = StateProvider((ref) => 0);

Widget build(BuildContext context, WidgetRef ref) {
  StateController<int> counter = ref.read(counterProvider.notifier);
  return ElevatedButton(
    onPressed: () => counter.state++,
    child: const Text('button'),
  );
}
```

위의 코드 대신에 아래의 예시코드처럼 사용하는게 좋습니다.

```
final counterProvider = StateProvider((ref) => 0);

Widget build(BuildContext context, WidgetRef ref) {
  StateController<int> counter = ref.watch(counterProvider.notifier);
  return ElevatedButton(
    onPressed: () => counter.state++,
    child: const Text('button'),
  );
}
```

>가능한 ref.read사용을 피해주세요.
ref.read메소드는 watch 또는 listen이 어려운곳에서 사용할 수 있는 대응책으로 사용하되, 가능한 watch/listen를 사용해주세요. 여기서 더 추천하는 메소드는 watch 메소드입니다.

>read를 프로바이더 내부에서 호출하지 마세요.
<br>
```
final myProvider = Provider((ref) {
  // 여기서 'read'를 호출하는 것은 좋지 않습니다.
  final value = ref.read(anotherProvider);
});
```

### Notifier provider와 riverpod annotation 비교
```
class Test extends Notifier<List<int>> {
  @override
  List<int> build() {
    return [0, 2];
  }

  void increment() {
    state = [1, 2];
  }
}

@riverpod
class TestAnnotation extends _$TestAnnotation {
  @override
  List<int> build() => [1, 2];
}
```