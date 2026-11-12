# 국민대학교 로켓 동아리 'ERUCA' 신입생 프로젝트

> SKY의 K는 국민대

센서로 비행 정보를 모으고, 지상국으로 보내고, SD카드에 남기는 로켓 프로젝트입니다.

**저장소:** [ERUCA-Control/freshman](https://github.com/ERUCA-Control/freshman)

처음 참여했다면 아래의 **처음 설정 → 내려받기 → 작업하기** 순서대로 따라오면 됩니다. 문제가 생겼을 때만 접힌 도움말을 열어보세요.

---

## 1. Git 처음 쓰기

우리 팀의 작업 순서는 다음과 같습니다.

**최신 파일 받기 → 내 작업 공간 만들기 → 수정해서 올리기 → 팀원 확인 후 합치기**

여기서 `main`은 팀이 함께 쓰는 기준 버전이고, **브랜치**는 내 작업을 따로 진행하는 공간입니다.

### 처음 한 번: 설치와 설정

1. [Git을 설치](https://git-scm.com/install/)합니다.
2. 저장소 관리자는 참여자에게 **Write 권한**을 부여합니다. 저장소가 Public이어도 push에는 쓰기 권한이 필요합니다.
3. Windows는 PowerShell 또는 Git Bash, macOS는 터미널을 열고 아래 명령을 입력합니다.

이름과 이메일은 본인 것으로 바꿉니다.

```bash
git --version
git config --global user.name "본인 이름"
git config --global user.email "본인 GitHub 이메일"
```

이름·이메일 설정은 커밋 작성자 정보입니다. GitHub 로그인은 별도로 필요하며, 인증 화면이 뜨면 **각자 본인 계정으로 인증**합니다. [권한 안내](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization) · [인증 안내](https://docs.github.com/en/get-started/git-basics/about-remote-repositories)

### 처음 한 번: 내 노트북에 내려받기

프로젝트를 보관할 상위 폴더에서 실행합니다.

```bash
git clone https://github.com/ERUCA-Control/freshman.git
cd freshman
git status
```

`freshman` 폴더가 생기면 준비 끝입니다. **이후 명령은 모두 이 폴더 안에서 실행합니다.** 이미 clone했다면 다시 받을 필요 없이 아래 작업 순서부터 시작하세요.

### 매번 작업할 때: 이 순서대로

**① 최신 버전 받고 내 브랜치 만들기**

아직 파일을 수정하지 않은 상태에서 실행합니다. `git status`에 남아 있는 수정이 있다면 멈추고 아래의 **「수정한 파일 때문에 pull이나 브랜치 전환이 막혀요」** 도움말부터 확인하세요.

```bash
git status
git switch main
git pull --ff-only origin main
git switch -c minsu-altitude
```

`minsu-altitude`는 예시입니다. **본인이름-작업내용**으로 바꾸고, 아래 push에서도 같은 이름을 사용하세요. 새 작업마다 새 이름을 씁니다.

**② 파일 수정하고 GitHub에 올리기**

편집기에서 파일을 저장한 다음 실행합니다. 아래는 실제로 있는 `readme.md`를 수정했을 때의 예시입니다.

```bash
git status
git add readme.md
git diff --staged
git commit -m "README 설명 수정"
git push -u origin minsu-altitude
```

- 다른 파일을 수정했다면 `readme.md`를 **실제 파일 경로**로 바꿉니다. 여러 파일이면 각각 `git add`합니다.
- `git diff --staged`에서 이번에 올릴 변경이 맞는지 확인합니다. 회로도·사진은 해당 프로그램에서도 직접 확인합니다.
- 같은 브랜치에서 추가 수정할 때는 **add → commit → `git push`**를 반복합니다.

| 명령 | 하는 일 |
| --- | --- |
| `pull` | GitHub의 변경을 내 현재 브랜치에 반영 |
| `add` | 이번에 기록할 파일 변경 선택 |
| `commit` | 선택한 변경을 내 노트북의 Git 이력에 기록 |
| `push` | 내 커밋을 GitHub에 업로드 |

**편집기에서 저장하는 것, commit하는 것, push하는 것은 각각 별도입니다.**

**③ GitHub에서 팀원에게 확인받기**

1. 저장소에서 `Compare & pull request`를 누릅니다. 안 보이면 `Pull requests` → `New pull request`로 들어갑니다.
2. **base: `main` / compare: 내 브랜치**인지 확인합니다.
3. **무엇을 바꿨는지 / 무엇을 확인했는지 / 아직 확인하지 못한 것**을 적습니다.
4. 팀원 한 명 이상이 검토한 뒤 병합합니다. 이 요청을 **PR(Pull Request)**이라고 합니다.

push는 내 브랜치를 올리는 단계이고, PR 병합은 그 변경을 팀의 `main`에 합치는 단계입니다. [PR 안내](https://docs.github.com/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request)

**④ 합쳐진 결과 받기**

PR이 병합되고, 내 작업 폴더에 미커밋 변경이 없는 상태에서 실행합니다.

```bash
git switch main
git pull --ff-only origin main
```

다음 작업은 다시 ①부터 시작합니다. 병합이 끝난 브랜치는 재사용하지 않습니다.

> **하나라도 오류가 나오면 다음 명령으로 넘어가지 말고 멈추세요.** 아래 도움말을 확인하거나 오류 문구를 팀원에게 공유하면 됩니다.

### 꼭 지킬 약속

- **`main`에서 직접 수정·push하지 않고, 내 작업 브랜치를 사용합니다.**
- 같은 회로도·PCB 파일은 한 번에 한 명이 편집하고, 시작·종료를 공유합니다.
- 처음에는 `git add .` 대신 **파일을 지정해서** 추가합니다.
- 토큰·비밀번호, 빌드 결과, 개인 설정, 불필요한 대용량 파일은 올리지 않습니다.
- `--force`, `reset --hard`, `clean -fd`는 뜻을 모른 채 실행하지 않습니다.
- 코드에서 핀을 바꾸면 회로도·배선 설명도 함께 업데이트합니다.

### 막혔을 때만 열어보기

<details>
<summary><strong>기존 브랜치에서 작업을 이어가고 싶어요</strong></summary>

작업 폴더에 미커밋 변경이 없는 상태에서 실행합니다. 브랜치 이름은 본인 것으로 바꿉니다.

```bash
git switch minsu-altitude
git pull --ff-only
```

위 pull은 첫 push로 연결한 **같은 이름의 원격 작업 브랜치**를 받습니다. 아직 push하지 않았다면 pull은 생략합니다. 팀의 최신 `main`까지 내 작업에 반영하려면 현재 수정을 먼저 커밋하고 실행합니다.

```bash
git fetch origin
git merge --no-edit origin/main
```

확인 후 `git push`합니다. 충돌이 나면 아래 도움말을 확인합니다. [pull](https://git-scm.com/docs/git-pull) · [merge](https://git-scm.com/docs/git-merge)

</details>

<details>
<summary><strong>수정한 파일 때문에 pull이나 브랜치 전환이 막혀요</strong></summary>

`git status`로 현재 브랜치와 수정 파일을 확인합니다.

- **이미 내 작업 브랜치라면:** 남길 변경을 add·commit한 뒤 pull이나 브랜치 전환을 진행합니다.
- **`main`에서 먼저 수정했다면:** 아직 사용하지 않은 이름으로 작업 브랜치를 만들고, 그 브랜치에서 add·commit합니다.

```bash
git switch -c minsu-mywork
```

이름은 본인 작업에 맞게 바꿉니다. 아직 커밋하기 어렵거나 어느 브랜치의 작업인지 모르겠다면, 파일을 지우거나 복제 폴더를 새로 받기 전에 팀원과 확인하세요.

</details>

<details>
<summary><strong>push가 거절되거나 pull --ff-only가 실패해요</strong></summary>

- **권한 오류:** 본인 계정으로 인증했는지, 저장소 Write 권한이 있는지 확인합니다. 브랜치 보호 규칙에 걸렸다면 PR을 사용합니다.
- **작업 브랜치 push가 non-fast-forward로 거절됨:** 원격의 같은 브랜치에 다른 커밋이 있을 수 있습니다. 현재 수정을 커밋한 뒤, 해당 작업 브랜치에서 아래를 실행합니다.

```bash
git fetch origin
git merge --no-edit origin/minsu-altitude
```

이름을 본인 브랜치에 맞게 바꾸고, 병합·확인을 마친 뒤 다시 `git push`합니다.

- **`main`에서 `pull --ff-only` 실패:** 로컬과 원격 이력이 갈라졌을 수 있습니다. `git status`를 확인하고 통합 담당자와 정리합니다. 강제 push나 파일 삭제로 해결하지 않습니다. [pull 안내](https://git-scm.com/docs/git-pull)

</details>

<details>
<summary><strong>merge conflict라고 나와요</strong></summary>

같은 부분의 변경을 Git이 자동으로 합치지 못한 상태입니다.

1. `git status`로 충돌 파일을 확인합니다.
2. 수정한 팀원과 최종 내용을 정합니다. 텍스트 파일의 `<<<<<<<`, `=======`, `>>>>>>>` 표시는 최종 내용으로 정리하며 제거합니다.
3. 코드·회로도를 직접 확인한 뒤, 해결한 파일을 `git add`합니다.
4. `git commit -m "병합 충돌 해결"` 후 `git push`합니다.

한쪽 내용을 무조건 선택하면 다른 사람의 작업을 잃을 수 있습니다. 회로도·PCB는 담당자와 CAD에서 내용을 확인하세요. 작업 폴더가 깨끗한 상태에서 시작한 `git merge`를 중단하려면 `git merge --abort`를 사용할 수 있습니다. [충돌 해결 안내](https://git-scm.com/docs/git-merge)

</details>

<details>
<summary><strong>다른 파일까지 add했거나, 인증 설정이 궁금해요</strong></summary>

- **add 취소:** `git restore --staged readme.md`처럼 실행하면 해당 파일을 커밋 대상에서만 뺍니다. 수정 내용은 남습니다. `--staged` 없는 restore와 구분하세요. [restore 안내](https://git-scm.com/docs/git-restore)
- **이메일 공개 범위:** 본인 GitHub 설정의 `noreply` 이메일을 사용할 수 있습니다. `--global` 이름·이메일 설정은 이 컴퓨터의 다른 저장소에도 적용됩니다. [이메일 안내](https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address)
- **HTTPS 인증:** 계정 비밀번호 대신 인증 도구나 개인 액세스 토큰을 사용합니다. 토큰을 코드나 저장소 URL에 적지 않습니다. [인증 안내](https://docs.github.com/en/get-started/git-basics/about-remote-repositories)
- **제외할 파일:** `.gitignore`로 정하되, 이미 Git이 추적 중인 파일은 자동으로 제외되지 않습니다. 인증 정보가 올라갔다면 해당 정보를 폐기·재발급하고 관리자와 정리합니다. [ignore 안내](https://git-scm.com/docs/gitignore) · [민감 정보 처리](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)

</details>

---

## 2. 만들 기능

아래는 **구현 목표**입니다. 부품을 골랐다는 것과 기능 구현·검증이 끝났다는 것은 구분합니다.

| 기능 | 내용 |
| --- | --- |
| 로켓 점화 | 니크롬선 가열 방식의 이그나이터 장치 제작 예정 |
| 낙하산 사출 | 로켓 회수를 위한 낙하산 사출 기능 |
| 실시간 고도 계산 | MS5611의 기압을 이용해 기준 지점 대비 고도 계산 |
| GPS 실시간 위치 정보 전송 | GPS 위치와 위치 정보의 유효 여부 전달 |
| 지상국 실시간 통신 | LoRa로 비행 정보와 장치 상태 전송 |
| SD카드 실시간 기록 | 센서 정보와 장치 상태를 시간 정보와 함께 저장 |

센서 수집·무선 전송·SD 저장 주기와 데이터 형식은 별도로 정합니다. 기압 기반 고도와 GPS 고도도 구분해 기록합니다.

## 3. 사용할 부품

| 구분 | 부품·모듈 | 역할 |
| --- | --- | --- |
| MCU | **ESP32-WROOM-32-E** | 센서 정보 처리와 통신·기록 제어 |
| IMU | **WT901** | 가속도·각속도·자세 정보 수집 |
| 고도 센서 | **MS5611** | 기압·온도 측정, 기압 기반 고도 계산 |
| SD카드 모듈 | **별도 모듈명 없음** | 데이터 저장 |
| LoRa | **RYLR890** | 무선 송수신 |
| 릴레이 | **SRD-05VDC-SL-C** | 외부 회로 스위칭 |

**GPS 센서 모델은 미정입니다.** 실제 개발 보드, 핀 배정, 전원 구성, 지상국 구성도 추가로 정리합니다.

<details>
<summary><strong>부품 자료를 볼 때 확인할 것</strong></summary>

- ESP32 모듈의 제조사 표기는 `ESP32-WROOM-32E`입니다. 모듈과 개발 보드를 구분하고 실제 보드 핀맵을 확인합니다. [Espressif 자료](https://documentation.espressif.com/esp32-wroom-32e_esp32-wroom-32ue_datasheet_en.html)
- WT901의 세부 모델과 제공 인터페이스를 확인합니다. [WitMotion 자료](https://wit-motion.com/index.php/Module/84.html)
- MS5611은 기압을 측정하고, 그 값으로 고도를 계산합니다. [TE Connectivity 자료](https://www.te.com/en/product-MS561101BA03-50.html)
- **RYLR890은 SPI 방식입니다.** 다른 모델의 UART AT 명령 예제를 그대로 적용하지 않습니다. [RYLR890 자료](https://reyax.com/upload/products_download/download_file/RYLR890_EN.pdf)
- 릴레이 부품명만으로 보드 전체의 입력 조건을 정하지 않습니다. SD카드 모듈도 실물의 핀 표기와 제품 자료를 확인합니다.

</details>

---

## 4. 파일은 어디에 넣나요?

**코드는 `code`, 회로도는 `circuits`, 실제 사진은 `photos`, 추진부 계산 엑셀은 `calculations`에 넣습니다.** 아래는 앞으로 사용할 구성 예시이며, 필요한 폴더부터 만듭니다.

```text
freshman/
├── readme.md
├── LICENSE
├── code/                     # 코드
│   ├── rocket/               # 로켓 탑재부 코드
│   │   ├── main.cpp          # 전체 실행 순서와 모듈 연결
│   │   ├── common/           # pins.h, data_types.h 등 공통 약속
│   │   ├── sensors/          # MS5611, WT901, GPS 모듈
│   │   ├── radio/            # LoRa 송수신
│   │   ├── sd-card/          # SD카드 기록
│   │   └── outputs/          # 출력 기능 모듈
│   ├── ground/               # 지상국 코드
│   └── examples/             # 부품별 독립 실행 예제
├── circuits/                 # 회로도·PCB 원본
│   ├── rocket/               # 탑재부 CAD 프로젝트
│   ├── ground/               # 지상부 CAD 프로젝트
│   └── pdf/                  # 검토용 회로도 PDF
├── calculations/             # 로켓 추진부 계산용 엑셀 파일
├── photos/                   # 실제 부품·제작 사진
│   ├── parts/                # 보유 부품 앞·뒷면
│   ├── wiring/               # 배선과 커넥터
│   ├── assembly/             # 조립 상태
│   └── tests/                # 시험 장면
├── docs/                     # 설명 문서
│   ├── setup.md              # 개발 환경과 실행 방법
│   ├── wiring.md             # 핀맵과 배선 설명
│   └── data-format.md        # 통신·저장 데이터 규격
└── test-records/              # 날짜별 실험 기록과 소규모 로그
```

파일명과 빌드 설정은 개발 도구를 정한 뒤 맞춥니다. 각 보드에 올릴 코드는 별도 빌드 프로젝트로 두고, 지상국에서도 MCU를 사용하면 그 펌웨어와 PC 프로그램을 구분합니다. `examples`의 시험 코드는 본 프로젝트와 별도로 실행할 수 있게 둡니다.

### 담당은 이렇게 나눕니다

| 역할 | 맡을 영역 |
| --- | --- |
| 통합 담당 | `main.cpp`, 공통 데이터 구조, 빌드 설정 |
| 센서 담당 | `sensors` 안의 센서별 코드 |
| 통신·지상국 담당 | `radio`, `ground` |
| 기록 담당 | `sd-card`, 저장 로그 형식 |
| 출력 기능 담당 | `outputs`, 관련 설계·시험 기록 |
| 회로·제작 담당 | `circuits`, 배선 문서와 실물 사진 |
| 추진부 계산 파일 관리 | `calculations`, 계산 엑셀 파일과 변경 내역 |

인원에 따라 한 사람이 여러 역할을 맡아도 됩니다. 센서 담당은 센서별로 나눌 수 있습니다.

- **`main.cpp`와 공통 파일을 바꿀 때는 통합 담당자와 먼저 맞춥니다.** 핀 배정은 회로 담당자와도 함께 확인합니다.
- 센서 코드는 정해진 측정 데이터를 전달하고, 통신·SD 코드는 각각 전송·저장 형식으로 바꿉니다.
- 데이터의 이름·단위·시간 기준·유효 여부를 먼저 맞춰 `data_types.h`와 `data-format.md`에 기록합니다.
- 회로도는 CAD 프로젝트 원본과 필요한 라이브러리를 함께 보관합니다. PDF는 검토용입니다. 병합 후 CAD에서 직접 열어 확인합니다.

### 추진부 계산 엑셀은 이렇게 보관합니다

- 로켓 추진부 관련 계산값을 저장하는 엑셀 파일은 **`calculations/`**에 모읍니다.
- 파일 이름은 계산 내용을 알아볼 수 있게 정하고, 수정 내용은 커밋 메시지나 PR에 적습니다.
- 같은 엑셀 파일은 한 번에 한 명이 수정하고, 작업 전에 담당자와 공유합니다. 엑셀의 임시 파일과 개인 임시 파일은 커밋하지 않습니다.

### 사진과 실험 기록은 이렇게 남깁니다

사진 이름에는 **날짜 + 대상·제작 버전 + 촬영 내용**을 넣습니다.

```text
2026-11-12_ms5611_front.jpg
2026-11-12_rocket-r01_wiring-top.jpg
2026-11-12_rocket-r01_assembly-side.jpg
```

관련 문서에는 사진 속 부품·보드 버전과 확인할 부분을 적고 사진을 연결합니다. 사진은 필요한 장면을 읽기 좋은 용량으로 올리고, 대량의 원본 사진·영상·전체 로그는 외부 보관 위치를 문서에 연결합니다.

실험은 `test-records/2026-11-12_ms5611/`처럼 날짜와 내용으로 나눕니다. 각 실험의 `notes.md`에는 **사용 부품·보드 버전 / 코드 커밋 / 시험 조건 / 관찰 결과 / 미확인 사항**을 적고, 필요한 소규모 로그를 함께 둡니다.

예를 들어 센서 연결 핀이 바뀌었다면 **코드의 핀맵, 회로도, 배선 설명, 배선 사진을 같은 PR에서 함께 갱신**합니다.
