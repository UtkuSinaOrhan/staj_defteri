ilk olarak docker volume nedir ne işe yarar bunu öğrendim 

docker volume

		-volume, container ve image gibi bir docker objesidir.
		-image veya container yaratır gibi yaratılırlar.
		-docker deamon'ın kurulu olduğu host makine üzerinde kurulurlar. Ama istenirse çeşitli volume driverlarına cloude gibi driverlara kurulabilirler.
		-container içinde yazılmış gibi görünürler bu sebeple de herhangi bir sorun yaratmaz
		-bir volume birden fazla containera bağlanabilir.


		SYNTAX: 

				docker volume create [VOLUME_NAME]
				
				docker volume inspect [VOLUME_NAME] "volume detaylarını gösterir."
					
					-> inspect satırından sonra alınan cevaptaki Mountpoint satırı volume içine kaydedilen dataların direkt olarak bulunduğu klasörü gösterir.

				docker container run -it -v ilkvolume:/uygulama alpine sh
					
					-> -it ile bağlantı açılıyor. -v ile volume bağlanıyor. container içindeki uygulama isimli klasöre bağlanan ilkvolume isimli volume ve alpine imajı ile bir conteiner yarat ve shell aç.

					-> volume'ün bağlanacağı klasörün container içinde olması gerekmez. varsa problem olmaz ama eğer yoksa da kendi container oluşturulurken oluşturulur.  


				docker volume ls
					
					-> bu kod satırı ile aktif olan volume varsa listelenir.

				docker container run -it -v ilkvolume:/deneme3:ro centos sh
					
					-> volume bu containera read-only olarak bağlanıyor. centos image ile oluşturulur ve açılan shellde : 
						-> touch test.txt "test.txt dosyası oluşturma kodu." çıktı olarak:
							-> touch: cannot touch 'test.txt': Read-only file system



sonrasında bind mount işlemi için udemy ve yapay zeka kullanarak container ile host arasında aşağıdaki  kodlar yardımı ile dosya paylaşmak için kullandım. bu dosyalar ile localde yapılan değişiklikler containerda da güncel olarak değişiyor.

Kodlar:
    utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker -v
    Docker version 29.6.1, build 8900f1d
    
    utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker container run -d -p 80:80 -v /mnt/c/Users/UtkuSinaOrhan/Desktop/AdanZyeDocker-master/kisim3/bolum28/websitesi:/usr/share/nginx/html nginx 
    dc5e96f41fe2651223458bf01f1d4e7f03c01fb0af4bad02788fc04ef769ca83
    
    utkusinaorhan@ASUS-TUF-GAMING-F15:~$ docker rm -f dc5  "bu kısım containerı siliyor."
    dc5




bunları çalıştıktan sonra alıştırma.md dosyasındaki konu tekrarı çalışmasını yaptım. 
kodlarda zorlandığım ve hatırlamadığım exec gibi komutlara geminiden baktım. 
syntaxı oturtmak için önemli bir egzersiz oldu