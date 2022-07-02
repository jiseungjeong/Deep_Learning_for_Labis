# Git/Github Workflow에 관하여

<aside>
💡 출처: 
[https://velog.io/@pond1029/Git-Workflow](https://velog.io/@pond1029/Git-Workflow) - 깃 워크플로우
https://github.com/mingrammer/git-tips
[https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-ko.md](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-ko.md) -깃 cheat_sheet
https://github.com/nvie/gitflow
[https://jud00.tistory.com/entry/CICD란-무엇일까](https://jud00.tistory.com/entry/CICD%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C) -CI/CD 개념

</aside>

 

# Git Workflow 란?

> **팀에서 브랜치를 어떻게 사용할 지에 대한 규칙**을 **Workflow**라고 한다.
Git을 사용하는 가장 대표적인 Workflow에는 Git flow, Github flow, Gitlab flow가 있다.
> 

# Git flow

브랜치의 역할이 명확하고 대규모 프로젝트에 적합하다.

5개의 브랜치로 관리하며 2개의 메인 브랜치인 **main**(=master), **develop**과 3개의 보조 브랜치인 **feature, release, hotfix**로 나뉜다.

![Untitled](/Deep%20Learning%20from%20Scratch/Git%20Github%20Workflow%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC%20ec50fb3e678f4fbfa6b08bce1827c0e3/Untitled.png)

- **main**
제품으로 출시(release)하는 브랜치
실제 배포 중인 **상용버전**
- **develop**
다음 출시 버전을 개발하는 브랜치
실제 작동 중인 버전의 다음 버전을 개발하기 위한 **메인 스트림**
- **feature**
기능을 개발하는 브랜치
develop 브랜치에서 뻗어나와 다시 develop 브랜치로 합쳐진다.
실제 **개발을 할 때 가장 많이 사용하는 브랜치**이다.
일반적으로 기능별 브랜치를 생성하고 기능 개발을 마치면 develop에 병합(merge)한다.
일반적으로 브랜치 명은 자유롭게 사용하며, origin에 commit 하지 않고 local에서만 작업한다.
- **release**
새로운 버전을 배포하기 위한 브랜치, QA의 용도
(QA: Quality assurance, 제품이나 서비스가 지정된 요구 사항을 충족하는지 여부를 결정하는 체계적인 프로세스)
주로 버그를 수정하는 디버깅만 커밋한다.
release-*라는 이름을 사용한다.
main에 병합했다면 develop에도 병합해서 변경된 내용을 일치시킨다.
- **hotfix**
상용 제품에서 버그가 발생했을 때 처리하는 브랜치
main 브랜치에서 뻗어나와 main과 develop에 합쳐진다.
버그 픽스를 위한 브랜치로 디버깅만 커밋하여, 보통 일회성으로만 사용한다.
버그를 수정하면 main과 develop에 모두 merge 시킨다.

# Git Flow 작업과정

1. 개인 작업은 develop에서 feature 브랜치를 따서 작업한다.
개인 작업이 끝나면 develop 브랜치에 merge한다.
2. develop브랜치에서 배포 준비가 끝나면 release 브랜치로 분할한다.
3. release 브랜치에서 디버깅하고 문제가 없으면 main과 develop 브랜치에 합친다.
4. main 브랜치를 배포한다.
5. 만약 배포 버전에서 문제가 생겨 급하게 수정해야 하면 hotfix 브랜치를 따서 작업한다.
6. hotfix에서 버그픽스가 끝나면 main과 develop에 합친다.

# Github Flow

> **하나의 main 브랜치**를 중점으로 운용하며 **pull request**를 활용하는 방식
> 

→ main 브랜치는 항상 최신 버전을 유지하며 안정적이어야 함.

![Untitled](/Deep%20Learning%20from%20Scratch/Git%20Github%20Workflow%EC%97%90%20%EA%B4%80%ED%95%98%EC%97%AC%20ec50fb3e678f4fbfa6b08bce1827c0e3/Untitled%201.png)

github flow는 브랜치의 용도가 명확하게 분류되지 않기 때문에 브랜치를 생성할 때 어떤 작업을 위한 브랜치인지 명확하게 작성해야함.

일반적으로 feature 브랜치의 작업은 local 저장소가 아닌 **원격 저장소**에 저장함.

# Github Flow 작업 과정

1. 개인 작업은 feature 브랜치에서 작업하며 작업이 끝나면 pull request를 생성한다.
2. pull request에서 코드 리뷰 후에 문제가 없으면 main 브랜치로 merge한다.
3. main에 병합하면 바로 배포 작업을 수행한다. (CI 자동화 권장)

## CI(Continuos Intergraion, 지속적 통합)

> 애플리케이션의 버그 수정이나 새로운 코드 변경이 **주기적**으로 빌드 및 테스트되면서 **공유**되는 **레포지토리에 merge**되는 것을 의미한다.
> 
- 1. ***코드 변경사항을 주기적으로 빈번하게 merge***
    
    → 가능한 작은 단위로 나누어 주기적으로 빈번히 개발 및 지속적 통합!!
    
    <aside>
    🔥 1. 개발자들은 계속해서 github와 같은 관리 시스템에 통합한다.
    2. 통합한 코드가 제대로 동작하는지 빌드 및 테스트를 진행한다.
    3. 버그가 발생하거나 하면 다음에 해야할 목록을 정리해두고 다음날이나 버그를 해결한다.
    
    </aside>
    
- 2. ***통합 단계의 자동화***
    
    위의 **주기적 빈번한 merge**는 **“귀찮다!”**
    
    → 그래서 자동화를 이용하는데, github에 코드만 올리고 나머지 작업인 테스트와 빌드는 프로그램이 자동으로 해준다.
    
    <aside>
    🔥 1. 위와 동일하게 개발자들은 github와 같은 관리 시스템에 작업한 코드를 통합한다.
    2. 빌드 및 테스트는 자동으로 진행되므로, 버그가 생기면 다음날 온 버그를 확인해서 버그를 해결한다.
    
    </aside>
    

### CI 의 장점

- 코드의 검증에 들어가는 시간이 줄어든다.
- 개발 편의성이 증가한다.
- 항상 테스트 코드를 통과한 코드만이 레포에 올라가기 때문에, 좋은 코드 퀄리티를 유지할 수 있다.

# Git&Github Workflow 구축

아마 선배가 하실듯..?