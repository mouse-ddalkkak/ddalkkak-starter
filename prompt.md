AI 코딩 도구(Claude Code · Codex · Cursor …)에 아래 글을 그대로 붙여 넣으면 검사할 앱에 딸깍 스타터킷을 넣어 줍니다. 딸깍 화면 "스타터킷 추가" 단계의 `프롬프트 복사`와 같은 글입니다.

```text
이 프로젝트에 딸깍 스타터킷(com.github.mouse-ddalkkak:ddalkkak, 저장소 https://jitpack.io)을 설치해 주세요.
1) 먼저 프로젝트의 빌드 도구(Gradle/Maven)와 설정 파일(build.gradle / build.gradle.kts / pom.xml),
Java 버전, Spring Boot 버전을 확인해 주세요.
2) 저장소 줄 maven { url 'https://jitpack.io' } 과 의존성 com.github.mouse-ddalkkak:ddalkkak:v1.2.0 을 추가해 주세요.
build.gradle.kts면 Kotlin 문법(maven("https://jitpack.io") · implementation("…")), pom.xml이면 <repository> · <dependency>로 넣어 주세요.
지원: Spring Boot 3.2 이상 · Java 17 이상 · Spring MVC 앱만 (아니면 설치하지 말고 알려 주세요)
코드가 실행 중인 버전과 같은지 비교하려면 커밋 정보 플러그인도 넣어 주세요: Gradle id 'com.gorylenko.gradle-git-properties' version '4.0.1' · Maven io.github.git-commit-id:git-commit-id-maven-plugin (parent가 spring-boot-starter-parent가 아니면 revision goal 실행과 generateGitPropertiesFile=true도). git 저장소가 아니면 이 플러그인은 빼 주세요.
다른 설정 파일이나 키는 필요 없어요.
3) 빌드가 통과하는지 확인하고 서비스를 재시작해 주세요.
바뀐 파일과 재시작 명령을 알려주세요.
```
