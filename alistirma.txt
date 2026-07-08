1: Öncelikle sistemdeki tüm container, image ve volumeleri görelim. Bunun için ayrı ayrı listeleme komutlarını girelim. Ve ardından temizlik yapmak adına makinenizdeki tüm containerları, imageleri ve volumeleri temizleyelim. Bunun iki yöntemi var. Bakalım siz kolay olanı mı seçeceksiniz. 

->

_______________CONTAINER_____________________________
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES



_____________IMAGE_________________

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker image ls
                                                                                  
IMAGE          ID             DISK USAGE   CONTENT SIZE   EXTRA
nginx:latest   ec4ed8b5299e        241MB           66MB


utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker image rm -f ec4ed8b
Untagged: nginx:latest
Deleted: sha256:ec4ed8b5299e5e90694af7750eb6dffd2627317d30544d056b0371f8082f7bce
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker image ls
                                                                                  
IMAGE   ID             DISK USAGE   CONTENT SIZE   EXTRA

______________________________VOLUME________________________
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker volume ls
DRIVER    VOLUME NAME
<-




2: centos, alpine, nginx, httpd:alpine, ozgurozturknet/adanzyedocker, ozgurozturknet/hello-app, ozgurozturknet/app1 isimli imajları çalıştığımız sisteme çekelim. 

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker image ls
                                                                                  i Info →   U  In Use
IMAGE           ID             DISK USAGE   CONTENT SIZE   EXTRA
alpine:latest   28bd5fe8b56d         13MB         3.93MB
centos:7        be65f488b776        301MB         76.1MB
nginx:latest    ec4ed8b5299e        241MB           66MB
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker pull httpd:alpine
alpine: Pulling from library/httpd
ec6419fed67b: Pull complete
71af8d887193: Pull complete
e5ad846ecbb8: Pull complete
f0c9ed0cf49e: Pull complete
4f4fb700ef54: Pull complete
5e8b95221646: Pull complete
d54f80382ece: Download complete
b4e124edb500: Download complete
Digest: sha256:1b766f17b84026429b7cb243317b142921b24432336e798bc881c43f45ed9567
Status: Downloaded newer image for httpd:alpine
docker.io/library/httpd:alpine
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker pull ozgurozturknet/adanzyedocker
Using default tag: latest
latest: Pulling from ozgurozturknet/adanzyedocker
1c5aa5048b34: Pull complete
9d48c3bd43c5: Pull complete
1587ec6e5583: Pull complete
d3565940ff69: Pull complete
e7daf8feccda: Pull complete
84d0ceb32a5d: Pull complete
1cc6c921162a: Pull complete
17877ce0de23: Pull complete
4e10ed3cf6fc: Pull complete
49641b0d4586: Pull complete
Digest: sha256:10631a62b96b8dc8c468fe482aff70871c6c81f4a49ea4c5350ce765cf9f2185
Status: Downloaded newer image for ozgurozturknet/adanzyedocker:latest
docker.io/ozgurozturknet/adanzyedocker:latest
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker pull ozgurozturknet/hello-app
Using default tag: latest
latest: Pulling from ozgurozturknet/hello-app
e7f2aa010900: Pull complete
aad63a933944: Pull complete
Digest: sha256:a4b3acfb88eafb47a7b5f1266f25ff114d3148186d130dad5d4319086b26c4c2
Status: Downloaded newer image for ozgurozturknet/hello-app:latest
docker.io/ozgurozturknet/hello-app:latest
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker pull ozgurozturknet/app1
Using default tag: latest
latest: Pulling from ozgurozturknet/app1
3bd64be52cfe: Pull complete
1e929b64ace7: Pull complete
169185f82c45: Pull complete
d5d6362eff06: Pull complete
Digest: sha256:31acbf06b10306dc403bb57ecd2be4e870d9ecacacbff006a56c1f5e40f762d6
Status: Downloaded newer image for ozgurozturknet/app1:latest
docker.io/ozgurozturknet/app1:latest


<-

->image isimlerini değiştirip eskilerini silme işlemi:

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker image ls
                                                                                  i Info →   U  In Use
IMAGE                                 ID             DISK USAGE   CONTENT SIZE   EXTRA
alpine:latest                         28bd5fe8b56d         13MB         3.93MB
centos:7                              be65f488b776        301MB         76.1MB
httpd:alpine                          1b766f17b840       97.3MB         21.9MB
nginx:latest                          ec4ed8b5299e        241MB           66MB
ozgurozturknet/adanzyedocker:latest   10631a62b96b        432MB          121MB
ozgurozturknet/app1:latest            31acbf06b103        182MB         48.7MB
ozgurozturknet/hello-app:latest       a4b3acfb88ea          9MB         2.81MB
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker tag ozgurozturknet/hello-app hello-app:v1
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker tag ozgurozturknet/app1 app1:v1
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker tag ozgurozturknet/adanzyedocker adanzyedocker:v1
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker image ls
                                                                                  i Info →   U  In Use
IMAGE                                 ID             DISK USAGE   CONTENT SIZE   EXTRA
adanzyedocker:v1                      10631a62b96b        432MB          121MB
alpine:latest                         28bd5fe8b56d         13MB         3.93MB
app1:v1                               31acbf06b103        182MB         48.7MB
centos:7                              be65f488b776        301MB         76.1MB
hello-app:v1                          a4b3acfb88ea          9MB         2.81MB
httpd:alpine                          1b766f17b840       97.3MB         21.9MB
nginx:latest                          ec4ed8b5299e        241MB           66MB
ozgurozturknet/adanzyedocker:latest   10631a62b96b        432MB          121MB
ozgurozturknet/app1:latest            31acbf06b103        182MB         48.7MB
ozgurozturknet/hello-app:latest       a4b3acfb88ea          9MB         2.81MB
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker rmi ozgurozturknet/app1
Untagged: ozgurozturknet/app1:latest
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker rmi ozgurozturknet/hello-app
Untagged: ozgurozturknet/hello-app:latest
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker rmi ozgurozturknet/adanzyedocker
Untagged: ozgurozturknet/adanzyedocker:latest
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker image ls
                                                                                  i Info →   U  In Use
IMAGE              ID             DISK USAGE   CONTENT SIZE   EXTRA
adanzyedocker:v1   10631a62b96b        432MB          121MB
alpine:latest      28bd5fe8b56d         13MB         3.93MB
app1:v1            31acbf06b103        182MB         48.7MB
centos:7           be65f488b776        301MB         76.1MB
hello-app:v1       a4b3acfb88ea          9MB         2.81MB
httpd:alpine       1b766f17b840       97.3MB         21.9MB
nginx:latest       ec4ed8b5299e        241MB           66MB
utkusinaorhan@ASUS-TUF-GAMING-F15:~$

<-



3: app1 isimli imajdan bir container yaratalım.

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container create --name ilk-uygulama-app1 app1:v1
68b561ce7621394781aa2397a165dd4ba3c6e699906f5c9d16dfc5dda2f679b9

<-


4: httpd:alpine isimli imajdan detached bir container yaratalım. Yarattığımız container ismini ve id’sini görelim. 


->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container run -d --name httpdalpine-uygulamasi httpd:alpine
d215168a91898ee940edf0c272d11217327a951c181d7608d1f10e95b05ca636

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE          COMMAND              CREATED         STATUS         PORTS     NAMES
d215168a9189   httpd:alpine   "httpd-foreground"   8 seconds ago   Up 8 seconds   80/tcp    httpdalpine-uygulamasi


<-

5: Yarattığımız bu contaier’ın loglarına bakalım.

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container logs httpdalpine-uygulamasi
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Wed Jul 08 15:33:43.397935 2026] [mpm_event:notice] [pid 1:tid 1] AH00489: Apache/2.4.68 (Unix) configured -- resuming normal operations
[Wed Jul 08 15:33:43.397981 2026] [core:notice] [pid 1:tid 1] AH00094: Command line: 'httpd -D FOREGROUND'

<-


6: Container’ı durduralım, ardından yeniden çalıştıralım ve son olarak container’ı sistemden kaldıralım. 

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE          COMMAND              CREATED         STATUS         PORTS     NAMES
d215168a9189   httpd:alpine   "httpd-foreground"   2 minutes ago   Up 2 minutes   80/tcp    httpdalpine-uygulamasi
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container stop d215168
d215168
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container start d215168
d215168
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE          COMMAND              CREATED         STATUS         PORTS     NAMES
d215168a9189   httpd:alpine   "httpd-foreground"   3 minutes ago   Up 3 seconds   80/tcp    httpdalpine-uygulamasi
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container rm d215168
Error response from daemon: cannot remove container "d215168": container is running: stop the container before removing or force remove
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container rm -f d215168
d215168
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                     PORTS     NAMES
68b561ce7621   app1:v1   "java app1"   19 minutes ago   Exited (0) 5 minutes ago             ilk-uygulama-app1


<-


7: adanzyedocker isimli imajdan websunucu adında detached ve “-p 80:80” ile portu publish edilmiş bir container yaratalım. Kendi bilgisayarımızın browserından bu web sitesine erişelim.

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container run -it -d -p 80:80 --name websunucu adanzyedocker:v1

514e7f6c7bfa19f55120d8fc420093d9c987e1c6c7195e52bfd498dfa6b21a8e

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE              COMMAND              CREATED          STATUS         PORTS                                 NAMES
514e7f6c7bfa   adanzyedocker:v1   "httpd-foreground"   10 seconds ago   Up 9 seconds   0.0.0.0:80->80/tcp, [::]:80->80/tcp   websunucu

<-



8: websunucu adlı bu container’ın içerisine bağlanalım. /usr/local/apache2/htdocs klasörünün altına geçelim ve echo “denemedir” >> index.html komutuyla buradaki dosyaya denemedir yazısını ekleyelim. Web tarayıcıya geçerek dosyaya ekleme yapabildiğimizi görmek için refresh edelim. Sonrasında container içerisinden exit ile çıkalım.

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE              COMMAND              CREATED         STATUS         PORTS                                 NAMES
514e7f6c7bfa   adanzyedocker:v1   "httpd-foreground"   6 minutes ago   Up 6 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   websunucu


utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker exec -it websunucu sh

/usr/src/myapp # cd /usr/local/apache2/htdocs
/usr/local/apache2/htdocs # echo "denemedir utku" >> index.html
/usr/local/apache2/htdocs # exit

<-


9: websunucu isimli container’ı çalışırken silelim.

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container rm -f 514e
514e

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                      PORTS     NAMES
68b561ce7621   app1:v1   "java app1"   31 minutes ago   Exited (0) 18 minutes ago             ilk-uygulama-app1

<-


10: alpine isimli imajdan bir container yaratalım. Ama varsayılan olarak çalışması gereken uygulama yerine “ls” uygulamasının çalışmasını sağlayalım.

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container run --name alpine-ls alpine:latest ls
bin
dev
etc
home
lib
media
mnt
opt
proc
root
run
sbin
srv
sys
tmp
usr
var

<-

11: “alistirma1” isimli bir volüme yaratalım. 

->
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker volume create arastirma1

arastirma1
<-

12: alpine isimli imajdan “birinci” isimli bir container yaratalım. Bu container’ı interactive modda yaratalım ve bağlanabilelim. Aynı zamanda “alistirma1” isimli volume’u bu containerın “/test” isimli folder’ına mount edelim. Bu folder içerisine geçelim ve “touch abc.txt” komutuyla bir dosya yaratalım daha sonra “echo deneme >> abc.txt” komutuyla bu dosyanın içerisine yazı ekleyelim. 

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container run -it --name birinci -v arastirma1:/test alpine:latest
/ # pwd
/
/ # ls
bin    etc    lib    mnt    proc   run    srv    test   usr
dev    home   media  opt    root   sbin   sys    tmp    var
/ # cd test
/test # touch abc.txt
/test # ls
abc.txt
/test # echo "deneme" >> abc.txt
/test # cat abc.txt
deneme

<-

13: alpine isimli imajdan “ikinci” isimli bir container yaratalım. Bu container’ı interactive modda yaratalım ve bağlanabilelim. Aynı zamanda “alistirma1” isimli volume’u bu containerın “/test” isimli folder’ına mount edelim. Bu folder içerisinde “ls” komutyla dosyaları listeleyelim ve abc.txt dosyası olduğunu görelim. “cat abc.txt” ile dosyanın içeriğini kontrol edelim. 

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container run -it --name ikinci -v arastirma1:/test alpine
:latest
/ # cd test
/test # ls
abc.txt
/test # cat abc.txt
deneme

<-


14: alpine isimli imajdan “ucuncu” isimli bir container yaratalım. Bu container’ı interactive modda yaratalım ve bağlanabilelim. Aynı zamanda “alistirma1” isimli volume’u bu containerın “/test” isimli folder’ına mount edelim fakat Read Only olarak mount edelim. Bu folder içerisine geçelim ve “touch abc1.txt” komutuyla bir dosya yaratmaya çalışalım. Ve yaratamadığımızı görelim.

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container run -it --name ucuncu -v arastirma1:/test:ro alpine:latest
/ # cd test
/test # touch abc1.txt
touch: abc1.txt: Read-only file system

<-


15: Bilgisayarımızda bir klasör yaratalım “örneğin c:\deneme” ve bu klasörün içerisinde index.html adlı bir dosya yaratıp bu dosyanın içerisine birkaç yazı ekleyelim.

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ mkdir deneme
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ cd deneme
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ touch index.html
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ echo "selam docker ben utku" >> index.html
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ cat index.html
selam docker ben utku

<-


16: adanzyedocker isimli imajdan websunucu1 adında detached ve “-p 80:80” ile portu publish edilmiş bir container yaratalım. Bilgisayarımızda yarattığımız klasörü container’ın içerisindeki /usr/local/apache2/htdocs klasörüne mount edelim. Web browser açarak 127.0.0.1’e gidelim ve sitemizi görelim. Daha sonra bilgisayarımızda yarattığımız klasörün içerisindeki index.html dosyasını edit edelim ve yeni yazılar ekleyelim. Web sayfasını refresh ederek bunların geldiğini görelim.

->

utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ docker container run -d -p 80:80 --name websunucu1 -v $(pwd):/usr/local/apache2/htdocs adanzyedocker:v1
8e1612db956c44555a114b60ff07f43277c9857a6eef8af2129b8e3343309649
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ docker container exec -it websunucu1 sh
/usr/src/myapp # cd ..
/usr/src # ls
myapp
/usr/src # cd ..
/usr # ls
bin      include  lib      libexec  local    sbin     share    src
/usr # cd local/
/usr/local # ls
apache2  bin      lib      share
/usr/local # cd
apache2/  bin/      lib/      share/
/usr/local # cd apache2/
/usr/local/apache2 # cd htdocs/
/usr/local/apache2/htdocs # ls
index.html
/usr/local/apache2/htdocs # cat index.html
<h1>Merhaba Docker! Ilk Sürüm</h1><p>Bu yazi container restart edilmeden eklendi!</p>
/usr/local/apache2/htdocs # exit
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ ls
index.html
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ cat
^C
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ cat index.html
<h1>Merhaba Docker! Ilk Sürüm</h1><p>Bu yazi container restart edilmeden eklendi!</p>
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ nano index.html
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ cat index.html
<h1>Merhaba Docker! Ilk Sürüm</h1><p>Bu yazi container restart edilmeden eklendi!</p>
<h2>restart yaptım ve bu çıktı</h2>
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ nano index.html
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ cat index.html
<h1>Merhaba Docker! Ilk Surum</h1><p>Bu yazi container restart edilmeden eklendi!</p>
<h2>restart yaptim ve bu çikti</h2>
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ nano index.html
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ cat index.html
<h1>Merhaba Docker! Ilk Surum</h1><p>Bu yazi container restart edilmeden eklendi!</p>
<h2>restart yaptim ve bu cikti</h2>
utkusinaorhan@ASUS-TUF-GAMING-F15:~/deneme$ docker ps
CONTAINER ID   IMAGE              COMMAND              CREATED         STATUS         PORTS                                 NAMES
8e1612db956c   adanzyedocker:v1   "httpd-foreground"   6 minutes ago   Up 6 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   websunucu1


<-


17: Tüm çalışan container’ları silelim. 


->

utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE              COMMAND              CREATED         STATUS         PORTS                                 NAMES
8e1612db956c   adanzyedocker:v1   "httpd-foreground"   8 minutes ago   Up 8 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   websunucu1
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container rm -f 8e1612
8e1612
utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

<-
