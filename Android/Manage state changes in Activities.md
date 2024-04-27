###   1. onCreate()

`onCreate()` 메서드는 액티비티가 생성될 때 호출됩니다. 여기서는 레이아웃을 설정하고 (`setContentView()`), 초기화 코드를 실행하며, 뷰와 데이터를 바인딩하는 등의 작업을 수행합니다. 모든 액티비티는 이 메서드를 구현해야 하며, `super.onCreate()`를 호출하는 것으로 시작해야 합니다.

kotlinCopy code

`override fun onCreate(savedInstanceState: Bundle?) {     super.onCreate(savedInstanceState)     setContentView(R.layout.activity_main)     // 초기화 작업을 여기에 수행합니다. }`

### 2. onStart()

`onStart()` 메서드는 액티비티가 사용자에게 보여지기 직전에 호출됩니다. 이 시점에서 액티비티는 아직 사용자와 상호작용하기 시작하지 않았습니다. 이 메서드는 액티비티가 사용자에게 보이는 것을 준비하는 데 사용됩니다.

kotlinCopy code

`override fun onStart() {     super.onStart()     // 액티비티가 사용자에게 보여지기 직전의 로직을 실행합니다. }`

### 3. `onResume()`

`onResume()` 메서드는 액티비티가 사용자와 상호작용하기 직전에 호출됩니다. 이 시점에서 액티비티는 화면에 보이고, 사용자 입력을 받을 준비가 되었습니다. 여기서 일시 중지된 애니메이션을 다시 시작하거나, 실행 중지된 멀티미디어를 재개할 수 있습니다.

kotlinCopy code

`override fun onResume() {     super.onResume()     // 액티비티가 활성화되고 사용자와 상호작용을 시작합니다. }`

### 4. `onPause()`

`onPause()` 메서드는 액티비티가 다른 액티비티에 의해 부분적으로 가려질 때 호출됩니다. 이 메서드는 주로 CPU 사용을 많이하는 작업을 중지하거나, 비디오 재생 같은 자원을 해제하는 데 사용됩니다. 여기서 수행된 작업은 빠르게 완료되어야 합니다.

kotlinCopy code

`override fun onPause() {     super.onPause()     // 액티비티가 일시 중지될 때 필요한 상태 저장 및 자원 해제를 수행합니다. }`

### 5. `onStop()`

`onStop()` 메서드는 액티비티가 사용자에게 더 이상 보이지 않을 때 호출됩니다. 예를 들어, 새로운 액티비티가 시작되어 기존 액티비티를 완전히 가릴 때 이 메서드가 실행됩니다. 여기서 데이터의 지속적인 저장, 자원 해제, 혹은 추적 중지 같은 작업을 수행할 수 있습니다.

kotlinCopy code

`override fun onStop() {     super.onStop()     // 액티비티가 보이지 않게 될 때의 로직을 실행합니다. }`