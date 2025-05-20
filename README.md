

# 📘 Git 명령어 요약 정리

## ✅ 1. Git 기본 설정 및 초기화

| 명령어 | 설명 |
|--------|------|
| `git config --global user.name "이름"` | 사용자 이름 설정 |
| `git config --global user.email "이메일"` | 사용자 이메일 설정 |
| `git config --global --list` | 전체 설정 목록 보기 |
| `git config --global init.defaultBranch main` | 기본 브랜치를 main으로 설정 |
| `git init` | 현재 폴더를 Git 저장소로 초기화 |
| `git clone [URL]` | 원격 저장소를 로컬에 복제 |

## 📂 2. 상태 확인 및 로그 조회

| 명령어 | 설명 |
|--------|------|
| `git status` | 작업 디렉토리 및 스테이징 상태 확인 |
| `git log` | 커밋 로그 (J/K로 이동, `:q`로 종료) |
| `git log --oneline` | 커밋 로그를 한 줄 요약으로 표시 |
| `git diff` | 변경된 파일 내용 비교 |

## 📥 3. 변경사항 스테이징 & 커밋

| 명령어 | 설명 |
|--------|------|
| `git add .` | 전체 파일 스테이징 |
| `git add [파일명]` | 특정 파일만 스테이징 |
| `git commit -m "메시지"` | 커밋 메시지 작성 |
| `git commit -am "메시지"` | 수정된 파일 스테이징 + 커밋 (신규 파일은 제외됨) |

## 🔀 4. 브랜치 관련

| 명령어 | 설명 |
|--------|------|
| `git branch` | 브랜치 목록 확인 |
| `git branch [이름]` | 새 브랜치 생성 |
| `git switch [이름]` / `git checkout [이름]` | 브랜치 이동 |
| `git switch -c [이름]` / `git checkout -b [이름]` | 브랜치 생성 + 이동 |
| `git branch -d [이름]` | 브랜치 삭제 (병합된 경우만) |
| `git branch -D [이름]` | 브랜치 강제 삭제 (미병합도 삭제됨) |

## 🔄 5. 원격 저장소 연동 및 Push/Pull

| 명령어 | 설명 |
|--------|------|
| `git remote add origin [URL]` | 원격 저장소 연결 |
| `git push -u origin main` | main 브랜치를 원격에 업로드 및 추적 설정 |
| `git push` | 변경사항 푸시 |
| `git pull` | 원격 저장소 최신 커밋 가져오기 + 병합 |
| `git fetch` | 변경사항만 가져오기 (병합은 안 함) |

## 🕰 6. Git 과거로 돌아가는 방법

### 🔁 과거 커밋으로 이동

| 목적 | 명령어 | 설명 |
|------|--------|------|
| 잠깐 과거 커밋 보기 | `git checkout [커밋ID]` | 임시 이동 (detached HEAD) |
| 커밋만 되돌리기 | `git reset --soft [커밋ID]` | 커밋 취소 (수정 내용 유지) |
| 커밋 + add 되돌리기 | `git reset --mixed [커밋ID]` | 스테이징도 취소 |
| 완전 초기화 | `git reset --hard [커밋ID]` | 되돌리고 작업 내용 삭제 (주의!) |

### 🔙 커밋 취소 (이력 유지)

| 명령어 | 설명 |
|--------|------|
| `git revert [커밋ID]` | 해당 커밋을 되돌리는 새 커밋 생성 |
| `git rm [파일명]` → `git revert --continue` | 충돌 시 해결 후 진행 |

### 🔄 임시 작업 되돌리기

| 명령어 | 설명 |
|--------|------|
| `git restore [파일명]` | 수정한 파일을 취소 |
| `git restore --staged [파일명]` | add된 파일 스테이징 취소 |

## 🔃 7. 브랜치 병합 & Rebase

### 📌 일반 병합
```
git switch main
git merge feature/login
```

### 📌 Rebase 방식
```
git switch feature/header
git rebase main
# 충돌 시: git add → git rebase --continue
```

### 📌 병합 후 브랜치 삭제
```
git branch -d feature/login
git push origin --delete feature/login
```

## ⚔ 8. 충돌 해결 시 VS Code 옵션

| 옵션 | 설명 |
|------|------|
| ✅ Accept Current Change | 현재 브랜치(HEAD) 내용 유지 |
| ✅ Accept Incoming Change | 병합 브랜치(MERGE_HEAD) 내용 사용 |
| ✅ Accept Both Changes | 양쪽 코드 모두 포함 (수동 수정 필요) |
| ✅ Compare Changes | 시각적으로 비교 후 직접 편집 |

- 병합 중단: `git merge --abort`
- 리베이스 중단: `git rebase --abort`

## 🌿 9. 원격 브랜치에서 로컬 브랜치 생성 및 이동
```
git switch -t origin/[브랜치명]
```

## 🧹 10. 기타 유용한 명령어

| 명령어 | 설명 |
|--------|------|
| `git stash` | 변경사항 임시 저장 |
| `git stash pop` | 저장한 변경사항 복원 |
| `git reset --hard HEAD` | 현재 커밋 상태로 되돌림 (주의!) |
| `git rm [파일명]` | Git에서 파일 삭제 |
