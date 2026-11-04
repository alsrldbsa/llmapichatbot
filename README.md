# llmapichatbot

LLM API 기반 챗봇 설계 구현 팀 과제입니다. 공통 동작을 가진 기본 챗봇 `ChatBot`을 만들고, 목적별 챗봇 4개를 **상속**으로 파생합니다. 대화 이력·지식·예제는 **배열만으로** 관리하고, 실제 API 대신 **가짜(스텁) LLM 클라이언트**를 직접 만들어 연결합니다.

> 2026-2 Introduction to Programming 2 (명지대학교), 강의 슬라이드 38~41

## 구조

```
src/      Java 소스. 클래스 하나당 파일 하나 (작성 순서: src/README.md)
docs/     설계와 결정 사항
  설계.md       클래스별 필드·메서드·구현 방법
  결정사항.md   슬라이드에 없는 부분과 팀 결정 기록
  작업순서.md   단계별 작업과 이슈 번호
tests/    확인 시나리오와 기대 결과
```

## 클래스 관계

```
ChatMessage ──> ConversationBuffer ─┐
                                    ├──> ChatBot (부모, reply() 흐름 고정)
LLMClient (스텁) ───────────────────┘        │ extends
                       ┌───────────┬─────────┴──┬────────────┐
                    FaqBot      TutorBot    PlannerBot    KoreanBot
                 buildPrompt  buildPrompt  postProcess   buildPrompt
```

## 원칙

- 대화 이력·FAQ·예제는 **배열 + size 변수**로만 관리한다. `ArrayList` 등 컬렉션은 쓰지 않는다.
- 배열이 꽉 차면 **2배 크기 배열을 만들어 직접 복사**한다.
- `reply()`의 5단계 흐름은 부모에만 둔다. 자식은 `buildPrompt` 또는 `postProcess`만 오버라이드한다.
- 자식은 `super.buildPrompt()` 결과에 덧붙인다. 같은 조립 코드를 다시 쓰지 않는다.
- 스텁 응답은 **같은 입력이면 같은 출력**, 여러 줄로 만든다.
- 강의 슬라이드 원본(PDF)은 저장소에 올리지 않는다.
- 슬라이드에 없는 규칙은 `docs/결정사항.md`에서 정한 뒤 구현한다.

## 진행 방식

1. `docs/결정사항.md`의 결정 칸을 채운다 (이슈 #1).
2. `docs/작업순서.md`의 단계 순서대로 이슈를 맡아 구현한다.
3. 이슈 하나 = 브랜치 하나 = PR 하나. PR 본문에 `Closes #번호`.

## 실행 방법

준비 중입니다.
