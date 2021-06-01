---  
title: "[Python] Pycharm requirements"  
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