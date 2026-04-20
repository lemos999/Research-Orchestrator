# Research-Orchestrator

**Research-Orchestrator**는 대규모 언어 모델이 학술 연구, 문헌 검토, 원고 작성 등의 복잡한 작업을 수행할 때 지켜야 할 운영 계약을 정의한 파일 기반 프롬프트 아키텍처입니다.

이 시스템은 모델의 기억이나 프롬프트 엔지니어링에 의존하는 대신, 파일 시스템 기반의 명시적 규칙을 읽고 따르도록 강제하여 환각을 줄이고 작업의 일관성과 감사 가능성을 확보합니다.

## 핵심 특징

* **내부 아카이브와 공개 아카이브 분리**: GPT의 구동을 위한 내부 지식 파일과 사용자에게 제공되는 누적형 공개 연구 아카이브를 분리하여 관리합니다.
* **증거 중심의 연구 워크플로우**: 단순 요약이 아닌, 개념 정의, 사전 연구 조사, 교차 검증, 경쟁 가설 비교, 논증 형성으로 이어지는 보수적인 연구 단계를 적용합니다.
* **누적형 원고 작성**: 한 번의 프롬프트로 전체 논문을 생성하지 않습니다. 신뢰할 수 있는 출처를 바탕으로 섹션을 누적하며, 명확한 인용 원장과 함께 최종 원고를 조립합니다.
* **과장 없는 투명한 보고**: 진행 상황은 시스템 디버그 로그가 아닌, 표준화된 연구 프로세스 언어로 작성되며, 모호한 추측과 검증된 사실을 명확히 구분합니다.

## 디렉토리 구조

* `AGENTS.md`: 모델이 최우선으로 읽고 따라야 하는 최상위 운영 계약 및 실행 지침.
* `skills/`, `references/` 및 기타 계약 파일: 연구 워크플로우, 원고 작성, 평가 루브릭 등의 세부 모듈 파일.

## 사용 방법

런타임 환경에 따라 아래의 방법을 적용합니다.

* **GPTs 환경**
  1. 준비된 ZIP 압축 파일을 지식 영역(Knowledge)에 업로드합니다.
  2. 압축 파일 내에 있는 파일이 아닌, 압축 파일 외부에 별도로 존재하는 `AGENTS.md` 파일의 전체 내용을 복사하여 GPT의 시스템 프롬프트(Instructions) 영역에 그대로 붙여넣습니다.

* **Codex 등 로컬 워크스페이스 환경**
  1. 본 레포지토리를 클론합니다.
  2. 터미널 등을 통해 해당 디렉토리로 이동하여 작업을 시작하면, 시스템이 작업 공간의 파일 구조를 인식하여 운영 계약이 즉시 적용됩니다.

---

# Research-Orchestrator (English)

**Research-Orchestrator** is a file-based prompt architecture that defines an operating contract for Large Language Models performing complex tasks such as academic research, literature reviews, and manuscript drafting.

Instead of relying on hidden context windows or prompt theater, this system forces the model to read and follow explicit file-system-based rules. This approach minimizes hallucinations and ensures consistency and auditability throughout the task execution.

## Core Features

* **Separation of Internal & Public Archives**: Separates internal operating files required for the LLM's runtime from the public, cumulative research archive delivered to the user.
* **Evidence-First Research Workflow**: Enforces a conservative, step-by-step research process including concept definition, prior-art mapping, evidence appraisal, competing explanation comparison, and argument formation.
* **Cumulative Manuscript Assembly**: Prevents one-shot generation of entire papers. The system accumulates sections over time based on verified evidence and integrates them using a canonical citation ledger.
* **Transparent, Unexaggerated Reporting**: Output is formatted using standard research-process language rather than system debug logs. It clearly distinguishes verified facts from inference or unresolved questions.

## Directory Structure

* `AGENTS.md`: The root operating contract and primary instruction set.
* `skills/`, `references/`, and other contract files: Detailed modular files for workflows, manuscript assembly, and evaluation.

## Usage

Apply the following setup depending on your runtime environment.

* **For Custom GPTs**
  1. Upload the provided ZIP archive to the **Knowledge** section.
  2. Copy the entire contents of the standalone `AGENTS.md` file (located outside the ZIP archive) and paste it directly into the GPT's **Instructions** field.

* **For Codex or Workspace-based Environments**
  1. Clone this repository.
  2. Navigate (`cd`) into the directory and begin your task. The file-based operating contract will be applied automatically within the workspace.
