---
title: "SSH!-실습편"
date: 2017-10-20 08:26:28 -0400
categories: ssh webdev web
---
ssh(secure shell)은 프로토콜의 일종이다. 프로토콜의 종류로는 HTTP, FTP, HTTPS 등이 있다. HTTP는 브라우저와 웹서버간 통신을 위한 프로토콜이고, FTP는 로컬에서 호스팅 컴퓨터에 파일업로드시에 쓰인다. HTTPS는 HTTP와 비슷하지만 암호화된 형태이다. 이외에도 메일 전송에 쓰이는 프로토콜인 IMAP 등이 있다.

HTTP가 브라우저와 통신을 하기 위해 만들어진 프로토콜이라면 shell은 OS와 통신하기 위해 만들어진 프로토콜이다. SSH는 암호화된 shell 프로토콜이라는 점에서 HTTPS와 유사하다.

window는 별도의 ssh client인 putty

실습:

DigitalOcean이란?
<img src='https://cdn-images-1.medium.com/max/800/1*lYBKJmMiWuRTOYV2jUM0WA.gif'></img>
<img src='https://t1.daumcdn.net/cfile/tistory/260A913354E98C271A'></img>
DigitalOcean concentrates on three key selling points to stand out: simplicity, pricing, and high-performance virtual servers. They zero in on giving developers an easy and quick way to set up affordable Linux instances which they call droplets. DigitalOcean supports most of the modern Linux distros; Ubuntu, Fedora, Debian, and CentOS. It is straightforward to set up several applications on their droplets e.g. Ruby on Rails, LAMP, Ghost, Docker or stack.

Finally, DigitalOcean prides itself with a simple, user-friendly setup. Targeting developers only, providing Linux virtual machines and DNS management. It lacks hosted databases, configuration management, analytics, load balancing among others. DigitalOcean proudly markets themselves as a bare-bones IaaS provider for Linux developers.


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
