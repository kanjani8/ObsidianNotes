There are a few differences with composable functions.

![It has composable annotation  a function name with parameters  it returns noting](https://developer.android.com/static/codelabs/basic-android-kotlin-compose-first-app/img/4e79342589823240.png)

- You add the `@Composable` annotation before the function.
- `@Composable` function names are capitalized.
- `@Composable` functions can't return anything.
- `@Composable` functions explain a part  of UI

```
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
	Text(text = "Hello $name!")
}
```


@주석 -  코드에 추가 정보를 첨부하는 방법
 이 정보는 Jetpack Compose 컴파일러와 같은 도구가 앱의 코드를 이해하는 데 도움이 됩니다.

- 파스칼 표기법을 사용하여 이름을 지정해야 합니다(MUST).
파스칼 표기법은 복합어에서 각 단어의 첫 글자를 대문자로 표기하는 명명 규칙
파스칼 표기법과 카멜 표기법의 차이점은 파스칼 표기법의 경우 모든 단어를 대문자로 표기하고, 카멜 표기법의 경우 첫 번째 단어는 대문자 또는 소문자일 수 있습니다.