## WINDOWS TEMEL KOMUTLAR

##### Yerel kullanıcı ekleme
      net user (kullanıcı adı) (parola) /add  
#### Domain kullanıcısı ekleme
      net user (kullanıcı adı) (parola) /DOMAIN
      net user (kullanıcı adı) (parola) /DOMAIN
Kullanıcı silme
      net user (kullanıcı adı) /del
Domain grubuna Admin yetkili kullanıcı ekleme
      net group “domain admins” (kullanıcı adı) /add /DOMAIN
Kullanıcı ayrıntılarını görme
      net user (kullanıcı adı)
Kullanıcıları görme
      wmic useraccount get sid, name  //sadece admin kullanıcısını görmek için komutun sonuna “ | findstr /L 500” yaz	
İp adresini öğrenme
      curl icanhazip.com
Gateway adresini öğrenme
      netstat -rn
İşletim sistemi versiyonunu gösterme
      ver
Kullanıcının yetkilerini görme
      whoami /priv
Görev zamanlayıcı oluşturma
      SCHTASKS /Create /SC WEEKLY /D MON /TN cmd /TR c:\windows\system32\cmd.exe  // Haftanın Pazartesi günleri cmd.exe komutunu çalıştır.
Powershell Üzerinden Log İnceleme
      Get-EventLog -LogName System -Index <Index_no> 
