# src

Java 소스 폴더. 클래스 하나당 파일 하나. 아래 순서대로 만든다 (자세한 설계는 `docs/설계.md`).

| 순서 | 파일 | 역할 | 이슈 |
|---|---|---|---|
| 1 | `ChatMessage.java` | 메시지 1개 (role, content) | #2 |
| 2 | `ConversationBuffer.java` | 메시지 배열, 2배 확장, 최근 K개 합치기 | #3 |
| 2 | `LLMClient.java` | 규칙 기반 가짜 응답 | #4 |
| 3 | `ChatBot.java` | 부모. reply() 5단계 고정 | #5 |
| 4 | `FaqEntry.java`, `FaqBot.java` | FAQ 우선 프롬프트 | #6 |
| 4 | `TutorBot.java` | 예제 + 단계별 설명 지시 | #7 |
| 4 | `PlannerBot.java` | 응답을 체크리스트로 | #8 |
| 4 | `KoreanBot.java` | 한국어 지시 항상 포함 | #9 |
| 5 | `Main.java` | 슬라이드 41 데모 실행 | #10 |

패키지는 쓰지 않는다 (기본 패키지). 컴파일·실행 방법은 #10에서 루트 README에 적는다.
