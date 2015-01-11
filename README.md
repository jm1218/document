[[ cordova 설치 및 프로젝트 생성하기 ]]

## 해당 가이드는 cordova 3.5 / windows /a ndroid 기반으로 작성되었습니다.
## iOs는 Xcode등 별도의 개발환경이 필요합니다.(window에서 Xcode설치 불가)

============================= 기본 환경설정 =============================

1. intelliJ 설치 후 설정 잡기
http://www.jetbrains.com/idea/download/

2. node.js 설치
http://www.nodejs.org/

3. apache ant 설치(zip파일)
http://ant.apache.org/bindownload.cgi

4. android sdk stand-alone version 설치
http://developer.android.com/sdk/index.html#download

5. sdk-manager 실행 후 안드로이드 버전 및 extra lib 설치

7. 환경변수 추가(각자 환경에 맞도록)
C:\developer\build tools\apache-ant-1.9.4\bin; 		-- ant build
C:\developer\android\android-sdk\tools;		        -- android tools
C:\developer\android\android-sdk\platform-tools;	-- abd


============================= 프로젝트 생성 및 실행 =============================

※ cordova install(%users%\AppData\Roaming\npm\node_modules\cordova 경로에 프로그램 생성)
 >> npm intall -g cordova

※ cordova version upgrade(필요한 경우에만)
 >> npm upgrade -g cordova

※ 프로젝트 생성(현재 경로에 생성됨, 두번째, 세번째 값은 옵션)  
 >> cordova create [projectName] [reverse domain-style identifier] [application's display text]
 ex> cordova create Test com.co.test 'TestProject'

※ platform 추가(해당 프로젝트 경로에서 실행 /  프로그램 내부적으로 각 플랫폼 sdk의 command명령을 통해 프로젝트를 생성하므로 각 플랫폼 sdk가 path에 등록 되어 있어야함)
 >> cordova platform add android
 >> cordova platform add ios

※ plugin 추가(해당 프로젝트 경로에서 실행)
 >> cordova plugin add [plugin url]

※ 빌드(해당 프로젝트 경로에서 실행)
 >> cordova build android
 >> cordova build ios

※ 설치 후 실행(해당 프로젝트 경로에서 실행)
 >> cordova install android

※ 빌드, 설치, 실행 한번에(해당 프로젝트 경로에서 실행)
 >> cordova run android

## 프로젝트 생성 후 www(web resource)만 IDE 에서 imort후 개발 후 cordova command line interface를 통해 device에서 실행해 볼 수 있습니다.
## 대부분은 웹에서 개발할 수 있으나, plugin을 연동해야 되는 부분은 웹에서 소스 작성후 device에서 확인해야 합니다.
## check out 받은 프로젝트를 실행할때는 빌드환경이 프로젝트 생성자에 맞게 세팅이 되어 있으므로, local.properties파일에서 sdk경로를 자신의 환경에 맞게 설정해야 합니다.

============================= 프로젝트 구조 =============================
※ 생성된 프로젝트 구조

[hooks] -- cordova 명령을 커스터 마이징 할수 있는 스크립트를 포함하는 디렉토리(잘모르겟음)

[platfroms] -- 추가한 플랫폼이 위치함(IDE 에서 프로젝트를 import하면 직접 실행도 가능)
    |
    --- android
    |
    --- ios 

[plugins] -- 추가한 플러그인들이 위치함
    |
    --- org.apache.cordova.splashscreen
    |
    --- org.apache.cordova.camera
    |
    --- org.apache.cordova.dialogs

[www] -- web 리소스가 위치함

## 개발시에는 web소스에 코드를 작성. 
## cordova build android/ios 로 빌드시 해당 웹소스가 각각 플랫폼별로 적용됨


============================= 참고 =============================

※ cordova 공식 사이트
 http://cordova.apache.org/

※ ngCordova(angular.js - cordova.js 연동 module)
 http://cordova.apache.org/ 

※ android adb 관련 검색해볼것
 http://webclass.tistory.com/entry/android-adb-%EC%82%AC%EC%9A%A9%EB%B2%95
 http://toridori.tistory.com/entry/adb-%EA%B0%84%EB%8B%A8%ED%95%9C-%EB%AA%85%EB%A0%B9%EC%96%B4

※ adb tcpip 5555 -- TCP로 접속하겠다고 설정
 restarting in TCP mode port: 5555 -- 이렇게 뜨면 성공

※ wifi 연결 후 핸드폰 아이피로 connect 
 adb connect [phoneIP]

※ logCat
 adb logcat -- logCat 실행

※ 이후 usb뽑아도 log 및 설치 가능

※ 해당 프로그램 로그만 보기 
adb shell
logcat | grep 'pakage'
ex> logcat | grep com.co.test

※ cordova logging 
adb logcat CordovaLog:D *:S

  
