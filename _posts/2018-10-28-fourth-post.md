---
title: "SSH!-암호이론편 (Symmetrical and Asymmetrical Encryption)"
date: 2018-10-28 08:26:28 -0400
categories: ssh webdev web encryption symmetrical asymmetrical key exchange algorithm diffie hellman elliptic curve cryptography
---
ssh는 서로 다른 두 컴퓨터에서 remote로 암호 통신을 하기 위한 프로토콜이다. HTTPS와 다른 점은 HTTPS는 인터넷 통신을 위한 것이라면 ssh는 서로 다른 두 컴퓨터 os 끼리의 통신을 위한 것이라는 점이다.

이번 SSH!-이론편에서는 지난 [SSH!-실습편][SSH!-실습편]에 이어서 SSH와 관련된 암호 이론을 소개한다.

결론부터 말하자면, ssh는 첫 통신을 할때 Asymmetrical Encrytion을 통해 서로를 확인하고 이후 Symmetrical Encryption을 통해 통신한다. 둘 중 하나만 이용하면 될텐데 둘 다 이용하는 이유는 각자가 장단점이 있기 때문이다. 
우선 Asymmetrical Encryption을 이용하면 안전하게 암호화 통신을 할 수 있지만 암호화 및 복호화 연산이 상대적으로 더 복잡하여 시간이 많이 소모된다. 따라서 첫 통신만 Asymmetrical Encryption을 이용하고 이후에는 연산이 더 간단한 Symmetrical Encryption을 이용한다.
그럼 왜 처음 부터 Symmetrical Encryption을 이용하지 않을까? 왜냐하면 Symmetrical Encryption은 통신 시에 함께 통신 하고자 하는 특정 사람인지를 확인할 수 없어서 둘의 통신 사이에 해커가 중간자로 낄 수도 있다. 따라서 첫 통신은 Asymmetrical Encryption을 이용한다.
근데... 그래서 Symmetrical Encryption과 Asymmetrical Encryption이 뭐야?!

<b>Symmetrical Encryption</b>

Symmetrical Encryption이란 서로 암호 통신을 하고자하는 객체 Alice와 Bob이 동일한 키를 가지고 그 키를 통해 암호화된 컨텐츠를 주고 받는 방식이다. Alice와 Bob은 동일한 키를 가지고 있으니 복호화 해서 컨텐츠를 해독할 수 있다. 하지만 이 방식에는 문제가 있으니 바로 둘이 키를 공유하지 않는 처음에는 어떻게 동일한 키를 공유하게 하느냐가 문제이다. 둘 중 한 사람이 키를 생성해서 다른 한 사람에게 보내주면 되지 않냐고? 그럼 보내주는 그 키는 어떻게 암호화 할 것인데? 그렇지 않으면 둘의 통신을 엿듣고 있던 해커가 그 키를 볼 수도 있을텐데?

<b>Key Exchange Algorithm - Diffie Hellman Key Exchange</b>

여기서 키 교환 알고리즘이 등장한다. 키 교환 알고리즘이란 암호 통신을 하는 두 객체가 비가역적인 수학 연산을 이용해 서로의 고유 키를 안전하게 교환하여 동일한 키를 갖게 하는 알고리즘을 말한다. 

<b>   비가역적 연산을 이용한 암호화</b>
    
    (본 글에서는 수학적인 암호 연산과정을 최대한 추상화하여 핵심적인 컨셉만 설명하니 걱정말길 바란다!)
    비가역적인 연산인 modulo라는 것을 정의하도록 하자. 
    여기서 비가역적 연산이란 예를 들어 
    
    a modulo p = result
    
    라는 연산이 있다고 했을 때, 
    a와 p를 이용해 연산하면 result라는 결과 값이 나오는 것을 알 수 있지만
    반대로 result와 p 값을 안다고 해도 a 값을 유추할 수 없는 것을 비가역적 연산이라 말한다.

위의 비가역적 연산을 이용하면 Alice에게 a라는 고유 키, Bob에게 b라는 고유 키가, 그리고 누구에게나 공개 돼 있는 키 p가 있다고 했을 때,
Alice는 a modulo p 연산을 통해 결과 값 result_a를 Bob에게
Bob은 b modulo P 연산을 통해 결과 값 result_b를 Alice에게 안전하게 전달할 수 있다.
왜냐하면 중간에 해커가 result_a와 result_b를 탈취하더라도 비가역적 연산을 통해 생성된 값이기 때문에 원래 고유 키인 a와 b를 알 수 없다.
따라서 Alice와 Bob은 이를 통해 각자 고유 키인 a, b를 서로에게 안전하게 전송할 수 있고 이후 전송 받은 서로의 키에 자신의 키를 다시 연산하면 둘은 같은 키를 갖게된다.
이후 같이 공유하는 키를 이용해 암호화 통신을 하는 것을 Symmetrical Encryption이라고 한다.
하지만 서두에서 다루었듯이 Symmetrical Encryption은 첫 통신 부터 사용하기에는 부적절하다.

<b>Asymmetrical Encryption</b>
Asymmetrical Encryption은 서로 통신하는 대상을 확인하기 위해 Symmetrical Encryption에 private 키, public 키라는 개념을 더했다.
Alice와 Bob은 각각 private 키를 로컬에서 안전하게 보관한다. 그리고 각자의 private 키를 이용해 public 키를 생성하여 이를 네트워크에 공개한다.
이후 Alice는 Bob에게 키를 전송할 때에 result_a에 본인의 private 키를 sign하여 전송한다. 그러면 Bob result_a에 Alice의 private 키가 sign된 키를 받게 되고 이를 Alice의 public 키로 해석해 전송 받은 키가 Alice로 부터 온 키라는 것을 확인할 수 있다.
반대의 과정을 거치면 Alice 또한 Bob으로 부터 온 것을 확인할 수 있는 키를 전송 받을 수 있다.
이를 통해 서로가 확인된 키를 공유하게 되어 암호화 통신을 할 수 있다.

<b>별첨: Elliptic Curve Cryptography</b>

<img src = 'https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Elliptic_curve_on_Z61.svg/275px-Elliptic_curve_on_Z61.svg.png'/>

Symmetrical Encryption을 할 때에 Diffie Hellman Key Exchange을 키 교환 알고리즘으로 이용한다고 위에서 언급했다. Elliptic Curves는 Diffie Hellman Key Exchange의 대체 알고리즘으로서 비가역적 연산과정으로 modulo 연산을 이용하는 대신에 대수기하학적으로 elliptic curve를 이용한다. Elliptic Curves를 이용했을 때 연산량이 더 적기 때문에 이 알고리즘을 이용한다. 자세한 설명은 링크([What is the math behind elliptic curve cryptography?][What is the math behind elliptic curve cryptography?])를 첨부한다.

본 글은 수학적 내용을 추상화하여 글로 표현했기 때문에 이해에 한계가 있을 수 있습니다. 아래 링크에 걸어둔 Computerphile의 영상과 함께 보시면 보다 시각적인 이해도를 높일 수 있습니다.

감사합니다!

지난 회 [SSH!-실습편] 확인은 이곳에서! : https://github.com/dgsung/dgsung.github.io/blob/master/_posts/2018-10-28-third-post.md

MUST 구독! ssh에 관한 암호 이론을 직관적으로 설명하는 유튜브 채널 Computerphile 링크!:

<a href='https://www.youtube.com/watch?v=NmM9HA2MQGI'/>

<a href='https://www.youtube.com/watch?v=Yjrfm_oRO0w'/>

<a href='https://www.youtube.com/watch?v=vsXMMT2CqqE&t='/>

<a href='https://www.youtube.com/watch?v=NF1pwjL9-DE'/>


[SSH!-실습편]: https://github.com/dgsung/dgsung.github.io/blob/master/_posts/2018-10-28-third-post.md
[What is the math behind elliptic curve cryptography?]: https://hackernoon.com/what-is-the-math-behind-elliptic-curve-cryptography-f61b25253da3

