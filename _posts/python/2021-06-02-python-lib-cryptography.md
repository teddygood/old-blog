---  
title: "[Python] Build package cryptography"  
categories: Python  
tag:
  - Pycharm
  - requirements
  - python
  - docker
date: 2021-06-02
---  

삽질 기록

---

## 사건

Django 블로그 프로젝트를 docker로 옮기는 도중 문제가 생겼다. 그 문제는 alpine linux와 python에서 암호화 알고리즘이 구현된 패키지인 cryptography의 호환성 문제였다. 

```Dockerfile
FROM python:3.8-alpine
```

```
cryptography==3.4.7
```

현재 Dockerfile에서 사용하는 image 버전과 requirements.txt에 적힌 cryptography 버전은 위와 같다.

```shell
$ docker-compose build
```

```
ERROR: No matching distribution found for cryptography==3.4.7
```

`Dockerfile`, `docker-compose.yml`을 다 만들고 난 후에 마지막으로 위의 명령어로 빌드를 하던 중 Error를 만났다. 

![crypto-doc](/assets/images/cryptography-doc.jpg)

아무리 구글링을 해도 찾지를 못 해서 공식 문서를 보기로 결정했고 어느정도 해결책을 찾았다.

대략 요약하면 cryptography 패키지는 Rust를 사용하기에 Rust compiler도 같이 다운로드 해야지 돌아간다는 것이다. 좀 더 설명을 추가하자면 Rust는 cryptography를 빌드할 때 필요하다. 그렇기에 multi-stage를 사용하여 빌드하라고 한다.

물론 multi-stage를 사용하면 이미지를 경량화하는 것도 좋은 방법이지만 도커를 자세히 배운 사람이 아니라 잘 모르기 때문에 이 방법은 패스했다. 

```shell
$ sudo apk add gcc musl-dev python3-dev libffi-dev openssl-dev cargo
```



![더 상세한 details](/assets/images/crypto-building-error.jpg)



## References

>-  [Cryptography installation](https://cryptography.io/en/latest/installation/)
>-  [Dependencies to build on Alpine Linux?](https://github.com/pyca/cryptography/issues/5776)
>- [Using Alpine can make Python Docker builds 50x slower](https://pythonspeed.com/articles/alpine-docker-python/)
>- [The best Dockeer base image for Python application](https://pythonspeed.com/articles/base-image-python-docker-images/)

[wsl2 docker](https://www.44bits.io/ko/post/wsl2-install-and-basic-usage)
