## LINUX TEMEL KOMUTLAR

| Komut  			    | Açıklama                                                       	|
|-----------------------------------|-------------------------------------------------------------------|
| cp     			    | Kopyalama                                                      	|
| rm     			    | Dosya silme                                                    	|
| rm -rf 			    | Klasör silme                                                   	|
| cp -rf 			    | Klasör kopyalama                                               	|
| grep   			    | İçeriği filtreleyerek getirme                                  	|
| ls -a 			    | Gizli klasörleri görme                                         	|
| ls -al 			    | Gizli klasörleri listeli görme                                 	|
| ls -ln 			    | İzinleri görme                                                 	|
| ln -s  			    | “ln -s /root/dosya_adı  /root/yeni_yolu”  -> Kısayol oluşturma 	|
| tracert, pathping                 | Hop atlama                                                        |
| history                           | Önceden girilen komutları getirir.                                |
| cat                               | Metin belgesi içindekileri okuma                                  |
| man                               | “man program_adı” -> Bir programın nasıl kullanıldığını gösterir. |
| ps                                | Çalışan prosesler                                                 |
| kill                              | kill -9 PID  -> Çalışan 9 numaralı prosesi sonlandırır.           |
| htop                              | İşlemci tüketimini gösterir.                                      |
| more                              | Terminal ekranına belirli miktarda çıktı gösterir.                |
| uniq                              | Aynı olan kelimeleri teke düşürür.                                |
| sort                              | Harf sıralamasına göre düzenler                                   |
| sort -n			    | dosya içeriğini sıraya göre getirir				|
| halt                              | Ekranı kilitler, geri dönüşü olmaz                                |
| tail -f log_dosyası               | Dosyanın sonunu getirir ve günceller.                             |
| locate                            | Aranan dosyanın yolunu bulma.  updatedb ile güncellemen gerekir.  |
| Gzip                              | dosya sıkıştırır                                                  |
| gunzip                            | sıkıştırılmış klasörü çıkarır                                     |
|                                   |                                                                   |
|                                   |                                                                   |
|                                   |                                                                   |
|                                   |                                                                   |
|                                   |                                                                   |







find		=	Aranan dizin ya da dosya bulma 
find  /etc -type f -name “*.py” -perm -u+x -mtime -5 | xargs ls -ls
find . 		= Bulunduğu dizin altını arar.
name 		= Tırnak içine aranacak dosya yazılır.
type 		= Dosya tipi. f dosya , d dizin
perm 		= İzin Yetkileri. Örnekte kullanıcının çalıştırılabilir dosya yetkileri
mtime 		= Gün cinsinden değer. Örnekte son 5 gün
atime 		= Dakika cinsinden değer.
size 		= veri boyutuna göre bulma  -size -10M (10megabayt tan küçük olanlar)
find . | wc -l  	= Kaç satır bulduğunu gösterir.


grep / awk
ifconfig | grep -i “ether” | awk ‘{print $2}’	->	mac adresini ekrana bastırdık
i = ignore . Büyük küçük harfe duyarlı olma.
v = Belirtilen kelimenin geçtiği satırları getirme
c = Kelimeden kaç tane geçtiğini gösterir.


fdisk, df	=	Disk durumunu görme
fdisk -l		=	Disk bölümlerini görme
free		=	Ram durumunu görme
top, vmstat	=	Cpu durumunu görme
id		=	Yetkileri görme
getprivs	=	Meterpreter ekranında yetkileri görme
whoami	=	Hangi kullanıcı olduğumuzu görme
uname -a	=	İşletim sistemi	, versiyon, kernel bilgisi alma
lsb_release -a =	Dağıtım adını öğrenme
lshw		=	Donanım hakkında bilgi alma
dmidecode --type [bios]  =  Sistem hakkında bilgi alma


Linux ip verme 		=	ifconfig eth0 10.0.0.10
İp adresini öğrenme		=	curl icanhazip.com, curl ifconfig.me
Gateway, mask verme	=	route add default gw 10.0.0.1 netmask 255.0.0.0 eth0
Gateway adresini öğrenme	=	netstat -rn , route -n
Portu kullanan servisler	=	lsof -i :80  (80 portunu kullanan processleri getirir.
Ağ servisini yeniden başlatma	=	systemctl restart NetworkManager.services
Web server açma			=	service apache2 start    var/www/html dizini
Arp tablosunu görme			=	arp ,  arp -a
Dns ip öğrenme			=	cat /etc/resolv.conf
Dns ip değiştirme			=	nano /etc/dhcp/dhclient.conf
						#prepend domain-name-servers 127.0.0.1;	 ->								#işaretini kaldır,   127.0.0.1 yerine yeni dns leri gir.
Kullanıcı ekleme		=	adduser, useradd
Kullanıcı silme			=	deluser, userdel
Parola oluşturma		=	passwd kullanıcı_adı
Yetkilendirme			=	chmod +777 dosya_adı
Kullanıcıları görme		=	cat /etc/passwd
Parolaları görme		=	cat /etc/shadow	cat /etc/shadow | grep “root:”
En yüksek yetkili kullanıcıyı görme	=	cat /etc/passwd | grep “x:0”
Parola özetini görme	=	cat /etc/shadow | grep “root:” | cut -d “$” -f4 | cut -d “:” -f1
Silinmiş kullanıcıları görme	= cat /var/log/secure | grep userdel
***   /var/log/secure => Oluşturulmuş ve silinmiş kullanıcıların loglarını tutar.
Sistemin şifreleme algoritmasını bulma	=	authconfig --test | grep hashing
En son ssh bağlantısı yapılan yeri görme	= home/kullanıcı ad/.ssh/known_hosts dosyasında yazar.
Ssh hatası verirse		=       ssh -oHdstKeyAlgorithms=+ssh-dss root@192.168.1.24
apt update			=	Paketlerin yüklendiği veri tabanını günceller
apt upgrade			=	Sistemdeki tüm programları günceller
apt install paket_adı 	 	=	Program yükleme
apt remove paket_adı		=	Program silme
Patch Yolu Gösterme		=	export PATH=$PATH:/dosya/dosya
sudo -l				=	sudo yetkilerini görme (sudoers.d dosyasını okur)
cat /etc/crontab		=	Zamanlanmış görevleri göster.
Klavye dilini kalıcı değiştirme =      nano /etc/default/keyboard -> XKBLAYOUT="tr"
