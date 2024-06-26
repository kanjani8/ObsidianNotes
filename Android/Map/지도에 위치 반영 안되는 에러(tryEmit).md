`MutableSharedFlow`의 `emit` 메서드를 사용하면서[[Coroutine]]Scope에서 호출하는 방법을 썼더니 해결되었다.


### 왜 문제가 발생했었나요?

1. **`tryEmit` vs `emit`**:
    
    - `tryEmit`: `tryEmit`은 비블로킹(non-blocking) 방식으로 동작합니다. 즉, ==`MutableSharedFlow`의 버퍼에 여유 공간이 없을 경우== 데이터를 추가하지 않고 실패합니다. 이는 코루틴 스코프가 필요하지 않으며, 즉시 성공하거나 실패합니다.
    - `emit`: 반면, `emit`은 서스펜딩(suspending) 함수로, 호출 시 코루틴을 일시 중단할 수 있습니다. 이는 `MutableSharedFlow`에 공간이 날 때까지 대기하므로, ==데이터가 성공적으로 흘러들어가도록 보장==합니다. 하지만 이를 사용하기 위해서는 코루틴 스코프가 필요합니다.
2. **코루틴 스코프의 부재**:
    
    - 초기 설정에서 `tryEmit`을 사용한 것은 코루틴 스코프 없이 데이터를 발행하려 했기 때문입니다. 하지만 `tryEmit`이 버퍼가 가득 찼을 때 실패했을 가능성이 있으며, 이는 데이터가 `SharedFlow`를 통해 흘러가지 않았을 수 있음을 의미합니다.
    - `emit`을 사용하면서 적절한 코루틴 스코프 (`CoroutineScope(Dispatchers.Main).launch{}`)를 제공하였기 때문에, 데이터가 안정적으로 흘러가고 `collect`가 호출될 수 있었습니다.

### 이 해결책을 계속 사용해야 하나요?

`emit`과 코루틴 스코프를 사용하는 방법은 `MutableSharedFlow`를 사용할 때 매우 효과적이고 안정적인 방법입니다. 이는 다음과 같은 이유로 권장됩니다:

- **데이터 손실 방지**: `emit`은 버퍼 공간이 확보될 때까지 대기하기 때문에, 데이터 손실 위험 없이 `MutableSharedFlow`로 데이터를 안정적으로 전송할 수 있습니다.
- **코루틴과의 일관성**: 코루틴을 사용하는 코텍스트에서는 `emit` 같은 서스펜딩 함수가 자연스럽고 코루틴의 동작 방식과 일관성을 유지합니다.

### 개발자로서 알아두면 좋은 것들

- **코루틴 스코프 관리**: [[Coroutine]]을 사용할 때는 적절한 스코프 관리가 중요합니다. `ViewModel`의 `viewModelScope`, `Activity`의 `lifecycleScope` 등 생명주기를 고려한 스코프 사용이 필요합니다.
- **데이터 흐름의 안정성 보장**: 앱에서 중요한 데이터 흐름을 관리할 때는 데이터 손실이 없도록 주의해야 합니다. `SharedFlow`, `StateFlow` 등을 사용하여 데이터 상태를 관리하고, 이벤트를 처리하는 방식을 학습하는 것이 좋습니다.

이러한 변경을 통해 앱의 기능이 보다 안정적으로 작동하게 될 것입니다. 또한, 이와 같은 패턴은 다양한 앱 개발 상황에서 유용하게 적용될 수 있으므로, 코루틴과 흐름 제어에 대해 더 깊이 이해하고 연습하는 것이 중요합니다.