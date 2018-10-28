---
title: "SSH!-이론편"
date: 2017-10-20 08:26:28 -0400
categories: ssh webdev web
---
ssh는 서로 다른 두 컴퓨터에서 remote로 암호 통신을 하기 위한 프로토콜이다. HTTPS와 다른 점은 HTTPS는 인터넷 통신을 위한 것이라면 ssh는 서로 다른 두 컴퓨터 os 끼리의 통신을 위한 것이라는 점이다.

이번
<a href='https://github.com/dgsung/dgsung.github.io/blob/master/_posts/2018-10-28-third-post.md'>dd</a>
```ssh
ssh {user}@{host}
```
여기서 user는 접속하려는 계정을 의미한다. 예를 들면 root계정으로 접속할 수 있다. host는 접속하려는 주소를 의미한다. 예를 들면 IP 주소나 도메인 주소가 될 수 있다.

apt-get: ubuntu 명령어. node의 npm이나 mac의 brew와 비슷한 명령어

```ubuntu
sudo apt-get install git
sudo apt-get install nodejs
```
git clone https
git clone ssh

rsync -av . root@{}:~/

Encryption
Symmetrical Encryption
key exchang algorithm - Difiie Hellman Key Exchange
Asymmetrical Encryption
Hashing

More information on apt-get : https://help.ubuntu.com/community/AptGet/Howto
More information on rsync : https://www.tecmint.com/rsync-local-remote-file-synchronization-commands/

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
