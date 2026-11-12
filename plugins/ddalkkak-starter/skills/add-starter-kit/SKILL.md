---
name: add-starter-kit
description: 이 Spring Boot 프로젝트에 딸깍 스타터킷(com.github.mouse-ddalkkak:ddalkkak)을 넣어 딸깍 검사기와 연결한다. "딸깍 스타터킷 넣어 줘", "딸깍에 연결", "add ddalkkak starter kit" 같은 요청에 쓴다.
---

# 딸깍 스타터킷 넣기

[딸깍](https://github.com/mouse-ddalkkak/ddalkkak)이 앱을 검사하려면 앱에 스타터킷 라이브러리가 들어 있어야 한다. 키와 설정 파일은 필요 없다. 앱이 켜지면 같은 컴퓨터의 딸깍(`http://localhost:7777`)을 스스로 찾아 연결을 요청한다.

넣을 버전은 **`v1.1.0`** 이다. 딸깍 v1.1.x용이고, 다른 딸깍 버전은 [호환 표](https://github.com/mouse-ddalkkak/ddalkkak-starter#호환-버전)를 본다.

## 1. 먼저 확인한다

범위 밖이면 파일을 고치지 말고 이유를 알린 뒤 멈춘다.

- 빌드 도구와 설정 파일: `build.gradle` · `build.gradle.kts` · `pom.xml`. 멀티 모듈이면 `@SpringBootApplication`이 있는(실제로 띄우는) 모듈에 넣는다
- Spring Boot 3.2 이상(4.x 포함) · Java 17 이상
- Spring MVC(서블릿) 앱: `spring-boot-starter-web`(Boot 4는 `spring-boot-starter-webmvc`)이나 war 배포. WebFlux만 있는 앱은 지원하지 않는다
- 이미 `com.github.mouse-ddalkkak:ddalkkak`이 있으면 새로 더하지 않고 버전만 `v1.1.0`으로 맞춘다

## 2. 의존성을 넣는다

기존 `repositories` · `dependencies` 블록이 있으면 그 안에 한 줄씩 더한다. 저장소를 `settings.gradle(.kts)`의 `dependencyResolutionManagement`에서만 받는 프로젝트(`repositoriesMode`가 `FAIL_ON_PROJECT_REPOS`)는 저장소 줄을 거기에 넣는다.

Gradle (`build.gradle`)

```groovy
repositories { maven { url 'https://jitpack.io' } }
dependencies { implementation 'com.github.mouse-ddalkkak:ddalkkak:v1.1.0' }
```

Gradle Kotlin DSL (`build.gradle.kts`)

```kotlin
repositories { maven("https://jitpack.io") }
dependencies { implementation("com.github.mouse-ddalkkak:ddalkkak:v1.1.0") }
```

Maven (`pom.xml`)

```xml
<repositories><repository><id>jitpack.io</id><url>https://jitpack.io</url></repository></repositories>
<dependency><groupId>com.github.mouse-ddalkkak</groupId><artifactId>ddalkkak</artifactId><version>v1.1.0</version></dependency>
```

## 3. 커밋 정보 플러그인을 넣는다

딸깍은 실행 중인 앱의 커밋과 연결한 코드의 커밋이 같은지 비교한다. 그 값을 jar에 넣는 플러그인이다. 프로젝트가 git 저장소가 아니면(`git rev-parse --git-dir` 실패) 넣지 않는다. 커밋이 없어 빌드만 실패한다.

- Gradle: `plugins { id 'com.gorylenko.gradle-git-properties' version '4.0.1' }` (Kotlin DSL은 `id("com.gorylenko.gradle-git-properties") version "4.0.1"`)
- Maven: `io.github.git-commit-id:git-commit-id-maven-plugin`. parent가 `spring-boot-starter-parent`면 `<plugin>`에 groupId · artifactId만 쓴다. 아니면 version과 `revision` goal 실행, `<generateGitPropertiesFile>true</generateGitPropertiesFile>`도 넣는다

## 4. 빌드를 확인한다

프로젝트의 wrapper로 빌드한다(`./gradlew build -x test` · `./mvnw -q package -DskipTests`, Windows는 `gradlew.bat` · `mvnw.cmd`). 의존성을 못 받으면 저장소 줄이 실제로 쓰이는 곳에 들어갔는지 본다. 실패하면 고친 뒤 다시 빌드하고, 고칠 수 없으면 오류를 그대로 알린다.

## 5. 딸깍 주소

설정하지 않는다. 기본은 같은 컴퓨터의 `http://localhost:7777`이다. 사용자가 딸깍을 다른 포트로 설치했다고 하거나 앱이 Docker 안에서 돈다고 하면, 앱을 띄우는 환경에 `DDALKKAK_URL=http://<딸깍 주소>:<포트>`를 넣으라고 알린다.

## 6. 알린다

- 바뀐 파일과 바뀐 줄
- 앱을 다시 켜는 명령(예 `./gradlew bootRun`, 이미 서비스로 돈다면 그 재시작 방법)
- 다시 켜면 딸깍 화면 "서비스 연결" 단계에 연결 요청이 뜨고, **허용**을 누르면 연결된다
