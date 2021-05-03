---  
title: "[GitHub Blog] 폰트와 폰트 크기 변경"  
categories: Blog  
tag:
  - Blog
  - Github Blog
  - minimal-mistsakes
  - Jekyll
date: 2021-05-01
last_modified_at: 2021-05-01
--- 

드디어 바꾸는 블로그 폰트

---

## 지금까지 폰트와 폰트 크기 변경을 하지 않은 이유

지금까지 나는 가독성이 떨어지는 폰트와 폰트 크기를 유지하면서 블로그에 글을 꾸역꾸역 적었다. 수정하지 않고 그대로 글을 올리고 있던 이유는 단지 블로그에 올리는 것이 책 리뷰 밖에 없었기 때문이다. GitHub 블로그는 아무래도 접근성이 낮다 보니까 어짜피 볼 사람도 없을 것이라고 예상하고 방치했다.

이대로 계속 사용할까 고민도 했지만 현재 `나는 리뷰어다 2021`에도 참여하고 앞으로는 공부했던 것을 정리하여 올려 볼 예정이기 때문에 가독성이 좋도록 폰트와 폰트 크기를 수정했다. 

![이전 블로그1](/assets/images/past-blog-1.jpg)
![이전 블로그2](/assets/images/past-blog-2.jpg)
**<center>[이전 블로그]</center>**

![현재 블로그1](/assets/images/current-blog-1.jpg)
![현재 블로그2](/assets/images/current-blog-2.jpg)
**<center>[현재 블로그]</center>**

별로 달라진 것이 없어 보이지만 그래도 조금이나마 더 보기 좋게 바꿨다.

## 폰트 변경 준비

[Google Fonts](https://fonts.google.com/?subset=korean)에 들어가면 공개된 폰트들이 있다. 여기서 골라서 사용하면 되지만 개인적으로 원하는 폰트들이 없었다.

구글링을 한 결과 [블로그 리뉴얼, 그리고 D2Coding 웹폰트](https://noonnu.cc/font_page?commit=filter&search=%EB%82%98%EB%88%94&order_by=pd)라는 글을 찾게 됐다.

![D2coding star](/assets/images/d2coding-star.jpg)

바로 [이분의 깃허브](https://github.com/wan2land/d2coding)에 들어가서 Star을 눌러주고 블로그에 적용을 시켰다.(wan2land님 감사합니다!)

개발용 폰트는 구했으니 남은 건 일반 글에서 쓰일 폰트다. `Noto Sans KR`폰트를 쓸까 잠시 고민했지만 좀 더 읽기 편한 느낌을 찾고 싶었다. 그러다 찾은 폰트가 `나눔스퀘어`폰트이다.

그러나 나눔스퀘어 폰트는 네이버에서 만든 것이기 때문에 라이선스를 잘 확인해볼 필요가 있다. [네이버 나눔 글꼴, 마루 부리 글꼴 라이센스 안내](https://help.naver.com/support/contents/contents.help?serviceNo=1074&categoryNo=3497) 글을 네이버 고객센터에서 찾을 수 있었다.

![나눔 라이선스](/assets/images/nanum-license.jpg)

그렇다고 한다. 잘 사용하겠습니다. 이제 다 된 거나 다름없습니다.

근데 웹에 적용시킬 방법을 모르겠네? 이럴 땐 바로 구글에게 물어봅시다. 

![나눔 폰트 구글 결과](/assets/images/nanum-google.jpg)

바로 나오죠? 이럴 때 느끼는 거지만 GitHub, 오픈 소스 정말 감사합니다.(오픈 소스를 사용할 때는 GitHub Repository에 Star 눌러주는 거 잊지 맙시다.) [moonspam님의 NanumSquare Repository](https://github.com/moonspam/NanumSquare)(moonspam님 감사합니다!)

## 폰트 변경

자신의 Local Repository에서 `\_sass\minimal-mistakes`경로에 있는 `_variables.scss`파일을 수정한다. `sans-serif`에는 "NanumSquare"을 `monospace`에는 "D2Coding"을 추가한다.

```scss
/* system typefaces */
$serif: Georgia, Times, serif !default;
$sans-serif: -apple-system, BlinkMacSystemFont, "NanumSquare", "Roboto", "Segoe UI",
  "Helvetica Neue", "Lucida Grande", Arial, sans-serif !default;
$monospace: "D2Coding", Monaco, Consolas, "Lucida Console", monospace !default;
```

자신의 Local Repository에서 `\assets\css`경로에 있는 `main.scss`파일을 수정한다. import 2줄을 추가하면 된다.

```scss
@import "minimal-mistakes"; // main partials

@import url("//cdn.jsdelivr.net/gh/wan2land/d2coding/d2coding-full.css"); // d2coding font
@import url("//cdn.jsdelivr.net/gh/moonspam/NanumSquare@1.0/nanumsquare.css"); // nanum square font
```

위의 코드는 현재 블로그의 코드이며
[commit 5c16d5c](https://github.com/teddygood/teddygood.github.io/commit/5c16d5ccac7e8d96374d9fd396f84b809437c81b), 
[commit 4ef6ea4](https://github.com/teddygood/teddygood.github.io/commit/4ef6ea4dfc44626416112a217f6c1502b83a727b), [commit 7b61678](https://github.com/teddygood/teddygood.github.io/commit/7b616786da3ca860c140e7440947d66aecbb258c)를 참고하여 바꾸면 된다.(원래 이렇게 의미없이 커밋하면 안 되는데 이 때는 지킬 블로그 테스트를 하는 방법을 몰랐습니다. 저처럼 커밋하지 마시고 한 번에 커밋하세요.)

## 폰트 크기 변경

자신의 Local Repository에서 `\_sass\minimal-mistakes`경로에 있는 `_reset.scss`파일을 수정한다. 

```scss
html {
  /* apply a natural box layout model to all elements */
  box-sizing: border-box;
  background-color: $background-color;
  font-size: 16px;

  @include breakpoint($medium) {
    font-size: 18px;
  }

  @include breakpoint($large) {
    font-size: 18px;
  }

  @include breakpoint($x-large) {
    font-size: 18px;
  }

  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;
}
```
반응형 웹페이지를 위해서 minimal-mistakes는 scss의 breakpoint 기능을 사용한다. 위의 코드는 현재 블로그의 폰트 사이즈이며 [commit 2037564](https://github.com/teddygood/teddygood.github.io/commit/203756487086ca3efdf791327296672745b2755a)를 참고하여 원하는 크기로 바꾸면 된다.

## References

>- [블로그 리뉴얼, 그리고 D2Coding 웹폰트](https://wani.kr/posts/2019/05/25/d2coding-webfont/)
>- [블로그 한글 폰트 변경](https://devinlife.com/howto%20github%20pages/set-font/)
>- [GitHub Pages 기타 설정](https://devinlife.com/howto%20github%20pages/github-pages-settings/)
>- [moonspam님의 NanumSqaure Repository](https://github.com/moonspam/NanumSquare)
>- [wna2land님의 d2coding Repository](https://github.com/wan2land/d2coding)