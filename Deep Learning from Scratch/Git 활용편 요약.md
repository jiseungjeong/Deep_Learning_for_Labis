# Git 활용편 요약

---

<aside>
💡 **출처:**

[https://www.youtube.com/watch?v=he3VFI-rjs8](https://www.youtube.com/watch?v=he3VFI-rjs8) - Git 기본편

[https://www.youtube.com/watch?v=eSBNr7Nfofs](https://www.youtube.com/watch?v=eSBNr7Nfofs) - Git 활용편

</aside>

# Summary

---

Main default(주된 브랜치, 출시용 브랜치)

Develop(직접적인 개발을 진행하지는 않음, 개발된 것들 합치는 브랜치)

Feature/isssue-#1-keyword (직접적인 개발을 진행함) ex) feature/issue-#1-login

main에서 develop branch에서 feature branch에서 계속 업데이트(구현)

구현 다하면 develop으로 합침

# Pull request (PR)

---

- Review 개념을 이용해 합칠 때 검토 가능하고, 검토 후 serge
- New pull request를 이용해서 pr 만들고, compare 내용을 base로 합침.
- Description은 리뷰어한테 알려줄 사항
- reviewer는 검토자, assignees는 개발자
- Pull request도 id로 구별함

# Issue란?(markdown 지원함)

---

- 기능 하나를 의미함.(ex) 로그인 기능 하나가 이슈 하나를 의미함.)

Title: login

Write: * 아이디는 10~15글자

* 비밀번호는 15~20글자

issue에서 Login 기능을 구현하기 위해 개발자 정할 때 assignees를 할당함(collaborator 로 초대하면 최대 10명 할당할 수 있음)

- Labels 선택할 수도 있음
- project도 등록할 수 있음
- milestone을 등록 할 수 있음

이후 submit new issue를 누르면 됨. 이후 issue에는 #1처럼 아이디가 생성되게 되는 데, GitHub에서는 샵1로 이슈를 식별함.

projects는 등록을 projects 탭에서 해야하는데, create new project를 눌러 project board name을 적고 description도 적으면 됨.

Project template도 고를 수 있는데, automated kanban이 편하기에 이를 권장함.

Milestone은 Projects 탭에서 등록을 해야하는 데, 타이틀은 login처럼 기능관련 이름으로 하고, due date를 설정하여 마감기한을 정할 수 있음.

Terminal

- Git branch -a : 브랜치 목록 싹 꺼내기
- Remotes/origin : 설치파일(실행을 시키지 않는 이상 반영이 안 된다.) ex) 크롬을 설치해야한다.
- Git checkout -t remote/origin/…(브랜치 명) (-t는 remotes 브랜치를 설치해줌 t는 track을 의미)
- Git status : 변경사항을 보여줌 이후 add, commit -m “” 하면 됨. 이후 push 까지.

# Keyword(키워드 샵1) (default branch를 develop branch로 설정!) (이슈 자동으로 닫힘)

---

- Close
- Closes
- Closed
- Fix
- Fixes
- Fixed
- Resolve
- Resolves
- Resolved