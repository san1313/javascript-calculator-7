## 미션 제출 방법
- 미션 구현을 완료한 후 GitHub을 통해 제출해야 한다.
	- GitHub을 활용한 제출 방법은 프리코스 과제 제출 문서를 참고해 제출한다.
- GitHub에 미션을 제출한 후 우아한테크코스 지원 플랫폼 에 PR 링크를 포함하여 최종 제출한다.
	- 자세한 안내는 제출 가이드 를 참고한다.
	- 과제를 수행하면서 느낀 점, 배운 점, 많은 시간을 투자한 부분 등 자유롭게 작성한다.

## 과제 제출 전 체크 리스트
- 기능을 올바르게 구현했더라도 요구 사항에 명시된 출력 형식을 따르지 않으면 0점을 받게 된다.
- 기능 구현을 완료한 후 아래 가이드에 따라 모든 테스트가 성공적으로 실행되는지 확인한다.
- 테스트가 실패하면 점수가 0점이 되므로 제출하기 전에 반드시 확인한다.

## 테스트 실행 가이드
- 터미널에서 node --version 을 실행하여 Node.js 버전이 20.17.0 이상인지 확인한다.
- 아래 명령을 입력하여 패키지를 설치한 후 실행하는 데 문제가 없어야 한다.
```npm install
npm run test
npm run start
```

## 문자열 덧셈 계산기
### 정리
1. 입력한 문자열에서 숫자를 추출하여 더하는 계산기를 구현한다.
2. 구분자는 기본 [,:] 이고, //;\n 의 경우 ;를 커스텀 구분자로 사용한다.
3. 사용자가 잘못된 값을 입력할 경우 "[ERROR]" 로 시작하는 메시지와 함께 Error 발생 후 어플리케이션을 종료한다.
4. 프로그램 실행의 시작점은 App.js 의 run() 이다.
5. 사용자의 값을 입력 및 출력하려면 Console.readLineAsync() 와 Console.print() 를 활용한다.

### 기능 목록
1. 사용자에게 문자열을 입력 받는다.
2. 입력받은 문자열을 분석한다.
	1. 입력 값이 잘못되었을 경우 "[ERROR]"로 시작하는 메시지를 출력하고 Error처리한다.
	2. 커스텀 구분자를 배열에 저장하고 //와 \n을 제거한 문자열을 반환한다.
	3. 배열에 있는 모든 구분자를 통해 숫자를 분리해 배열에 저장한다.
	4. 잘못된 입력 값을 판단한다.
3. 배열의 숫자를 모두 더해 반환한다.
4. 반환된 숫자를 출력한다.

### 생각해봐야 할 것
1. 커스텀 구분자가 특수 문자가 아닌 일반 글자일 경우
2. 커스텀 구분자가 숫자인 경우
3. Error 처리는 어떤 경우에 해야하는가
	- 구분자와 양수로 구성된 문자열이다.
	- 음수 또는 0인 경우 Error처리한다.
	- 커스텀 구분자가 1글자가 아닌 여러 글자일 경우 (요구사항이 문자열이 아닌 문자임)
	- 커스텀 구분자를 처리한 후에도 숫자가 아닌 문자가 남아있는 경우
4. 구분자 사이에 숫자가 없는 경우가 발생했을 경우
	- 에러로 처리한다.
5. //;\n//-\n 같은 경우는 //;\n과 //-\n 두 개로 볼 것인가 ;\n//- 한 개로 볼 것인가
	- 두 개로 보는 것으로 설정.

### 테스트 케이스
- 1,2:3
- //;\n1;2;3
- 1//;\n//-\n;2-3
- -1,2,3
- //\n1,2,3
### 과제 진행 요구 사항
- 미션은 문자열 덧셈 계산기 저장소를 포크하고 클론하는 것으로 시작한다.
- 기능을 구현하기 전 README.md 에 구현할 기능 목록을 정리해 추가한다.
- Git의 커밋 단위는 앞 단계에서 README.md 에 정리한 기능 목록 단위로 추가한다.
	- AngularJS Git Commit Message Conventions (번역본) 을 참고해 커밋 메시지를 작성한다.
- 자세한 과제 진행 방법은 프리코스 진행 가이드 문서를 참고한다.
### 기능 요구 사항
입력한 문자열에서 숫자를 추출하여 더하는 계산기를 구현한다.
- 쉼표(,) 또는 콜론(:)을 구분자로 가지는 문자열을 전달하는 경우 구분자를 기준으로 분리한 각 숫자의 합을 반환한다.
	- 예: "" => 0, "1,2" => 3, "1,2,3" => 6, "1,2:3" => 6
- 앞의 기본 구분자(쉼표, 콜론) 외에 커스텀 구분자를 지정할 수 있다. 커스텀 구분자는 문자열 앞부분의 "//"와 "\n" 사이에 위치하는 문자를 커스텀 구분자로 사용한다.
	- 예를 들어 "//;\n1;2;3"과 같이 값을 입력할 경우 커스텀 구분자는 세미콜론(;)이며, 결과 값은 6이 반환되어야 한다.
- 사용자가 잘못된 값을 입력할 경우 "[ERROR]"로 시작하는 메시지와 함께 Error 를 발생시킨 후 애플리케이션은 종료되어야 한다.
#### 입출력 요구 사항
#### 입력
- 구분자와 양수로 구성된 문자열
#### 출력
- 덧셈 결과
```
결과 : 6
```
#### 실행 결과 예시
```
덧셈할 문자열을 입력해 주세요.
1,2:3
결과 : 6
```
### 프로그래밍 요구 사항
- Node.js 20.17.0 버전에서 실행 가능해야 한다.
- 프로그램 실행의 시작점은 App.js 의 run() 이다.
- package.json 파일은 변경할 수 없으며, 제공된 라이브러리와 스타일 라이브러리 이외의 외부 라이브러리는 사용하지 않는다.
- 프로그램 종료 시 process.exit() 를 호출하지 않는다.
- 프로그래밍 요구 사항에서 달리 명시하지 않는 한 파일, 패키지 등의 이름을 바꾸거나 이동하지 않는다.
- 자바스크립트 코드 컨벤션을 지키면서 프로그래밍한다.
	- 기본적으로 JavaScript Style Guide 를 원칙으로 한다.
#### 라이브러리
- @woowacourse/mission-utils 에서 제공하는 Console API를 사용하여 구현해야 한다.
	- 사용자의 값을 입력 및 출력하려면 Console.readLineAsync() 와 Console.print() 를 활용한다.
