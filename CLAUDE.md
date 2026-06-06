# CLAUDE.md — healthcare-kb 사용 지침

> 이 파일은 Claude Code가 본 저장소를 다룰 때 따르는 규칙임. 이 repo는 GC 헬스케어 신사업·전략 리서치 지식베이스로, YouTube·자료를 정리한 **소스 노트**와 **용어 마스터**를 누적·버전관리함.

## 핵심 원칙 (두괄식)

이 repo를 인용할 때는 ① 용어 정의는 `glossary.md`를 단일 기준으로 삼고, ② 사실·수치 근거는 반드시 `sources/`의 해당 소스 파일을 출처로 명기하며, ③ 1차 출처로 검증되지 않은 정량 수치는 ⚠️ 표기와 함께 "발언/추정 기준"임을 밝힘.

## 디렉터리 구조

```
healthcare-kb/
├── CLAUDE.md          # (이 파일) Claude Code 사용 지침
├── README.md          # 구조·작업규칙·소스 인덱스
├── glossary.md        # 용어 마스터 (단일 기준)
├── sources/           # 소스 노트 (주제 폴더 분류)
│   ├── bio-bd/        # 제약·바이오 BD
│   ├── ax-llm/        # AX·LLM 활용
│   ├── healthy-aging/ # 건강노화·만성질환
│   └── digital-health/# 데이터·디지털헬스
└── templates/         # 소스 노트 표준 포맷
```

## Claude Code 작업 규칙

1. **용어 인용**: 전문용어 정의가 필요하면 `glossary.md`를 먼저 참조. 정의가 없으면 새 소스 정리 시 추가하되, 임의로 추정 정의를 단정하지 말 것.
2. **근거 인용**: 사실·수치를 인용할 때는 해당 `sources/<파일>.md`를 출처로 명기. 출처가 없는 수치는 본문에 단정 명시 금지.
3. **미검증 수치 처리**: 소스 노트의 정량 수치 다수는 투자 채널·출연자의 발언·추정값으로 1차 출처 미검증임. 인용 시 ⚠️ 경고를 유지하고, 대외 문서에서는 공시·논문·학회 초록 등 원 출처 확인을 권고할 것.
4. **두괄식·근거 기반**: 결론을 먼저 제시하고, 출처 있는 정보는 항상 출처를 동반.
5. **새 소스 추가**: `templates/source_template.md` 포맷 준수 — ① 메타데이터 ② 핵심 요약(두괄식) ③ 주제별 정리 ④ 전체 자막(타임스탬프). 파일명은 `sources/<주제폴더>/YYYY-MM-DD_핵심주제.md` (주제폴더: bio-bd / ax-llm / healthy-aging / digital-health, 새 주제는 폴더 추가).
6. **신규 용어 등록**: 새 소스에서 전문용어가 나오면 `glossary.md`에 가나다/알파벳 순으로 추가(정의 + 최초 출처 파일 링크).
7. **커밋 메시지**: `add: <소스명>` / `update glossary: <용어>` / `fix: <내용>`.

## LLM Wiki 운영 규칙 (3계층 매핑)

이 repo는 LLM Wiki 구조로 운영함. 계층 매핑: **raw = `sources/`**(불변 원본, 소스 노트) / **wiki = `wiki/` + `glossary.md`**(정리된 지식 레이어) / **schema = 이 CLAUDE.md**(운영 규칙).

- **불변 원칙**: `sources/`의 원본 소스 노트는 수정하지 않음(오탈자 등 명백한 fix 제외). 가공·연결은 전부 `wiki/`에서 수행.
- **wiki/ 구조**: `concepts/`(주제·개념 페이지), `entities/`(기업·인물·제품·기관 페이지), `analyses/`(질의 중 재사용 가치가 있는 분석 결과), `index.md`(전체 인덱스). 1페이지 = 1개념, 상단 한 줄 요약 + 태그, `[[백링크]]`로 상호 연결, 하단에 출처(`sources/` 경로) 명기.
- **glossary.md와의 관계**: glossary는 용어의 한 줄 정의 사전, `wiki/concepts/`는 주제 단위 종합 페이지. 중복 시 glossary가 정의의 단일 기준이며 concepts 페이지는 glossary 항목을 백링크로 참조.
- **ingest**: `sources/`의 소스를 읽어 wiki 페이지 생성·갱신·연결. 기존 페이지와 겹치면 병합·강화, 모순 발견 시 본문에 ⚠️ 충돌 표시 후 사람에게 보고. ingest는 `wiki/index.md`와 README 인덱스도 갱신.
- **query**: 답변은 wiki(+glossary) 범위 내에서. **출처를 반드시 표기하고, wiki에 없으면 "없음"이라고 답함**(환각 금지). 재사용 가치가 있는 분석은 `analyses/`에 저장.
- **lint**: 깨진 백링크, 어디에도 연결되지 않은 외톨이 페이지, 규칙 위반 파일명, 누락 개념을 점검·수정. 작업 세션마다 1회 이상 실행 권장.
- **사람 승인**: wiki 페이지의 **삭제**와 `_private` 성격 자료 처리는 사람이 결정. 에이전트는 제안만 함.
- **동기화**: 작업 시작 전 `git pull`, 종료 시 commit + push. 웹챗 Claude는 주로 `sources/` 적재를, Claude Code는 주로 `wiki/` 가공을 담당(경로 분리로 충돌 최소화).

## 다른 프로젝트에서 이 repo 참조하기

기존 작업 프로젝트에서 본 KB를 **읽기 전용 참고자료**로 사용하는 방법:

1. 기존 프로젝트 루트에서 참조용 폴더로 clone:
   ```bash
   git clone https://github.com/JiantJay/healthcare-kb.git refs/healthcare-kb
   ```
2. 기존 프로젝트의 `.gitignore`에 추가(본 프로젝트 커밋과 분리):
   ```
   refs/
   ```
3. 작업 전 최신화:
   ```bash
   cd refs/healthcare-kb && git pull && cd -
   ```
4. 기존 프로젝트의 `CLAUDE.md`에 아래 블록을 붙여넣어 참조 규칙을 인식시킴(이 파일 하단 "부모 프로젝트용 스니펫" 참조).

## 부모 프로젝트용 CLAUDE.md 스니펫

```markdown
## 참고 지식베이스: healthcare-kb

`refs/healthcare-kb/`는 헬스케어 신사업·전략 리서치 KB(읽기 전용 참조).
- 전문용어 정의는 `refs/healthcare-kb/glossary.md`를 단일 기준으로 인용.
- 사실·수치 근거는 `refs/healthcare-kb/sources/<주제폴더>/<파일>.md`를 출처로 명기.
- 소스 노트의 정량 수치 다수는 1차 출처 미검증(발언·추정)이므로, 인용 시 그 사실을 함께 밝히고 대외 문서에서는 원 출처 확인을 권고.
- 작업 시작 전 `cd refs/healthcare-kb && git pull`로 최신화.
```
