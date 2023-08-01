# basic

- framework
- 앱을 만들기 위해 사용하는 정확한 틀
- Fuchsia의 사용자 인터페이스와 애플리케이션을 만들기 위해 사용한다.
- 크로스 플랫폼(안드로이드, IOS) 애플리케이션 개발

- **Dart Language 사용**
- 웹 프로젝트를 하기 위해서는 Hummingbird 를 사용할 수 있지만 초기 단계임을 참고

## Flutter 시작하기

- https://flutter.dev

### SDK (Software Development Kit)

- 소스코드의 모음과 유틸리티
- sdk 다운받기
    - [Windows install | Flutter](https://docs.flutter.dev/get-started/install/windows)
    - c 프로그램파일에 압축을 풀기 X
- 환경변수 설정하기
    - 압축파일 주소 복사해서 path에 새로 만들어준다.

- Android studio
    - install
    - virtual devices
        - create
            - 안드로이드 이미지 다운받기
                - 저는 pie를 받았어요 ^^
    - plugin에서 dart 다운받기
        - 이미 받으셨다면 restart IDE 가 떠 있을거에요
    - plugin에서 flutter도 다운받기
        - 다운 받은 후에는 restart IDE 눌러서 새롭게 시작하기
    - flutter doctor
        - cmd에서 flutter doctor를 실행해보면 환경 점검을 할 수 있다.
        
        ```html
        [√] Flutter (Channel stable, 3.10.5, on Microsoft Windows [Version 10.0.19045.3086], locale ko-KR)
        [√] Windows Version (Installed version of Windows is version 10 or higher)
        [!] Android toolchain - develop for Android devices (Android SDK version 34.0.0)
            X cmdline-tools component is missing
              Run `path/to/sdkmanager --install "cmdline-tools;latest"`
              See https://developer.android.com/studio/command-line for more details.
            X Android license status unknown.
              Run `flutter doctor --android-licenses` to accept the SDK licenses.
              See https://flutter.dev/docs/get-started/install/windows#android-setup for more details.
        [√] Chrome - develop for the web
        [X] Visual Studio - develop for Windows
            X Visual Studio not installed; this is necessary for Windows development.
              Download at https://visualstudio.microsoft.com/downloads/.
              Please install the "Desktop development with C++" workload, including all of its default components
        [√] Android Studio (version 2022.2)
        [√] VS Code (version 1.80.0)
        [√] Connected device (3 available)
        [√] Network resources
        ```
        
    - android studio project 생성 → 애뮬레이터로 실행
    - visual studio 설치
- flutter doctor --android-licenses 실행

- 바로 프로젝트를 만들어본다.
    - src폴더에 src/flutter 이외에도
    - src/flutterwork폴더를 만들어서 \로 프로젝트 위치를 설정해준다.

- 애뮬레이터 생성
    - 애뮬레이터로 휴대폰 임시로 실행 가능