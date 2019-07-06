# 외부 의존성(External Dependency)을 갖고 작업하기

**Bazel**은 다른 프로젝트로부터 온 타겟에 의존성을 갖습니다. 이러한 다른 프로젝트들로부터 온 의존성을 외부 의존성이라고 부릅니다.

workspace directory에 있는 **WORKSPACE** 파일은 Bazel이 다른 프로젝트들의 소스들을 얻는 방법에 대해 알려줍니다. 이런 다른 프로젝트들은 한개 이상의 **BUILD** 파일들을 그 자신의 타겟들과 함께 갖고 있을 수 있습니다.

메인 프로젝트 안의 **BUILD** 파일들은 **WORKSPACE** 파일에 있는 그들의 이름을 사용함으로써 이런 외부 타겟에 의존성을 가질 수 있습니다.

예를 들면 한 시스템에서 두가지 프로젝트들이 있다고 가정하겠습니다.

```
/
  home/
    user/
      project1/
        WORKSPACE
        BUILD
        srcs/
          ...
      project2/
        WORKSPACE
        BUILD
        my-libs/
```

**project1**이 **/home/user/project2/BUILD**에 정의된 **:foo**라는 타겟에 의존하기를 원한다면, **project2** 라고 이름 붙은 저장소가 **/home/user/project2**에서 발견 될 수 있다고 구체화할 수 있습니다.

**WORKSPACE** 파일은 이용자가 파일 시스템의 다른 파트나 인터넷으로부터 다운로드한 것에서 온 타겟에 의존성을 갖게 해줍니다. 이용자는 또한 커스텀으로 '저장소 규칙'을 작성하여 더 복잡한 동작을 수행할 수 있습니다.

이 **WORKSPACE**파일은 BUILD 파일들과 같은 문법을 사용하지만, 다른 일련의 규칙들을 따릅니다. built-in된 규칙들의 풀 리스트는 Build 백과사전의 [Workspace Rules](https://docs.bazel.build/versions/master/be/workspace.html)와 [임베디드 스타크라크 저장소 규칙](https://docs.bazel.build/versions/master/repo/index.html)에 대한 문서에 있습니다.