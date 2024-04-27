Wear OS에서 센서 데이터를 읽는 과정은 주로 `SensorManager` API를 사용하여 구현됩니다. 여기서는 Wear OS 앱에서 심박수 센서를 예로 들어 센서 데이터 읽기 과정을 자세히 설명하겠습니다. 이 과정은 다른 유형의 센서에도 비슷하게 적용될 수 있습니다.

### 1. 센서 권한 요청하기 [[Permission]]

먼저, `AndroidManifest.xml` 파일에 필요한 권한을 추가합니다. 심박수 센서를 사용하기 위해서는 `BODY_SENSORS` 권한이 필요합니다.

xmlCopy code

`<uses-permission android:name="android.permission.BODY_SENSORS"/>`

Android 6.0 (API 레벨 23) 이상에서는 런타임에 사용자로부터 이 권한을 요청해야 합니다.
![[Pasted image 20240412091244.png]]
### 2. `SensorManager`와 센서 인스턴스 가져오기

`SensorManager`를 사용하여 시스템의 센서 서비스에 접근하고, 특정 센서에 대한 인스턴스를 가져옵니다. 심박수 센서를 예로 들면 다음과 같습니다.

kotlin code

`val sensorManager = getSystemService(Context.SENSOR_SERVICE) as SensorManager val heartRateSensor = sensorManager.getDefaultSensor(Sensor.TYPE_HEART_RATE)`

Sensor Manager  사용 코드 상세 예시

### 3. 센서 이벤트 리스너 등록하기

센서 데이터를 읽기 위해 `SensorEventListener`를 구현하고, 해당 리스너를 원하는 센서에 등록합니다. 리스너는 센서 값이 변경될 때마다 호출됩니다.

kotlinCopy code

`val sensorListener = object : SensorEventListener {     override fun onSensorChanged(event: SensorEvent) {         if (event.sensor.type == Sensor.TYPE_HEART_RATE) {             val heartRate = event.values[0]             // 여기에서 심박수 데이터를 사용하세요.         }     }      override fun onAccuracyChanged(sensor: Sensor, accuracy: Int) {         // 센서 정확도가 변경될 때 처리할 코드를 여기에 작성합니다.     } }  sensorManager.registerListener(sensorListener, heartRateSensor, SensorManager.SENSOR_DELAY_NORMAL)`

### 4. 센서 리스너 해제하기

앱이 더 이상 센서 데이터를 필요로 하지 않거나, 액티비티가 중지될 때 센서 리스너를 해제해야 합니다. 이는 배터리 소모를 줄이고 시스템 자원을 효율적으로 사용하기 위함입니다.

kotlinCopy code

`sensorManager.unregisterListener(sensorListener)`

이 과정을 통해 Wear OS 앱에서 심박수와 같은 센서 데이터를 효과적으로 읽고 사용할 수 있습니다. 체온이나 혈압과 같은 다른 센서 데이터를 다루려면 해당 센서에 맞는 `Sensor.TYPE_...`을 사용하고, 필요한 권한을 요청해야 합니다. 현재 Wear OS API에서는 직접적으로 체온이나 혈압을 측정하는 센서 타입을 제공하지 않기 때문에, 이런 기능을 구현하려면 외부 장치를 사용해야 할 수도 있습니다.