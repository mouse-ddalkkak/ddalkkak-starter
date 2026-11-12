# ddalkkak-starter

[딸깍](https://github.com/mouse-ddalkkak/ddalkkak)으로 검사할 Spring Boot 앱에 스타터킷을 넣어 주는 AI 코딩 도구용 프롬프트 · 스킬 · 플러그인입니다. 도구가 프로젝트를 보고 의존성을 넣고 빌드를 확인한 뒤 재시작 방법을 알려 줍니다. 앱을 다시 켜면 딸깍 화면에 연결 요청이 뜹니다.

검사할 앱 조건: Spring Boot 3.2 이상(4.x 포함) · Java 17 이상 · Spring MVC(서블릿). 딸깍과 같은 컴퓨터에서 띄웁니다.

## Claude Code

```bash
claude plugin marketplace add mouse-ddalkkak/ddalkkak-starter
claude plugin install ddalkkak-starter@ddalkkak-starter
```

검사할 앱 폴더에서 Claude Code를 열고 `/ddalkkak-starter:add-starter-kit`을 실행합니다. Claude Code 안에서는 `/plugin marketplace add mouse-ddalkkak/ddalkkak-starter` · `/plugin install ddalkkak-starter@ddalkkak-starter`로 설치해도 됩니다.

## Codex

```bash
codex plugin marketplace add mouse-ddalkkak/ddalkkak-starter
codex plugin add ddalkkak-starter@ddalkkak-starter
```

검사할 앱 폴더에서 Codex를 열고 `$add-starter-kit`을 실행하거나 "딸깍 스타터킷 넣어 줘"라고 말합니다.

## 프롬프트

다른 AI 코딩 도구는 [prompt.md](prompt.md)의 글을 붙여 넣습니다. 딸깍 화면의 `프롬프트 복사`와 같은 글입니다.

## 직접 넣기

AI 도구 없이 넣을 때는 아래 줄을 넣고 앱을 다시 켭니다.

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

딸깍을 7777이 아닌 포트로 설치했거나 앱이 Docker 안에서 돈다면 앱을 띄울 때 `DDALKKAK_URL=http://<딸깍 주소>:<포트>`를 넣습니다.

## 호환 버전

| ddalkkak-starter | 딸깍 | 넣는 스타터킷 |
| --- | --- | --- |
| v1.0.0 | v1.1.x | `v1.1.0` |

딸깍 v1.0.0은 지원하지 않습니다. 딸깍 설치 명령을 다시 실행해 올립니다. 이 저장소는 딸깍 본체와 따로 버전을 매깁니다. 플러그인을 새 버전으로 받으려면 `claude plugin marketplace update ddalkkak-starter` · `codex plugin marketplace upgrade ddalkkak-starter`를 실행합니다.

## 라이선스

[Apache-2.0](LICENSE)
