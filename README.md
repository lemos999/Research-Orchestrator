# Research-Orchestrator

**Research-Orchestrator**는 대규모 언어 모델이 학술 연구, 문헌 검토, 코딩, 원고 작성 등의 복잡한 작업을 수행할 때 지켜야 할 운영 계약을 정의한 파일 기반 프롬프트 아키텍처입니다.

이 시스템은 모델의 기억이나 프롬프트 엔지니어링에 의존하는 대신, 파일 시스템 기반의 명시적 규칙을 읽고 따르도록 강제하여 환각을 줄이고 작업의 일관성과 감사 가능성을 확보합니다.

## 핵심 특징

* **내부 아카이브와 공개 아카이브 분리**: GPT의 구동을 위한 내부 지식 파일과 사용자에게 제공되는 누적형 공개 연구 아카이브를 분리하여 관리합니다.
* **증거 중심의 연구 워크플로우**: 단순 요약이 아닌, 개념 정의, 사전 연구 조사, 교차 검증, 경쟁 가설 비교, 논증 형성으로 이어지는 보수적인 연구 단계를 적용합니다.
* **누적형 원고 작성**: 한 번의 프롬프트로 전체 논문을 생성하지 않습니다. 신뢰할 수 있는 출처를 바탕으로 섹션을 누적하며, 명확한 인용 원장과 함께 최종 원고를 조립합니다.
* **명시적 코딩 계획 및 위임**: 코딩 작업 시 반드시 사전 계획을 승인받도록 제한하며, 필요시 명시적인 하위 에이전트 위임 오케스트레이션을 지원합니다.
* **과장 없는 투명한 보고**: 진행 상황은 시스템 디버그 로그가 아닌, 표준화된 연구 프로세스 언어로 작성되며, 모호한 추측과 검증된 사실을 명확히 구분합니다.

## 디렉토리 구조

* `AGENTS.md`: 모델이 최우선으로 읽고 따라야 하는 최상위 운영 계약 및 실행 지침. (지식 영역 최상단 루트에 단독 배치)
* `skills/`, `references/` 및 기타 계약 파일: 연구 워크플로우, 원고 작성, 평가 루브릭 등의 세부 모듈 파일. (하나의 ZIP 파일로 압축하여 관리)

## 사용 방법

본 시스템은 Custom GPT 또는 파일 인식이 가능한 LLM 런타임 환경에서 작동하도록 설계되었습니다.

1. **파일 준비**: 레포지토리 내의 `AGENTS.md` 파일을 제외한 나머지 모든 파일 및 폴더(`skills/`, `references/` 등)를 모아 하나의 ZIP 아카이브(예: `Research-Orchestrator.zip`)로 압축합니다.
2. **파일 업로드**: GPT 설정의 지식 영역 최상단 루트에 `AGENTS.md` 파일과 압축한 ZIP 파일을 함께 업로드합니다.
3. **시스템 프롬프트 설정**: 모델의 기본 설정에 다음과 같은 짧은 지침을 추가하여 오케스트레이션을 활성화합니다.
   * *"작업을 시작하거나 사용자의 요청에 답하기 전에, 반드시 루트에 첨부된 `AGENTS.md` 파일을 먼저 읽고 그 안의 운영 계약을 따르시오."*

---

# Research-Orchestrator (English)

**Research-Orchestrator** is a file-based prompt architecture that defines an operating contract for Large Language Models performing complex tasks such as academic research, literature reviews, coding, and manuscript drafting.

Instead of relying on hidden context windows or prompt theater, this system forces the model to read and follow explicit file-system-based rules. This approach minimizes hallucinations and ensures consistency and auditability throughout the task execution.

## Core Features

* **Separation of Internal & Public Archives**: Separates internal operating files required for the LLM's runtime from the public, cumulative research archive delivered to the user.
* **Evidence-First Research Workflow**: Enforces a conservative, step-by-step research process including concept definition, prior-art mapping, evidence appraisal, competing explanation comparison, and argument formation.
* **Cumulative Manuscript Assembly**: Prevents one-shot generation of entire papers. The system accumulates sections over time based on verified evidence and integrates them using a canonical citation ledger.
* **Explicit Coding Plans & Delegation**: Requires an approved plan record before any writable coding execution and supports explicit parent-subagent delegation when requested.
* **Transparent, Unexaggerated Reporting**: Output is formatted using standard research-process language rather than system debug logs. It clearly distinguishes verified facts from inference or unresolved questions.

## Directory Structure

* `AGENTS.md`: The root operating contract and primary instruction set. (Placed directly at the root of the knowledge base).
* `skills/`, `references/`, and other contract files: Detailed modular files for workflows, manuscript assembly, and evaluation. (Packaged together into a single ZIP archive).

## Usage

This system is designed to run in a Custom GPT or any file-capable LLM runtime.

1. **Prepare Files**: Keep `AGENTS.md` separate. Package all other folders and files (e.g., `skills/`, `references/`) into a single ZIP archive (e.g., `Research-Orchestrator.zip`).
2. **Upload to Knowledge Base**: Upload both the `AGENTS.md` file and the ZIP archive to the root directory of your GPT's knowledge section.
3. **System Instructions**: Add a brief bootstrap instruction to the model's setup:
   * *"Before starting any task or answering the user, you must read the `AGENTS.md` file attached at the root and follow its operating contract."*
