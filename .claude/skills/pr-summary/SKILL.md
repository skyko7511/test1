---
name: pr-summary
description: 풀 리퀘스트의 변경사항을 요약한다
context: fork
agent: Explore
allowed-tools: Bash(gh *), Bash(git *)
---

## 풀 리퀘스트 컨텍스트
gh CLI가 없거나 PR이 없으면 git으로 기본 브랜치(main) 대비 현재 브랜치의 변경사항을 대신 보여준다.

- 현재 브랜치: !`git branch --show-current`
- 커밋 목록: !`git log --oneline main..HEAD 2>/dev/null || echo "(main 대비 새 커밋 없음)"`
- 변경된 파일: !`gh pr diff --name-only 2>/dev/null || git diff --name-only main...HEAD 2>/dev/null || echo "(변경 파일 없음)"`
- PR diff: !`gh pr diff 2>/dev/null || git diff main...HEAD 2>/dev/null || echo "(diff 없음)"`
- PR 코멘트: !`gh pr view --comments 2>/dev/null || echo "(gh CLI가 없거나 PR이 없어 코멘트를 가져올 수 없음)"`

## 할 일
이 풀 리퀘스트를 요약하라. 핵심 변경사항, 하위 호환성을 깨는 변경,
코멘트에서 제기된 우려 사항을 강조해서 정리한다.
diff가 비어 있으면 요약할 변경사항이 없다고 알리고, 별도 브랜치에서 작업하거나 gh CLI를 설치하라고 안내한다.
