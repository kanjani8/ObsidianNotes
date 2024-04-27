Android 6.0 (API 레벨 23) 이상에서는 앱이 실행 중에 사용자에게 중요한 권한을 요청해야 합니다. 이는 사용자가 앱의 권한을 더 잘 이해하고 제어할 수 있도록 하기 위함입니다. 예를 들어, 위치 정보나 신체 센서 데이터와 같은 민감한 정보에 접근하려면 런타임에 사용자의 명시적인 승인이 필요합니다.

### 권한 요청 과정

1. **권한 확인**: 먼저 앱이 필요한 권한을 이미 가지고 있는지 확인합니다. `ContextCompat.checkSelfPermission()` 메소드를 사용하여 특정 권한이 이미 승인되었는지 확인할 수 있습니다.
    
2. **권한 요청**: 필요한 권한이 없는 경우, `ActivityCompat.requestPermissions()` 메소드를 사용하여 사용자에게 권한을 요청합니다. 사용자는 대화 상자를 통해 요청을 승인하거나 거부할 수 있습니다.
    
3. **요청 결과 처리**: 사용자의 응답은 `onRequestPermissionsResult()` 콜백 메소드를 통해 받게 됩니다. 이 메소드를 오버라이드하여 사용자가 권한 요청을 승인했는지, 거부했는지에 따라 적절한 조치를 취할 수 있습니다.
    

### 예시 코드

아래 코드는 위치 권한을 요청하는 간단한 예시입니다.

`public class MainActivity extends AppCompatActivity {
    private static final int PERMISSIONS_REQUEST_ACCESS_FINE_LOCATION = 1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        getLocationPermission();
    }

    private void getLocationPermission() {
        /*
         * 위치 권한이 이미 있는지 확인합니다.
         * 권한이 있으면 앱의 동작을 계속합니다.
         * 권한이 없으면 사용자에게 권한 요청을 합니다.
         */
        if (ContextCompat.checkSelfPermission(this.getApplicationContext(),
                android.Manifest.permission.ACCESS_FINE_LOCATION)
                == PackageManager.PERMISSION_GRANTED) {
            // 권한이 이미 있을 때의 동작
        } else {
            ActivityCompat.requestPermissions(this,
                    new String[]{android.Manifest.permission.ACCESS_FINE_LOCATION},
                    PERMISSIONS_REQUEST_ACCESS_FINE_LOCATION);
        }
    }

    @Override
    public void onRequestPermissionsResult(int requestCode,
                                           @NonNull String[] permissions,
                                           @NonNull int[] grantResults) {
        switch (requestCode) {
            case PERMISSIONS_REQUEST_ACCESS_FINE_LOCATION: {
                // 요청이 취소되면 결과 배열이 비어있습니다.
                if (grantResults.length > 0
                        && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                    // 권한이 승인되었을 때의 동작
                } else {
                    // 권한이 거부되었을 때의 동작
                }
            }
        }
    }
}
`

이 예시에서는 위치 권한을 요청하는 과정을 보여줍니다. 먼저 `getLocationPermission()` 메소드에서 권한의 상태를 확인하고, 필요한 경우 사용자에게 권한을 요청합니다. 사용자의 응답은 `onRequestPermissionsResult()`에서 처리됩니다.

런타임 권한 요청은 사용자의 프라이버시를 존중하고 앱의 투명성을 높이는 데 중요한 역할을 합니다. 사용자에게 권한에 대한 명확한 정보를 제공하고, 권한 사용의 이유를 명시하는 것이 좋습니다.