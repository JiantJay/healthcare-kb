# healthcare-kb

GC 헬스케어 신사업·전략 리서치 지식베이스. YouTube·자료를 텍스트로 정리한 소스 노트와 용어 마스터를 누적·버전관리한다.

## 디렉터리 구조

```
healthcare-kb/
├── CLAUDE.md            # Claude Code 사용 지침 (인용 규칙)
├── glossary.md          # 용어 마스터 (단일 기준, 가나다/알파벳 정렬)
├── sources/             # 영상·자료별 정리 md (1소스 = 1파일, 주제 폴더 분류)
│   ├── bio-bd/          # 제약·바이오 BD
│   ├── ax-llm/          # AX·LLM 활용
│   ├── healthy-aging/   # 건강노화·만성질환 (anti-aging)
│   ├── digital-health/  # 데이터·디지털헬스
│   └── <각 카테고리>/papers/   # 학술 논문 요약 노트 + assets/(원본 PDF, git 제외)
├── templates/           # md 변환 표준 포맷
└── README.md            # 인덱스 + 작업 규칙
```

## 작업 규칙

1. **파일명 규칙**: `sources/<주제폴더>/YYYY-MM-DD_핵심주제.md` (게시일 기준, 공백 대신 `_`). 주제폴더: `bio-bd`(제약·바이오 BD), `ax-llm`(AX·LLM 활용), `healthy-aging`(건강노화·만성질환), `digital-health`(데이터·디지털헬스). 새 주제는 폴더 추가
2. **학술 논문**: `sources/<주제폴더>/papers/`에 요약 노트(.md)로 적재하고, 서지·DOI·라이선스·데이터 접근 정보를 상단에 명기. 원본 PDF는 대용량·저작권을 고려해 `papers/assets/`에 두되 기본 버전관리 제외(.gitignore), Open Access면 DOI 링크로 대체. **CC BY-NC-ND 등 라이선스는 상업화·서비스화 시 제약이 되므로 노트에 ⚠️ 경고 명기.**
3. **소스 노트 구조**: `templates/source_template.md` 준수 — ① 메타데이터 ② 핵심 요약(두괄식) ③ 주제별 정리 ④ 전체 자막(타임스탬프)
4. **정량 수치**: 1차 출처(공시·논문·기관 통계)로 검증된 수치만 본문에 명기. 출연자 구두 발언 등 미검증 수치는 ⚠️ 경고와 함께 출처를 발언 기준으로 표기
5. **용어 등록**: 소스 노트에서 새 전문용어가 나오면 `glossary.md`에 추가(정의 + 최초 출처 파일 링크)
6. **커밋 메시지**: `add: <소스명>` / `update glossary: <용어>` / `fix: <내용>` 형태

## 소스 인덱스

| 날짜 | 분류 | 주제 | 파일 |
|---|---|---|---|
| 2026-04-16 | bio-bd | K-바이오 밸류체인 3분류·중국 천인계획·생산적 금융 정책 제언 (신한 엄민용) | [link](sources/bio-bd/2026-04-16_K바이오_밸류체인_생산적금융_신한엄민용.md) |
| 2026-05-12 | bio-bd | 신약개발 프로세스·바이오 투자 옥석 판별 (이승규 한국바이오협회 부회장) | [link](sources/bio-bd/2026-05-12_신약개발_바이오투자_이승규부회장.md) |
| 2026-05-22 | bio-bd | ADA 2026 비만치료제 한계·미충족 수요와 K-바이오 5개사 (이해진의 바이오 투자학교) | [link](sources/bio-bd/2026-05-22_ADA2026_비만치료제_K바이오.md) |
| 2026-05-18 | bio-bd | K-바이오 시대·규제 혁파, 렉라자/MARIPOSA·SC제형·투자·AI (조병철 교수·권해순 연구원 2부) | [link](sources/bio-bd/2026-05-18_K바이오_렉라자_규제혁파_AI.md) |
| 2026-04-06 | ax-llm | LLM Wiki 입문 가이드 — 정원사 모델·raw/wiki/schema·옵시디언 실습 (편집자P) | [link](sources/ax-llm/2026-04-06_LLM위키_입문가이드_옵시디언실습.md) |
| 2026-05-19 | ax-llm | LLM Wiki 지식 저장소 구축기 — RAG와의 차이·Git+Obsidian·거버넌스 (전현준의 현업 에이전트) | [link](sources/ax-llm/2026-05-19_LLM위키_지식저장소_RAG차이.md) |
| 2026-05-20 | ax-llm | AI 네이티브 조직 운영 — 폐쇄 루프·소프트웨어 팩토리·새 조직구조 (YC 다이애나 후) | [link](sources/ax-llm/2026-05-20_AI네이티브_조직운영_YC다이애나후.md) |
| 2026-05-22 | ax-llm | 회사 단위 LLM Wiki(컴퍼니 브레인) 노코드 구축 실습 — Obsidian+Claude Code (Theuxlabs) | [link](sources/ax-llm/2026-05-22_회사_LLM위키_컴퍼니브레인_실습.md) |
| 2026-06-02 | bio-bd | 2026 하반기 제약·바이오 전망 — 기술이전·소사이클(RNA)·MASH·톱픽 (키움 허혜민) | [link](sources/bio-bd/2026-06-02_제약바이오_하반기전망_키움허혜민.md) |
| 2026-06-02 | bio-bd | 코스닥·제약바이오 수급 — 알테오젠 이전상장·국민성장펀드·장기지속형 (삼프로TV 메리츠 이화진) | [link](sources/bio-bd/2026-06-02_코스닥_제약바이오_수급_삼프로_이화진.md) |
| 2026-06-03 | bio-bd | AI×바이오 투자 지형 — 엔비디아·구글·빅파마 협업/인수, 옥석 기준, RNA·디지털트윈 (강하나) | [link](sources/bio-bd/2026-06-03_AI바이오_투자지형_엔비디아_구글_강하나.md) |
| 2026-06-10 | bio-bd | AI 신약·단백질 — 센트럴도그마·다크 프로테옴·표적단백질분해(TPD)·알파폴드 (조가연 VC) | [link](sources/bio-bd/2026-06-10_AI신약_단백질_다크프로테옴_조가연VC.md) |
| 2026-06-01 | healthy-aging | 착한 염증 나쁜 염증 1부 — 염증·면역 작동원리와 대사질환 기전 (서울대 이승훈) | [link](sources/healthy-aging/2026-06-01_착한염증나쁜염증_1부_염증면역원리_이승훈.md) |
| 2026-06-02 | healthy-aging | 착한 염증 나쁜 염증 2부 — 무증상 만성염증 진단(hsCRP)·치료·수면 (서울대 이승훈) | [link](sources/healthy-aging/2026-06-02_착한염증나쁜염증_2부_만성염증진단_이승훈.md) |
| 2026-06-04 | healthy-aging/papers | [논문] 포유류 노화·사망의 보편 전사체 신호·사망 시계 (Nature, Tyshkovskiy et al.) ⚠️CC BY-NC-ND | [link](sources/healthy-aging/papers/2026-06-04_Nature_노화사망_전사체시계_Tyshkovskiy.md) |
| 2026-06-09 | healthy-aging | 노화 역전 첫 인체 임상 — Life Bio ER-100(OSK 후성유전 복원, AAV) 시신경병증 1상 (보도자료+NCT07290244) | [link](sources/healthy-aging/2026-06-09_노화역전임상_LifeBio_ER100_OSK_시신경병증.md) |
