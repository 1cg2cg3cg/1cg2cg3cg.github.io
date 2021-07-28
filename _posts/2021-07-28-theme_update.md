---
date: 2021-07-28
title: "테마의 마스터 repository가 업데이트 됐을 때 반영하기"
excerpt: "commits behind mmistakes:master"

tags: page image

categories: pagetip
#toc: true
#toc_sticky: true
---

github page를 단순 기록용으로만 사용해오다가 다음과 같은 메세지를 발견했다.

![massage : N commits hehind master](https://github.com/1cg2cg3cg/images/blob/main/page/commits_behind_master/commits_behind_master.png?raw=true)

2일정도 무시하고 사용했는데 슬슬 거슬린다. cmd에서 명령어로 git을 사용하는 방법을 따로 공부하기 싫어서(단순 기록용도이기도 하고) 매 번 Add file로 작성해왔는데..

어쩔 수 없이 서칭을 통해 기본 개념을 파악했다. add, commit, push + pull, fetch, upstream... 뭐가 뭔지 설명하라고 하면 아직도 잘 모르겠다. 따로 정리해놓고 찾아가며 써야지

본론으로 문제 해결을 위해 [minimal-mistake 공식 홈페이지](https://mmistakes.github.io/minimal-mistakes/docs/upgrading/)를 참고해서

```
git remote add upstream https://github.com/mmistakes/minimal-mistakes.git

git pull upstream master
```

![fail](https://github.com/1cg2cg3cg/images/blob/main/page/commits_behind_master/fail.png?raw=true)
결과는 실패. 개념도 흔들리는데 명령어를 사용하려니 머리 깨진다. github 페이지에서 제시한 해결방법

```
# Step 1: From your project repository, check out a new branch and test the changes.

git checkout -b mmistakes-master master
git pull https://github.com/mmistakes/minimal-mistakes.git master

# Step 2: Merge the changes and update on GitHub.
git checkout master
git merge --no-ff mmistakes-master
git push origin master
```

![conflicts list](https://github.com/1cg2cg3cg/images/blob/main/page/commits_behind_master/conflicts_list.png?raw=true)

실패했지만 원인이 파일 충돌이라는 것을 알아냈다. 그리고

```
git status
```
![git status before](https://github.com/1cg2cg3cg/images/blob/main/page/commits_behind_master/git_status_before.png?raw=true)

의 빨간색 파일들과 같은 목록인 것을 발견하고 한참 고민 후 빨간색 파일들이 없어서 문제를 발생한다는 결론에 이르렀다. 근데 저 파일을 필요 없다고 지워도 된다고 했던 거 같은데..

어쨋든, 빨간 글씨를 초록색으로 만들기 위해

```
git add .
git status
```

![git status after](https://github.com/1cg2cg3cg/images/blob/main/page/commits_behind_master/git_status_after.png?raw=true)

```
git commit -m '1'
git merge upstream/master
```

엥.. 허무하게 해결했다.
![finish](https://github.com/1cg2cg3cg/images/blob/main/page/commits_behind_master/finish.png?raw=true)
