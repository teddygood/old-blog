---  
title: "[Python] Pycharm requirement"  
categories: Python  
tag:
  - Pycharm
  - requirements
  - python
  - docker
date: 2021-06-01
---  

삽질 기록

---

## 사건

`Package requirements 'requests==2.25.13' is not satisfied`

Django 블로그 만들기가 끝난 후 이제 Docker로 옮기기 위해 Dockerfile을 만들고 requirements.txt도 만들었는데 Pycharm에서 갑자기 위와 같은 이상한 문구가 떴다.

대충 details를 읽어보니까 크게 중요한 건 아닌 거 같다고 생각하고 details에서 추천하는 방법으로 `pip install --update pip`를 시도했는데 권한을 체크하라는 문구만 뜨고 해결되지는 않았다.

무시하고 하던 걸 계속 진행하려 했으나 자꾸 파이참에 뜨는 문구가 거슬려서 해결하기 위해 구글링을 시도했다.

## 해결

[stackoverflow](https://stackoverflow.com/questions/55306431/pycharm-warns-package-requirement-not-satisfied-when-using-pipenv-to-install-pac)  

[IDEs Support (IntelliJ Platform) JetBrains](https://intellij-support.jetbrains.com/hc/en-us/community/posts/360001522219-Package-requirements-not-satisfied-though-they-are-?page=1#community_comment_360000242119)  

`File -> Invalidate Caches/Restart.. -> Invalidate and Restart`

위의 사이트들을 찾고 빠르게 해결할 수 있었다. 

너무 빨리 해결할 수 있어서 캡처도 못 했다.

끝.

## 해결한 줄 알았으나 아니었다

package들을 지웠었으므로 다시 install을 해주라는 문구가 뜨길래 해줬다.

근데 또 다시 뜨는 문구.

![문구](/assets/images/package-requirement.jpg)  

이번에는 이미지를 찍어왔다.

![details](/assets/images/installing-packages-failed.jpg)

![더 상세한 details](/assets/images/pycharm-details.jpg)

문제는 `requests가 2.25.13 버전이 없는데 왜 이렇게 requirements.txt에 적혀있냐`였다.

근데 난 requirements.txt를 건드린 적이 없는데? 

그저 `pip freeze > requirements.txt`를 사용해서 만들었는데 상당히 억울하다.

혹시나 이런 버전이 있나 싶어서 requests 공식 문서에도 들어가서 확인했는데 그런 건 없다. 내부적으로 버전이 설정되어 있는 것이 아닌가 추측해본다. 공식 문서에도 2.25.1까지 표기되어 있었다.

## 진짜 해결

어쨌든 해결 방법은 엄청 간단하다. requirements.txt에 적혀있는 `requests==2.25.13`을 `requests==2.25.1`로 바꾸면 위에서 뜬 문구는 뜨지 않는다.

진짜 끝.