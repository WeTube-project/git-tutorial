# git 실습하기

## 한번하는 작업

1. fork 버튼을 눌러 저장소를 fork합니다.

2. 원격 저장소를 가져옵니다.

```git
git clone <fork된 내 저장소 주소>
```

4. clone명령으로 생성된 폴더로 이동합니다.

```git
cd <생성된 폴더 이름>
```

5. upstream 원격 저장소를 추가합니다.

```git
git remote add upstream <공용 원격 저장소 주소>
```

예를 들어, WeTube-project의 git-training 주소를 추가합니다.

6. 다음을 입력하여 origin과 upstream 정보를 확인합니다.

```git
git remote -v
```

- origin : 공용 저장소를 개인계정에 fork한 저장소
- upstream : 공용 저장소

## 매번하는 작업

- 작업 상태를 수시로 확인합니다.

```git
git status
```

1. 작업 브랜치를 만듭니다.

```git
git switch -c <브랜치 이름> origin/main
```

브랜치 이름은 작업한 내용을 표현합니다.

2. upstream 원격 저장소의 최신 상태를 반영합니다.

```git
git fetch upstream main
git rebase upstream/main
```

도중에 팀원이 upstream을 변경하였을 경우 충돌하므로  
작업을 시작하기 전에 최신상태로 변경합니다.

3. 작업을 합니다.  
   코드를 작성하여 원하는 작업을 합니다.

4. commit을 작성합니다.

```git
git add .
```

변경된 것을 추가합니다.

```git
git commit
```

커밋메시지 작성후 esc를 누르고 :wq를 하여 저장합니다.

5. 원격 저장소에 작업한 브랜치를 올립니다.

```git
git push origin <branch 이름>
```

6. pull request 합니다.  
   fork된 내 저장소에서 Compare & request를 누릅니다.

   내용을 작성하고 Create pull request를 누릅니다.

7. merge하기전 다음 두 가지를 체크합니다.

- 여러 개의 커밋 메시지를 하나로 통합합니다.  
   3개의 커밋 메시지를 통합하는 경우를 예시로 듭니다.

```git
git rebase -i HEAD~3
```

- upstream 원격 저장소의 최신상태를 반영합니다.

```git
git fetch upstream main
git rebase upstream/main
```

도중에 팀원이 upstream을 변경하였을 경우 충돌하므로  
merge하기 전에 한번 더 최신상태로 변경합니다.

8. merge합니다.  
   공용 원격 저장소(WeTube-project의 git-tutorial)의 Pull requests탭에서  
   Merge pull request를 누릅니다.

9. fork된 내 저장소의 현재 branch를 main에 merge합니다.

```git
git switch main
```

main으로 이동합니다.

```git
git merge <main에 merge하고자 하는 branch 이름>
```

merge합니다.

## 주의사항

1. fork된 내 저장소에서 작업합니다.
2. 공용 원격 저장소에 commit, push하지 않습니다.
3. 다른 팀원의 코드를 merge하지 않습니다.
4. 작업하기전과 merge하기전에 upstream 원격 저장소의 최신 상태를 반영합니다.

   ```git
   git fetch upstream main
   git rebase upstream/main
   ```
