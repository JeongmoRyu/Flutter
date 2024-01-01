# Flutter 앱 배포하는 법

- 공식 홈페이지 설명

[Build and release an Android app | Flutter (flutter-ko.dev)](https://flutter-ko.dev/deployment/android)

배포 후 디버깅 모드로 돌아가는 방법

### **Android Studio에서 디버그 모드로 변경:**

1. Android Studio를 엽니다.
2. 프로젝트 디렉터리에서 **`android`** 디렉터리로 이동합니다.
3. **`gradlew`** 또는 **`gradlew.bat`** 파일을 찾습니다.
4. 터미널 또는 명령 프롬프트에서 프로젝트 디렉터리로 이동한 후 다음 명령어를 실행합니다:
    
    ```bash
    ./gradlew app:assembleDebug
    
    ```
    

혹은

1. build.grandle에서 수정했던 release들을 주석처리만 해줘도 임시방편으로 사용할 수 있다.
