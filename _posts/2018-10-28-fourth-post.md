---
title: "SSH!-이론편"
date: 2018-10-28 08:26:28 -0400
categories: ssh webdev web encryption
---
ssh는 서로 다른 두 컴퓨터에서 remote로 암호 통신을 하기 위한 프로토콜이다. HTTPS와 다른 점은 HTTPS는 인터넷 통신을 위한 것이라면 ssh는 서로 다른 두 컴퓨터 os 끼리의 통신을 위한 것이라는 점이다.

이번 SSH!-이론편에서는 지난 [SSH!-실습편][SSH!-실습편]에 이어서 SSH와 관련된 암호 이론을 소개한다.

<bold>Symmetrical Encryption</bold>
Symmetrical Encryption이란 서로 암호 통신을 하고자하는 객체 Alice와 Bob이 동일한 키를 가지고 그 키를 통해 암호화된 컨텐츠를 주고 받는 방식이다. Alice와 Bob은 동일한 키를 가지고 있으니 복호화 해서 컨텐츠를 해독할 수 있다. 하지만 이 방식에는 문제가 있으니 바로 둘이 키를 공유하지 않는 처음에는 어떻게 동일한 키를 공유하게 하느냐가 문제이다. 둘 중 한 사람이 키를 생성해서 다른 한 사람에게 보내주면 되지 않냐고? 그럼 보내주는 그 키는 어떻게 암호화 할 것인데? 그렇지 않으면 둘의 통신을 엿듣고 있던 해커가 그 키를 볼 수도 있을텐데?

<bold>Key Exchange Algorithm - Diffie Hellman Key Exchange</bold>

<bold>비가역적 연산을 이용한 암호화</bold>
(본 글에서는 수학적인 암호 연산과정을 최대한 추상화하여 핵심적인 컨셉만 설명하니 걱정말길 바란다!)
암호화란 암호화하고자 하는 컨텐츠에 특별한 코드로 인코딩하여 권한을 가진 사람을 제외하고는 해석하지 못하게 하는 것을 말한다.
이를 위해 

<bold>Asymmetrical Encryption</bold>


```ubuntu
sudo apt-get install git
sudo apt-get install nodejs
```


지난 회 [SSH!-실습편] 확인은 이곳에서! : https://github.com/dgsung/dgsung.github.io/blob/master/_posts/2018-10-28-third-post.md

MUST 구독! ssh에 관한 암호 이론을 직관적으로 설명하는 유튜브 채널 Computerphile 링크!:

https://www.youtube.com/watch?v=NmM9HA2MQGI

https://www.youtube.com/watch?v=Yjrfm_oRO0w

https://www.youtube.com/watch?v=vsXMMT2CqqE&t=

https://www.youtube.com/watch?v=NF1pwjL9-DE


[SSH!-실습편]: https://github.com/dgsung/dgsung.github.io/blob/master/_posts/2018-10-28-third-post.md

