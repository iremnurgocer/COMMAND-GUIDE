Windows, macOS ve Linux İçin Kapsamlı Komut Rehberi



**1. BÖLÜM – TEMEL KOMUTLAR ve GEZİNME**

Bu bölümde terminalde dosya sisteminde gezinme, dosya oluşturma, listeleme, silme gibi **en sık kullanılan temel komutlar** bulunur.\
Her komutun hemen yanında kısa açıklaması, parametreleri ve farklı platformlardaki karşılıkları yer alır.

-----
**1.1. Dizin (Klasör) Gezinme Komutları**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Mevcut dizini göster|cd|Get-Location|pwd|Şu anda bulunduğun klasörü gösterir.|
|Dizin değiştir|cd dizin\_adı|Set-Location dizin\_adı|cd dizin\_adı|Belirtilen klasöre geçiş yapar.|
|Üst dizine çık|cd ..|Set-Location ..|cd ..|Bir üst klasöre döner.|
|Ekranı temizle|cls|Clear-Host|clear|Terminal ekranını temizler.|
|Dizin içeriğini listele|dir|Get-ChildItem|ls|Bulunduğun klasördeki dosya ve klasörleri gösterir.|

**🔹 Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|ls -l|Uzun liste (boyut, izin, tarih gösterir)|ls -l|
|ls -a|Gizli dosyaları da gösterir|ls -a|
|ls -la|Uzun + gizli dosyalar dahil|ls -la|
|dir /a|Windows’ta gizli dosyaları gösterir|dir /a|

-----
**1.2. Klasör (Dizin) Oluşturma, Taşıma, Silme**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Klasör oluştur|mkdir yeni\_klasor|New-Item -ItemType Directory yeni\_klasor|mkdir yeni\_klasor|Yeni klasör oluşturur.|
|Alt klasörlerle birlikte oluştur|—|—|mkdir -p /path/yeni/klasor|Gerekli üst dizinleri de otomatik oluşturur.|
|Klasör taşımak|move kaynak hedef|Move-Item kaynak hedef|mv kaynak hedef|Klasörü veya dosyayı başka yere taşır.|
|Boş klasör silmek|rmdir klasor|Remove-Item -Recurse klasor|rmdir klasor|Sadece boş klasörleri siler.|
|Dolu klasör silmek|rmdir /s /q klasor|Remove-Item -Recurse -Force klasor|rm -rf klasor|Tüm içeriğiyle birlikte siler. ⚠️ Dikkatli kullan!|

**🔹 Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-r veya /s|Alt dizinleri de dahil et (recursive)|rm -r klasor|
|-f veya /q|Onay sormadan sil (force/quiet)|rm -rf klasor|
|-p|Gereken üst dizinleri de oluştur|mkdir -p dizin/yeni|

-----
**1.3. Dosya Oluşturma, Yeniden Adlandırma, Silme**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Yeni dosya oluştur|type nul > dosya.txt|New-Item dosya.txt|touch dosya.txt|Boş dosya oluşturur.|
|Dosya silmek|del dosya.txt|Remove-Item dosya.txt|rm dosya.txt|Dosyayı siler.|
|Onay sormadan sil|del /q dosya.txt|Remove-Item -Force dosya.txt|rm -f dosya.txt|Silme işlemini onaysız yapar.|
|Dosyayı taşımak|move a.txt D:\hedef|Move-Item a.txt D:\hedef|mv a.txt ~/hedef/|Dosyayı taşır.|
|Dosyayı yeniden adlandırmak|rename eski.txt yeni.txt|Rename-Item|mv eski.txt yeni.txt|Dosyanın adını değiştirir.|

-----
**1.4. Dosya İçeriğini Görüntüleme**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Dosya içeriğini göster|type dosya.txt|Get-Content dosya.txt|cat dosya.txt|Dosyanın içeriğini ekrana basar.|
|İlk satırları göster|—|—|head -n 10 dosya.txt|İlk 10 satırı gösterir.|
|Son satırları göster|—|—|tail -n 10 dosya.txt|Son 10 satırı gösterir.|
|Sayfa sayfa görüntüle|—|—|less dosya.txt|Uzun dosyaları kaydırarak okumanı sağlar (q → çıkış).|
|Ekrana metin yazdırmak|echo Merhaba|Write-Output "Merhaba"|echo "Merhaba"|Basit çıktı verir.|

-----
**1.5. Dosya Arama ve İçerik Tarama**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Dosya adıyla arama|dir /s \*.txt|Get-ChildItem -Recurse -Filter \*.txt|find . -name "\*.txt"|Dizin içinde belirli dosya uzantısını arar.|
|İçerikte kelime arama|find "metin" dosya.txt|Select-String "metin" dosya.txt|grep "metin" dosya.txt|Dosya içeriğinde geçen kelimeleri arar.|
|Büyük/küçük harf duyarsız arama|—|—|grep -i "metin" dosya.txt|Harf duyarsız arama yapar.|
|Satır numarasıyla arama|—|—|grep -n "metin" dosya.txt|Eşleşen satır numaralarını gösterir.|
|Tüm dizinlerde arama|—|—|grep -r "metin" .|Alt dizinler dahil arar.|

-----
**1.6. Yardım, Bilgi ve Çıkış**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Yardım görmek|komut /?|Get-Help komut|komut --help|Komutun açıklamasını ve parametrelerini gösterir.|
|Manuel sayfasını açmak|—|—|man komut|Komutun ayrıntılı dokümantasyonunu gösterir.|
|Terminali kapatmak|exit|exit|exit|Terminal oturumunu kapatır.|

-----
**1.7. Faydalı Kombinasyonlar (Sık Kullanılan Örnekler)**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Gizli dosyalar dahil detaylı liste|ls -la|Uzun formatta gizli dosyaları gösterir.|
|Dosyayı hızlı oluştur ve içeriğini yaz|echo "Merhaba" > deneme.txt|Dosyayı oluşturur ve içine “Merhaba” yazar.|
|Dosyanın son satırlarını canlı izlemek|tail -f log.txt|Log takibi için kullanılır.|
|Tüm .txt dosyalarını sil|rm -f \*.txt|Uzantıya göre toplu silme.|
|Klasörü ve alt klasörleri gizli dahil kopyala|cp -rav kaynak hedef|Kopyalama işlemini ayrıntılı gösterir.|

-----
**1.8. Parametre Mantığı (Kısaltmaların Anlamı)**

|**Parametre**|**Açılım**|**Açıklama**|
| :- | :- | :- |
|-r / /s|recursive|Alt dizinleri dahil et|
|-f / /q|force / quiet|Onay sormadan işlemi yap|
|-a|all|Gizli dosyalar dahil|
|-l|long|Detaylı listeleme|
|-v|verbose|İşlem detaylarını göster|
|-p|parents|Gerekli dizinleri de oluştur|
|-i|interactive|Her işlem öncesi sor|
|--help|help|Komut yardımı göster|

-----
**Bölüm Özeti**

Bu bölümde terminalde hareket etmeyi, dosya ve klasörlerle işlem yapmayı, dosya içeriğini görüntülemeyi ve temel arama komutlarını öğrendin.\
Tüm işlemler için parametrelerin (-r, -f, -a gibi) temel mantığını da kavradın.

**2. BÖLÜM – DOSYA YÖNETİMİ, KOPYALAMA, TAŞIMA ve ARŞİVLEME**

Bu bölümde; dosya ve klasörleri kopyalama, taşıma, yeniden adlandırma, arşivleme (sıkıştırma/açma) işlemleri için kullanılan temel terminal komutları yer alır.\
Her komutun altında kısa açıklaması, parametreleri ve farklı platformlardaki karşılıkları bulunur.

-----
**2.1. Dosya ve Klasör Kopyalama**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Dosya kopyala|copy kaynak hedef|Copy-Item kaynak hedef|cp kaynak hedef|Belirtilen dosyayı başka dizine kopyalar.|
|Klasör kopyala (alt dizinlerle)|xcopy kaynak hedef /s /e|Copy-Item kaynak -Destination hedef -Recurse|cp -r kaynak hedef|Alt klasörleri dahil kopyalar.|
|Kopyalama işlemini doğrula|xcopy /v|Copy-Item -Verbose|cp -v|Kopyalanan dosyaları ekranda gösterir.|
|İzinleri / tarihleri koruyarak kopyala|—|—|cp -p|Dosya özelliklerini korur.|
|Mevcut dosyayı sormadan üzerine yaz|/y|-Force|-f|Mevcut hedef dosyayı uyarısız değiştirir.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-r / /s|Alt dizinleri dahil et|cp -r kaynak hedef|
|-v|Ayrıntılı çıktı|cp -rv kaynak hedef|
|-p|İzin ve tarihleri koru|cp -p dosya hedef|
|-f / /y|Üzerine yaz (onay sormadan)|cp -f dosya hedef|

-----
**2.2. Dosya ve Klasör Taşıma**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Dosya taşı|move kaynak hedef|Move-Item kaynak hedef|mv kaynak hedef|Dosyayı yeni konuma taşır.|
|Klasör taşı|move klasor hedef|Move-Item klasor hedef|mv klasor hedef|Tüm klasörü taşır.|
|Yeniden adlandırma|rename eski.txt yeni.txt|Rename-Item|mv eski.txt yeni.txt|Dosya veya klasör adını değiştirir.|

**🔹 Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-v|Ayrıntılı çıktı (Linux/macOS)|mv -v kaynak hedef|
|-f|Üzerine yaz (onaysız)|mv -f dosya hedef|

-----
**2.3. Dosya Arşivleme (Sıkıştırma)**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|ZIP arşivi oluştur|Compress-Archive kaynak.zip *(PowerShell)*|Compress-Archive -Path kaynak -DestinationPath hedef.zip|zip -r hedef.zip klasor|Belirtilen dosya veya klasörü .zip olarak arşivler.|
|ZIP arşivini aç|tar -xf dosya.zip *(PowerShell destekli)*|Expand-Archive -Path dosya.zip -DestinationPath hedef/|unzip dosya.zip|Sıkıştırılmış dosyayı çıkarır.|
|TAR arşivi oluştur|—|—|tar -cvf arsiv.tar klasor|.tar uzantılı arşiv oluşturur.|
|TAR arşivini aç|—|—|tar -xvf arsiv.tar|.tar arşivini açar.|
|GZ sıkıştırması (tek dosya)|—|—|gzip dosya.txt|Dosyayı .gz formatında sıkıştırır.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-r|Alt dizinleri dahil et|zip -r arsiv.zip klasor|
|-v|Ayrıntılı çıktı|tar -cvf arsiv.tar klasor|
|-x|Arşivi çıkar|tar -xvf arsiv.tar|
|-c|Arşiv oluştur|tar -cvf arsiv.tar klasor|
|-f|Dosya adı belirtir|tar -cvf arsiv.tar|
|-z|gzip sıkıştırma uygula|tar -czvf arsiv.tar.gz klasor|

-----
**2.4. Dosya Senkronizasyonu (Kopyalama + Güncelleme)**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Dosya senkronizasyonu|robocopy kaynak hedef /MIR|robocopy (PowerShell’de de çalışır)|rsync -av kaynak/ hedef/|Klasörleri aynalayarak kopyalar, yalnız değişiklikleri günceller.|
|Kopyalama ilerlemesini göster|/v|-Verbose|rsync -av --progress|İlerleme durumu ekrana yazılır.|
|Silinenleri de yansıt|/MIR|—|--delete|Kaynaktan silinen dosyaları hedefte de siler.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|/MIR|Ayna kopya (mirror) oluşturur|robocopy kaynak hedef /MIR|
|-a|Arşiv modu (izinleri korur)|rsync -a kaynak hedef|
|--delete|Hedefte olmayan dosyaları siler|rsync -av --delete kaynak hedef|
|--progress|Kopyalama ilerlemesini göster|rsync -av --progress kaynak hedef|

-----
**2.5. Geçici Dosyalar, Loglar, Yedekler**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Tüm .tmp dosyalarını sil|del /s /q \*.tmp|Remove-Item \*.tmp -Recurse -Force|find . -name "\*.tmp" -delete|Tüm geçici dosyaları siler.|
|Eski log dosyalarını temizle|—|—|find /var/log -type f -mtime +7 -delete|7 günden eski log dosyalarını siler.|
|Dosya boyutunu kontrol et|—|—|du -h dosya.txt|Dosya veya klasörün boyutunu gösterir.|
|Klasör boyutlarını listele|—|—|du -sh \*|Her alt klasörün toplam boyutunu verir.|

-----
**2.6. Parametre Mantığı (Kısaltmaların Anlamı)**

|**Parametre**|**Açılım**|**Açıklama**|
| :- | :- | :- |
|-r, /s|recursive|Alt dizinleri dahil et|
|-f, /y, /q|force / yes / quiet|Onay sormadan işlemi yap|
|-v|verbose|Ayrıntılı işlem detaylarını göster|
|-p|preserve|Dosya izinlerini veya tarihleri korur|
|-a|archive|Arşiv modu (rsync / cp için)|
|--delete|delete|Hedefte olmayan dosyaları sil|
|-z|zip/gzip|Sıkıştırma uygula|
|--progress|progress|İlerleme durumunu ekrana yazdırır|

-----
**2.7. Kullanışlı Komut Kombinasyonları**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Bir klasörü gizli dosyalarla birlikte kopyala|cp -rav kaynak hedef|Alt dizinleri dahil, ayrıntılı çıktı ile kopyalar.|
|Dosyaları hızlıca senkronize et|rsync -av --delete kaynak hedef|Kaynak ve hedefi aynalar.|
|Arşiv oluştur ve sıkıştır|tar -czvf yedek.tar.gz klasor|.tar.gz formatında sıkıştırılmış arşiv oluşturur.|
|ZIP dosyasını aç|unzip dosya.zip -d hedef/|Arşiv içeriğini hedef dizine çıkarır.|
|Büyük klasör boyutlarını öğren|du -sh \*|Her alt klasörün toplam boyutunu listeler.|

-----
**Bölüm Özeti**

Bu bölümde terminalde dosyaları ve klasörleri **kopyalama, taşıma, arşivleme, yedekleme ve senkronize etme** işlemlerinde kullanılan tüm temel komutları öğrendin.\
Ayrıca -r, -f, -v, -p, --delete gibi parametrelerin davranışı artık sana tanıdık gelmeli.

**3. BÖLÜM – DOSYA İZİNLERİ, SAHİPLİK ve ERİŞİM YÖNETİMİ**

Bu bölüm, kullanıcı izinlerini yönetmek, dosyaların kim tarafından okunabileceğini veya değiştirilebileceğini belirlemek için kullanılan terminal komutlarını kapsar.\
Windows, macOS ve Linux’ta yetki sistemi farklı olsa da temel mantık aynıdır: **okuma (read), yazma (write), çalıştırma (execute)** izinleri.

-----
**3.1. Kullanıcı ve Grup Kavramı**

|**Kavram**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|**User (kullanıcı)**|Sistemde oturum açan kişi|whoami → geçerli kullanıcı|
|**Group (grup)**|Kullanıcıların toplandığı erişim grubu|groups → ait olunan gruplar|
|**Owner (sahip)**|Dosyayı oluşturan kişi|ls -l çıktısında ilk sütun|

-----
**3.2. İzinleri Görüntüleme**

|**Platform**|**Komut**|**Açıklama**|**Örnek**|
| :- | :- | :- | :- |
|macOS / Linux|ls -l|Dosya izinlerini, sahiplikleri ve boyutları listeler|ls -l|
|macOS / Linux|stat dosya.txt|Dosya hakkında detaylı bilgi (boyut, izin, tarih)|stat dosya.txt|
|Windows CMD|icacls dosya.txt|Dosya izinlerini listeler|icacls dosya.txt|
|PowerShell|Get-Acl dosya.txt|ACL (Access Control List) detaylarını gösterir|Get-Acl .\dosya.txt|

**İzin biçimi örneği (Linux/macOS):**

-rwxr-xr--

| | | |

| | | └── Diğer kullanıcıların izinleri (r-- = sadece okuma)

| | └──── Grup izinleri (r-x = okuma + çalıştırma)

| └────── Sahip izinleri (rwx = okuma + yazma + çalıştırma)

└──────── Dosya tipi (- = dosya, d = klasör)

-----
**3.3. Dosya İzinlerini Değiştirme (chmod)**

|**Platform**|**Komut**|**Açıklama**|**Örnek**|
| :- | :- | :- | :- |
|macOS / Linux|chmod izin dosya|Dosya veya klasör izinlerini değiştirir|chmod 755 script.sh|
|Windows CMD|icacls dosya /grant kullanıcı:F|Kullanıcıya tam yetki verir|icacls deneme.txt /grant user:F|
|PowerShell|Set-Acl dosya (Get-Acl kaynak)|ACL tabanlı izin atar|—|

**Sayısal İzin Sistemi (Linux/macOS)**

|**Rakam**|**Anlamı**|**Açıklama**|
| :- | :- | :- |
|7|rwx|okuma + yazma + çalıştırma|
|6|rw-|okuma + yazma|
|5|r-x|okuma + çalıştırma|
|4|r--|sadece okuma|
|0|---|hiçbir izin yok|

**Örnekler:**

|**Komut**|**Anlamı**|
| :- | :- |
|chmod 755 script.sh|Sahip = tam yetki, grup = okuma/çalıştırma, diğer = okuma/çalıştırma|
|chmod 644 dosya.txt|Sahip = okuma/yazma, diğerleri = sadece okuma|
|chmod 700 gizli/|Sadece sahibi erişebilir (özel dizin)|

-----
**3.4. Sahiplik (chown) ve Grup Atama (chgrp)**

|**Platform**|**Komut**|**Açıklama**|**Örnek**|
| :- | :- | :- | :- |
|macOS / Linux|chown kullanıcı dosya|Dosya sahibini değiştirir|chown ali belge.txt|
|macOS / Linux|chown kullanıcı:grup dosya|Sahip ve grubu birlikte değiştirir|chown ali:admin belge.txt|
|macOS / Linux|chgrp grup dosya|Sadece grup atar|chgrp geliştirici rapor.doc|
|Windows CMD|icacls dosya /setowner kullanıcı|Sahiplik ataması yapar|icacls proje /setowner user|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-R|Alt dizinlerle birlikte uygula (recursive)|chown -R ali klasor/|
|/T|Windows’ta alt dizinlere uygular|icacls klasor /setowner user /T|

-----
**3.5. Yalnız Okunabilir / Yürütülebilir Dosyalar**

|**Amaç**|**Linux/macOS**|**Windows**|**Açıklama**|
| :- | :- | :- | :- |
|Dosyayı sadece okunabilir yap|chmod 444 dosya.txt|attrib +R dosya.txt|Dosya değiştirilemez hale gelir.|
|Dosyayı tekrar düzenlenebilir yap|chmod 644 dosya.txt|attrib -R dosya.txt|Yazma iznini geri verir.|
|Script çalıştırma izni ekle|chmod +x script.sh|—|Script’i çalıştırılabilir hale getirir.|
|Çalıştırma izni kaldır|chmod -x script.sh|—|Script’i çalıştırılamaz hale getirir.|

-----
**3.6. Erişim Listesi (ACL) Komutları**

|**Platform**|**Komut**|**Açıklama**|**Örnek**|
| :- | :- | :- | :- |
|Linux|getfacl dosya|Dosyanın ACL izinlerini gösterir|getfacl belge.txt|
|Linux|setfacl -m u:ali:rwx dosya|Ali’ye özel izin tanımlar|setfacl -m u:ali:rwx belge.txt|
|Windows CMD|icacls dosya /grant ali:F|Ali’ye tam erişim verir|icacls belge.txt /grant ali:F|
|PowerShell|Get-Acl, Set-Acl|ACL detaylı yönetimi|Get-Acl .\belge.txt|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-m|Mevcut izinlere ekleme (modify)|setfacl -m u:ali:rwx dosya|
|-x|İzin kaldırma|setfacl -x u:ali dosya|
|/grant|Windows: kullanıcıya izin ver|icacls dosya /grant user:F|
|/remove|Windows: izni kaldır|icacls dosya /remove user|

-----
**3.7. İzin ve Sahiplik Kombinasyon Örnekleri**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Bir klasörün sahibini ve grubunu değiştir|chown -R ali:admin proje/|Alt dizinler dahil sahipliği günceller.|
|Dosyayı yalnız sahibin erişebileceği hale getir|chmod 700 gizli.txt|Sadece sahip okur/yazar/çalıştırır.|
|Kullanıcıya ek izin ver|setfacl -m u:veli:rw dosya.txt|Veli okuma/yazma izni kazanır.|
|Windows’ta tüm izinleri kaldır|icacls dosya.txt /remove user|Kullanıcı erişimi kaldırılır.|
|Script’i çalıştırılabilir yap|chmod +x script.sh|Terminal üzerinden doğrudan çalıştırılabilir.|

-----
**3.8. Parametre ve Kısaltma Tablosu**

|**Parametre**|**Açıklama**|
| :- | :- |
|-R|Recursive – Alt dizinleri dahil et|
|+x / -x|Çalıştırma izni ekle / kaldır|
|+r / -r|Okuma izni ekle / kaldır|
|+w / -w|Yazma izni ekle / kaldır|
|u, g, o, a|user, group, others, all (izin hedefleri)|
|/grant, /remove, /T|Windows ACL işlemleri|
|-m, -x|Linux ACL ekleme/kaldırma|

-----
**3.9. Kısa Örnek Rehberi**

|**Amaç**|**Komut**|
| :- | :- |
|İzinleri görmek|ls -l|
|Sahipliği değiştirmek|chown kullanıcı dosya|
|Grubu değiştirmek|chgrp grup dosya|
|Script’i çalıştırılabilir yapmak|chmod +x script.sh|
|Tüm izinleri sıfırlamak|chmod 000 dosya.txt|
|Kullanıcıya tam yetki vermek (Windows)|icacls dosya /grant user:F|
|ACL listelemek|getfacl dosya|
|ACL izin eklemek|setfacl -m u:ali:rwx dosya|

-----
**3.10. Bölüm Özeti**

Bu bölümde:

- Dosya ve klasörlerin **izin yapısını** (rwx) öğrendin.
- **chmod, chown, chgrp, icacls, getfacl, setfacl** gibi komutlarla izin ve sahiplik değiştirmeyi gördün.
- -R, +x, /grant, -m gibi parametrelerin hangi bağlamda kullanıldığını kavradın.

**4. BÖLÜM – SİSTEM BİLGİSİ, KAYNAK YÖNETİMİ ve PERFORMANS KOMUTLARI**

Bu bölüm, bilgisayarın donanım, sistem, ağ ve kaynak durumunu terminal üzerinden izlemek ve yönetmek için kullanılan temel komutları kapsar.\
Hem sistem yöneticileri hem de geliştiriciler için en sık kullanılan komutlar buradadır.

-----
**4.1. Genel Sistem Bilgisi Komutları**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Sistem bilgisi|systeminfo|Get-ComputerInfo|uname -a|İşletim sistemi sürümü, mimari ve sistem detaylarını gösterir.|
|Bilgisayar adı|hostname|hostname|hostname|Cihazın ağ üzerindeki adını gösterir.|
|Kullanıcı adı|echo %USERNAME%|$env:USERNAME|whoami|Oturum açmış kullanıcı adını gösterir.|
|Sistem tarihi|date /t|Get-Date|date|Tarih ve saati görüntüler.|
|Çalışma süresi|net stats srv|(get-date) - (gcim Win32\_OperatingSystem).LastBootUpTime|uptime|Sistemin açık kalma süresini gösterir.|

-----
**4.2. Disk, Bellek ve Depolama Bilgisi**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Disk alanı|wmic logicaldisk get size,freespace,caption|Get-PSDrive|df -h|Disk kullanımını insan okunabilir biçimde gösterir.|
|Bellek (RAM) durumu|systeminfo|Get-CimInstance Win32\_OperatingSystem|free -h|Toplam, kullanılan ve boş RAM miktarını gösterir.|
|Disk doluluk oranı|—|—|du -sh \*|Dizin bazlı boyut bilgisi verir.|
|En büyük dosyaları bul|—|—|`du -ah|sort -hr|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-h|Boyutları insan okunabilir (KB, MB, GB) göster|df -h|
|-a|Tüm dosyalar dahil|du -ah|
|-s|Toplam özet boyut|du -sh \*|
|sort -r|Ters sıralama|`du -ah|

-----
**4.3. Süreç (Process) Yönetimi**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Çalışan işlemleri listele|tasklist|Get-Process|ps -e|Tüm aktif süreçleri listeler.|
|Detaylı işlem listesi|tasklist /v|`Get-Process|Format-List \*`|ps aux|
|Belirli işlemi bul|`tasklist|find "notepad"`|Get-Process notepad|`ps aux|
|İşlemi sonlandır|taskkill /IM notepad.exe /F|Stop-Process -Name notepad|kill -9 PID|Çalışan süreci kapatır.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|/IM|İşlem adıyla kapat|taskkill /IM chrome.exe|
|/PID|İşlem kimliğiyle kapat|taskkill /PID 3124|
|/F|Zorla kapat|taskkill /F /IM program.exe|
|-9|Linux: işlemi zorla kapat|kill -9 2135|
|-e|Tüm süreçleri göster|ps -e|
|aux|Geniş liste formatı|ps aux|

-----
**4.4. CPU, RAM ve Sistem Performansı İzleme**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Gerçek zamanlı sistem izleme|perfmon|Get-Counter|top|CPU, RAM ve işlem kullanımını gösterir.|
|CPU kullanım yüzdesi|—|Get-Counter '\Processor(\_Total)\% Processor Time'|mpstat veya top|CPU yükünü ölçer.|
|Bellek kullanımı (detaylı)|—|Get-Counter '\Memory\Available MBytes'|vmstat|Bellek durumu ve sayfa işlemleri.|
|Disk g/ç izleme|—|—|iostat|Disk okuma/yazma hızlarını gösterir.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-o|Çıktı formatını belirtir|top -o cpu|
|-d|Disk I/O bilgilerini dahil et|iostat -d|
|-n|Güncelleme aralığı|vmstat -n 5|

-----
**4.5. Donanım ve Cihaz Bilgileri**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Tüm donanım bilgisi|wmic cpu get name / wmic bios get serialnumber|Get-CimInstance Win32\_ComputerSystem|lshw|Donanım bileşenlerini gösterir.|
|CPU detayları|wmic cpu get name, NumberOfCores|Get-CimInstance Win32\_Processor|lscpu|İşlemci çekirdek bilgilerini listeler.|
|Bellek modülleri|wmic memorychip get capacity|—|cat /proc/meminfo|Bellek kapasitesi bilgisi verir.|
|PCI cihazları|—|—|lspci|Donanım bileşenlerini listeler.|
|USB cihazları|—|—|lsusb|USB cihazlarını gösterir.|

-----
**4.6. Ağ ve IP Bilgisi**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|IP adresi bilgisi|ipconfig|Get-NetIPAddress|ifconfig veya ip a|Ağ arabirimi IP detaylarını gösterir.|
|Ağ bağlantılarını listele|netstat -ano|Get-NetTCPConnection|netstat -tulnp|Aktif bağlantıları gösterir.|
|Ping testi|ping 8.8.8.8|Test-Connection 8.8.8.8|ping 8.8.8.8|Ağ bağlantısını test eder.|
|DNS çözümleme|nslookup domain.com|Resolve-DnsName domain.com|dig domain.com|DNS çözümlemesi yapar.|
|Ağ rotasını takip et|tracert domain.com|—|traceroute domain.com|Paketlerin izlediği rotayı gösterir.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|/all|Tüm IP bilgilerini detaylı göster|ipconfig /all|
|-n|DNS çözümlemesini devre dışı bırak|ping -n 5 8.8.8.8|
|-t|Sürekli ping gönder|ping -t 8.8.8.8|
|-c|Belirli sayıda ping|ping -c 4 8.8.8.8|

-----
**4.7. Parametre ve Kısaltma Tablosu**

|**Parametre**|**Açıklama**|
| :- | :- |
|-a|Tüm bilgi (all)|
|-h|İnsan okunabilir format|
|-r|Ters sıralama|
|-v|Ayrıntılı (verbose) çıktı|
|/F, -9|İşlemi zorla sonlandır|
|/all|Tüm detaylı bilgi (Windows)|
|-t, -c|Sürekli / sınırlı sayıda ping|
|-o|Sıralama ölçütü (top için)|

-----
**4.8. Kullanışlı Komut Kombinasyonları**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|En fazla CPU kullanan süreçleri bul|`ps aux --sort=-%cpu|head`|
|RAM kullanımına göre ilk 10 süreç|`ps aux --sort=-%mem|head`|
|Diskte en büyük klasörleri listele|`du -sh \*|sort -hr|
|Gerçek zamanlı kaynak izle|top|Anlık CPU, RAM, süreç durumu.|
|IP ve ağ arayüzü bilgisi|ip a|Bağlantı ve IP yapılandırmasını gösterir.|
|Aktif bağlantıları izle|netstat -tulnp|Port, servis, PID bilgisi verir.|

-----
**4.9. Bölüm Özeti**

Bu bölümde terminal üzerinden:

- **Sistem bilgilerini (uname, systeminfo)**,
- **Kaynak durumunu (df, free, tasklist)**,
- **İşlem kontrolünü (ps, kill, taskkill)**,
- **Ağ bağlantılarını (netstat, ping, traceroute)**\
  görmeyi ve yönetmeyi öğrendin.

Artık bir sistemin performansını doğrudan terminalden analiz edebilirsin

**5. BÖLÜM – AĞ, İNTERNET ve BAĞLANTI KOMUTLARI**

Bu bölüm, bilgisayarın ağ bağlantılarını, IP yapılandırmalarını, port dinlemelerini ve bağlantı sorunlarını terminal üzerinden yönetmek için kullanılan temel komutları kapsar.\
Ağ yöneticileri, sistem yöneticileri ve geliştiriciler için oldukça kritik komutlardır.

-----
**5.1. Ağ Yapılandırması Görüntüleme**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|IP yapılandırması|ipconfig|Get-NetIPAddress|ifconfig veya ip a|Cihazın IP, maske, ağ geçidi, DNS bilgilerini gösterir.|
|Tüm detayları listele|ipconfig /all|Get-NetIPConfiguration|ip addr show|Ağ adaptörleri ve MAC adresleri dahil detaylı bilgi verir.|
|IP adresini yenile|ipconfig /renew|—|dhclient -r && dhclient|DHCP üzerinden yeni IP alır.|
|IP adresini bırak (reset)|ipconfig /release|—|dhclient -r|Mevcut IP kiralamasını sonlandırır.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|/all|Tüm adaptör ve IP detaylarını gösterir|ipconfig /all|
|/renew|IP adresini yeniler|ipconfig /renew|
|-r|IP’yi bırakır (release)|dhclient -r|
|a|Linux: tüm arayüzleri listeler|ip a|

-----
**5.2. Ağ Bağlantılarını İzleme**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Aktif bağlantılar|netstat -ano|Get-NetTCPConnection|netstat -tulnp|Port, protokol, PID ve bağlantı durumlarını gösterir.|
|Sadece TCP bağlantıları|netstat -p tcp|—|netstat -t|TCP bağlantılarını listeler.|
|Sadece UDP bağlantıları|—|—|netstat -u|UDP bağlantılarını listeler.|
|Port dinleme durumlarını görmek|`netstat -an|find "LISTEN"`|—|ss -tuln|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-a|Tüm bağlantıları göster|netstat -a|
|-n|DNS çözümlemeden sadece IP göster|netstat -an|
|-o|PID bilgilerini dahil et|netstat -ano|
|-t, -u|TCP / UDP bağlantıları|netstat -tu|
|-l|Dinleyen portları listele|netstat -tuln|

-----
**5.3. Bağlantı Testi ve Tanılama**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Ping testi (bağlantı)|ping 8.8.8.8|Test-Connection 8.8.8.8|ping 8.8.8.8|Hedef IP’ye erişim olup olmadığını kontrol eder.|
|Belirli sayıda ping|ping -n 5 8.8.8.8|—|ping -c 5 8.8.8.8|Belirli sayıda ping gönderir.|
|Sürekli ping|ping -t 8.8.8.8|—|ping 8.8.8.8 (CTRL+C ile durdur)|Ağ istikrarını uzun süre test eder.|
|Ağ rotasını izle|tracert google.com|—|traceroute google.com|Paketlerin hedefe ulaşana kadar geçtiği düğümleri gösterir.|
|DNS çözümleme testi|nslookup openai.com|Resolve-DnsName openai.com|dig openai.com|Alan adının IP adresini çözer.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-n, -c|Ping sayısını belirler|ping -n 4 8.8.8.8|
|-t|Sürekli ping gönderir|ping -t 8.8.8.8|
|-h|Maksimum atlama sayısı|traceroute -h 20|
|+short|Kısa DNS cevabı|dig openai.com +short|

-----
**5.4. DNS ve Ağ Servis Yönetimi**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|DNS önbelleğini temizle|ipconfig /flushdns|Clear-DnsClientCache|sudo systemd-resolve --flush-caches|DNS kayıtlarını sıfırlar.|
|DNS sorgusu (manuel)|nslookup|Resolve-DnsName|dig|DNS kayıtlarını görüntüler.|
|Sunucu IP’sini çöz|nslookup openai.com|—|dig openai.com A|Alan adının IPv4 adresini döndürür.|
|Ters DNS sorgusu|—|—|dig -x 8.8.8.8|IP’den alan adını bulur.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|/flushdns|DNS önbelleğini temizler|ipconfig /flushdns|
|+trace|DNS çözümleme zincirini gösterir|dig openai.com +trace|
|A, MX, TXT|DNS kayıt türleri|dig openai.com MX|

-----
**5.5. Ağ Paylaşımları ve Erişim**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Ağ sürücülerini listele|net use|Get-SmbMapping|mount|Bağlı ağ sürücülerini gösterir.|
|Ağ sürücüsü bağla|net use Z: \\sunucu\paylasim|New-SmbMapping|mount -t cifs //sunucu/paylasim /mnt/hedef|Paylaşılan klasöre erişim sağlar.|
|Ağ sürücüsü kaldır|net use Z: /delete|Remove-SmbMapping|umount /mnt/hedef|Ağ bağlantısını kaldırır.|
|SMB bağlantı testi|net view \\sunucu|—|smbclient -L //sunucu -U kullanıcı|Paylaşılan klasörleri listeler.|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|/delete|Paylaşımı kaldırır|net use Z: /delete|
|-t|Bağlantı türünü belirler|mount -t nfs|
|-L|SMB paylaşımlarını listeler|smbclient -L //sunucu|

-----
**5.6. Gelişmiş Ağ Araçları**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Port taraması|—|—|nc -zv IP PORT|Hedef makinede port açık mı test eder.|
|HTTP isteği gönder|curl https://example.com|Invoke-WebRequest|curl veya wget|Web adresine istek atar, yanıt döndürür.|
|Hız testi|—|—|speedtest-cli|İnternet bağlantı hızını ölçer.|
|Ağ paketlerini izleme|—|—|tcpdump|Paket trafiğini analiz eder (root gerektirir).|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-z|Tarama modu (netcat)|nc -zv 192.168.1.1 80|
|-v|Ayrıntılı çıktı|nc -zv IP PORT|
|-O|curl çıktısını dosyaya kaydet|curl -O URL|
|-i|Arayüz seç|tcpdump -i eth0|

-----
**5.7. Parametre ve Kısaltma Tablosu**

|**Parametre**|**Açıklama**|
| :- | :- |
|-a|Tüm bağlantılar|
|-n|IP adresiyle göster|
|-o|PID bilgilerini dahil et|
|-t, -u|TCP / UDP|
|/all|Ayrıntılı ağ bilgisi|
|/flushdns|DNS önbelleğini temizle|
|-c, -n|Ping sayısı|
|-z, -v|Port testi, ayrıntılı çıktı|
|-h|Maksimum atlama (traceroute)|

-----
**5.8. Sık Kullanılan Kombinasyonlar**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|IP ve DNS bilgilerini görmek|ipconfig /all|Tüm adaptörlerin IP yapılandırması.|
|Ağ bağlantılarını listele|netstat -ano|Aktif bağlantılar ve PID bilgisi.|
|Ağ rotasını izlemek|traceroute google.com|Paketlerin geçtiği yönlendiricileri gösterir.|
|DNS çözüm zincirini görmek|dig openai.com +trace|Alan adı çözümleme adımlarını gösterir.|
|Web isteği göndermek|curl -I https://openai.com|HTTP başlıklarını getirir.|
|Port açık mı kontrol et|nc -zv 8.8.8.8 53|Port taraması yapar.|

-----
**5.9. Bölüm Özeti**

Bu bölümde:

- IP yapılandırması (ipconfig, ifconfig, ip a)
- Bağlantı izleme (netstat, ss)
- Ping, traceroute, DNS çözümleme
- Ağ paylaşımları ve port testleri\
  gibi ağ yönetimi için gereken tüm komutları öğrendin.

Artık terminalden hem **ağ teşhisi** hem **bağlantı yönetimi** yapabilirsin

**6. BÖLÜM – PAKET, YAZILIM ve GÜNCELLEME YÖNETİMİ**

Her işletim sisteminin kendi paket yönetim sistemi vardır:

- **Windows:** Chocolatey (choco), Winget (winget)
- **macOS:** Homebrew (brew)
- **Linux:** apt (Debian/Ubuntu), yum/dnf (RHEL/CentOS), pacman (Arch)

Bu bölümde tüm bu yöneticiler için temel komutları bulacaksın.

-----
**6.1. Paket Yöneticileri Genel Görünüm**

|**Platform**|**Yöneticiler**|**Açıklama**|
| :- | :- | :- |
|**Windows**|choco, winget, scoop|Yazılım yönetimi için 3. parti yöneticiler|
|**macOS**|brew|Homebrew en yaygın araçtır|
|**Linux**|apt, yum, dnf, pacman, zypper|Dağıtıma göre farklılık gösterir|

-----
**6.2. Paket Arama**

|**İşlem**|**Windows**|**macOS**|**Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Paket aramak|choco search paket|brew search paket|apt search paket|Paket adını veya açıklamasını arar.|
|Paket detayını görmek|winget show paket|brew info paket|apt show paket|Paket hakkında açıklama ve sürüm bilgisi verir.|

-----
**6.3. Paket Kurulumu**

|**İşlem**|**Windows**|**macOS**|**Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Paket yüklemek|choco install paket|brew install paket|sudo apt install paket|Paket depodan yüklenir.|
|Kurulum sırasında onay sormasın|choco install paket -y|brew install -q paket|sudo apt install -y paket|Onay istemeden otomatik kurar.|
|URL veya dosyadan yükleme|winget install <url>|brew install --cask <paket>|dpkg -i dosya.deb|Manuel kurulum (dosyadan).|

**Faydalı Parametreler**

|**Parametre**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|-y|Onay sormadan yükle|apt install -y|
|--cask|macOS GUI uygulaması yükleme|brew install --cask chrome|
|-q|Sessiz kurulum|brew install -q|
|-i|Dosyadan yükleme|dpkg -i paket.deb|

-----
**6.4. Paket Kaldırma**

|**İşlem**|**Windows**|**macOS**|**Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Paketi kaldır|choco uninstall paket|brew uninstall paket|sudo apt remove paket|Sistemde yüklü paketi kaldırır.|
|Tamamen kaldır (veriler dahil)|—|brew uninstall --zap paket|sudo apt purge paket|Yapılandırma dosyalarıyla birlikte siler.|
|Temizlik / gereksizleri kaldır|choco cleanup|brew cleanup|sudo apt autoremove|Kullanılmayan bağımlılıkları siler.|

-----
**6.5. Güncelleme Yönetimi**

|**İşlem**|**Windows**|**macOS**|**Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Paket listelerini yenile|—|brew update|sudo apt update|Depo listesini günceller.|
|Yüklü paketleri güncelle|choco upgrade all -y|brew upgrade|sudo apt upgrade|Tüm paketleri günceller.|
|Sistemdeki tüm güncellemeleri uygula|—|—|sudo apt full-upgrade|Tüm sistem paketlerini en yeni sürüme getirir.|

-----
**6.6. Depo (Repository) Yönetimi**

|**İşlem**|**Windows**|**macOS**|**Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Yeni depo ekle|—|brew tap depo/adres|sudo add-apt-repository ppa:depo/adres|Ek kaynak ekler.|
|Depo kaldır|—|brew untap depo/adres|sudo add-apt-repository --remove ppa:depo/adres|Eklenen depoyu siler.|
|Mevcut depoları listele|—|brew tap|grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/\*|Kayıtlı depoları gösterir.|

-----
**6.7. Paket Sorgulama ve Durum Kontrolü**

|**İşlem**|**Windows**|**macOS**|**Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Paket yüklü mü kontrol et|choco list --local-only|brew list|`dpkg -l|grep paket`|
|Paket sürümünü görmek|choco info paket|brew info paket|`apt show paket|grep Version`|
|Eksik bağımlılıkları bulmak|—|—|sudo apt check|Bağımlılık hatalarını kontrol eder.|

-----
**6.8. Arşivleme / Sıkıştırılmış Paket İşlemleri**

|**İşlem**|**Windows**|**macOS**|**Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|.zip dosyasını aç|tar -xf dosya.zip *(PowerShell)*|unzip dosya.zip|unzip dosya.zip|Zip dosyalarını açar.|
|.tar.gz oluştur|—|—|tar -czvf arsiv.tar.gz klasor|Klasörü arşivleyip sıkıştırır.|
|.tar.gz aç|—|—|tar -xzvf arsiv.tar.gz|Arşivi açar.|
|.deb paket aç|—|—|dpkg -x paket.deb hedef/|Deb dosyasının içeriğini çıkarır.|

-----
**6.9. Parametre ve Kısaltma Tablosu**

|**Parametre**|**Açıklama**|
| :- | :- |
|-y|Onay sormadan uygula|
|-q|Sessiz (quiet) mod|
|--cask|macOS GUI uygulamaları|
|--zap|Kalan dosyaları da sil|
|-i|Dosyadan kurulum|
|--purge / purge|Yapılandırma dosyalarıyla kaldır|
|update|Depo listesini yenile|
|upgrade|Paketleri güncelle|
|autoremove|Gereksiz bağımlılıkları kaldır|

-----
**6.10. Kullanışlı Komut Kombinasyonları**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Tüm sistem güncellemesi (Ubuntu)|sudo apt update && sudo apt upgrade -y|Paket listelerini günceller ve yükseltir.|
|macOS güncelleme zinciri|brew update && brew upgrade && brew cleanup|Tüm Homebrew sistemini günceller.|
|Tüm Chocolatey paketlerini güncelle|choco upgrade all -y|Windows'taki tüm yazılımları günceller.|
|Yeni depo ekle ve yükle|sudo add-apt-repository ppa:depo && sudo apt update && sudo apt install paket|Yeni kaynak ekleyip yükleme yapar.|
|Arşivleme ve yedekleme|tar -czvf yedek.tar.gz /var/www|Dizin yedeği oluşturur.|

-----
**6.11. Bölüm Özeti**

Bu bölümde terminal üzerinden:

- **Paket yükleme ve kaldırma** (apt install, choco install, brew uninstall)
- **Depo ve bağımlılık yönetimi**
- **Tam sistem güncelleme işlemleri**
- **Arşivleme (tar/zip)**\
  komutlarını öğrendin.

Artık hem Windows, macOS hem de Linux ortamlarında **yazılım kurulum ve güncelleme süreçlerini tamamen terminalden yönetebilirsin.**

**7. BÖLÜM – ÇIKTI YÖNLENDİRME, LOGLAMA ve BORU HATLARI**

Terminalde her komut bir “çıktı” (output) üretir.\
Bu çıktılar ekrana yazılabilir, dosyaya yönlendirilebilir veya başka bir komuta aktarılabilir.\
Bu sistemin temeli **stdout (çıktı)**, **stderr (hata)** ve **stdin (girdi)** akışlarına dayanır.

-----
**7.1. Temel Çıktı Yönlendirme Operatörleri**

|**Operatör**|**Açıklama**|**Örnek**|**Açıklama (Detaylı)**|
| :- | :- | :- | :- |
|>|Çıktıyı yeni dosyaya yazar (varsa üzerine yazar)|ls > liste.txt|“liste.txt” dosyasına yazılır, eski içerik silinir.|
|>>|Çıktıyı dosyanın sonuna ekler|echo "Yeni kayıt" >> log.txt|Log veya ekleme işlemleri için kullanılır.|
|<|Girdi olarak dosya kullan|sort < isimler.txt|Dosya içeriğini komuta girdi olarak verir.|
|2>|Hata çıktısını yönlendirir|command 2> error.txt|Sadece hata mesajlarını kaydeder.|
|&>|Normal + hata çıktısını yönlendirir|command &> tumlog.txt|Tüm çıktılar aynı dosyaya gider.|

-----
**7.2. Boru (Pipe) | Operatörü**

|**Komut**|**Açıklama**|**Ne Yapar**|
| :- | :- | :- |
|`ls|grep .txt`|grep komutuna aktarır|
|`cat dosya.txt|sort`|Çıktıyı sıralar|
|`ps aux|grep firefox`|Filtreleme yapar|
|`dmesg|less`|Sayfalı görüntüleme|
|`netstat -tuln|grep 80`|Port filtresi|

-----
**7.3. Girdi / Çıktı Akış Mantığı**

|**Akış**|**Sembol**|**Açıklama**|
| :- | :- | :- |
|**stdin**|< veya 0<|Komutun girdi kaynağı|
|**stdout**|> veya 1>|Komutun standart çıktısı|
|**stderr**|2>|Komutun hata çıktısı|

**Örnek:**

grep "hata" app.log > sonuc.txt 2> hatalar.txt

→ Normal çıktı sonuc.txt'ye, hatalar hatalar.txt'ye gider.

-----
**7.4. Loglama (Kayıt Tutma)**

|**İşlem**|**Windows**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- |
|Komut çıktısını log dosyasına kaydet|command > log.txt|command > log.txt|Çıktı log dosyasına yazılır.|
|Hataları ayrı log dosyasına kaydet|—|command 2> error.log|Hataları ayırır.|
|Hem çıktı hem hata logla|—|command &> full.log|Tüm çıktılar tek dosyada.|
|Tarihli log tut|—|echo "$(date): işlem tamam" >> app.log|Log dosyasına zaman damgası ekler.|

-----
**7.5. Çıktı Filtreleme ve Metin İşleme**

|**Komut**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|grep|Belirli kelimeleri filtreler|grep "error" log.txt|
|sort|Çıktıyı alfabetik sıralar|`ls|
|uniq|Tekrarlanan satırları kaldırır|`sort dosya.txt|
|wc|Satır, kelime, karakter sayar|`cat dosya.txt|
|head, tail|İlk / son satırları gösterir|tail -n 10 log.txt|
|cut|Belirli sütunları ayırır|cut -d ":" -f1 /etc/passwd|
|awk|Metin içinde sütun bazlı işlem yapar|awk '{print $1}' dosya.txt|
|tee|Hem ekrana yaz hem dosyaya kaydet|`ls|

-----
**7.6. Parametre ve Kısaltma Tablosu**

|**Parametre / Operatör**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|>|Çıktıyı dosyaya yönlendir|ls > liste.txt|
|>>|Dosyaya ekleme yap|echo "satır" >> log.txt|
|<|Girdi olarak dosya kullan|sort < dosya.txt|
|2>|Hata çıktısını yönlendir|python script.py 2> errors.log|
|&>|Hem hata hem çıktı yönlendirme|command &> tam.log|
|`|`|Çıktıyı başka komuta aktar|
|tee|Aynı anda ekrana ve dosyaya yaz|`ls|

-----
**7.7. Sık Kullanılan Kombinasyonlar**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Belirli kelimeyi log içinde ara|`grep "ERROR" app.log|tee errors.txt`|
|Hataları ayrı logla|command > out.txt 2> err.txt|Çıktı ve hatalar ayrı dosyalara gider.|
|En son 10 log satırını izle|tail -f app.log|Yeni log satırlarını canlı gösterir.|
|Logları filtrele ve say|`grep "404" access.log|wc -l`|
|Çıktıyı sıralayıp eşsiz satırları bul|`cat isimler.txt|sort|

-----
**7.8. Windows İçin Eşdeğerler**

|**İşlem**|**CMD / PowerShell Komutu**|**Açıklama**|
| :- | :- | :- |
|Çıktıyı dosyaya kaydet|command > dosya.txt|Çıktıyı kaydeder.|
|Ekleyerek yaz|echo "satır" >> log.txt|Log’a ekler.|
|Hataları kaydet|command 2> err.txt|Sadece hata mesajlarını kaydeder.|
|Filtreleme (grep alternatifi)|findstr "aranan"|Dosya veya çıktıda metin arar.|
|Birden fazla komutu zincirle|`dir|findstr ".txt"`|

-----
**7.9. Bölüm Özeti**

Bu bölümde öğrendin:

- > ve >> ile **çıktı yönlendirmeyi**
- | (pipe) ile **komut zincirlemeyi**
- grep, sort, tee, wc, awk gibi **metin işleme araçlarını**
- tail -f gibi **canlı log izlemeyi**

Artık terminalden veri akışını yönetebilir, çıktıları istediğin gibi yönlendirebilir ve log tutabilirsin 

**8. BÖLÜM – BETİKLER, OTOMASYON ve GÖREV ZAMANLAMA**

Bu bölüm, komutları tek tek yazmadan toplu çalıştırmayı, otomatik görev planlamayı ve zamanlayıcı sistemleri kullanmayı öğretir.\
Platformlara göre Bash (Linux/macOS) ve PowerShell / Task Scheduler (Windows) temelli örnekler içerir.

-----
**8.1. Betik (Script) Nedir?**

- **Tanım:** Birden fazla terminal komutunu .sh (Linux/macOS) veya .ps1 (PowerShell) dosyasına yazıp, sırasıyla çalıştırılabilir hale getirmektir.
- **Amaç:** Otomasyon, yedekleme, loglama, sistem bakımı gibi tekrar eden işlemleri otomatikleştirmek.
-----
**8.2. Basit Betik Oluşturma**

|**Platform**|**Betik Dosyası**|**Örnek İçerik**|**Açıklama**|
| :- | :- | :- | :- |
|**Linux/macOS**|nano script.sh|bash #!/bin/bash echo "Yedekleme başlatıldı" tar -czvf yedek.tar.gz /home/user/dosya|#!/bin/bash satırı shell türünü belirtir.|
|**Windows (PowerShell)**|notepad script.ps1|powershell Write-Output "Sistem kontrol başlıyor" Get-Date Get-Process|.ps1 uzantısı PowerShell betikleridir.|

**Çalıştırmak için:**

chmod +x script.sh

./script.sh

Windows’ta:

powershell.exe -ExecutionPolicy Bypass -File .\script.ps1

-----
**8.3. Değişkenler ve Parametreler**

|**Platform**|**Örnek**|**Açıklama**|
| :- | :- | :- |
|Linux/macOS|isim="Ali" → echo $isim|$ değişken kullanımı|
|PowerShell|$isim = "Ali" → Write-Output $isim|$ ile başlar, doğrudan kullanılabilir|
|Bash argüman|$1, $2, $@|Komuta verilen parametreleri alır|
|PowerShell argüman|$args[0], $args[1]|Script’e gönderilen parametreler|

-----
**8.4. Koşullar ve Döngüler**

|**Tür**|**Linux/macOS**|**PowerShell**|**Açıklama**|
| :- | :- | :- | :- |
|If Koşulu|bash if [ -f dosya.txt ]; then echo "Var"; fi|powershell if (Test-Path "dosya.txt") { "Var" }|Belirli koşul sağlanıyorsa işlem yapar.|
|For Döngüsü|bash for i in \*.txt; do echo $i; done|powershell foreach ($i in Get-ChildItem \*.txt) { $i }|Her dosya veya öğe üzerinde işlem yapar.|
|While Döngüsü|bash while true; do date; sleep 5; done|powershell while ($true) { Get-Date; Start-Sleep 5 }|Sonsuz veya şartlı tekrar döngüsü.|

-----
**8.5. Fonksiyonlar**

|**Platform**|**Tanım**|**Kullanım**|
| :- | :- | :- |
|Linux/macOS|bash selam() { echo "Merhaba $1"; } selam Ali|Fonksiyon tanımlama ve çağırma.|
|PowerShell|powershell function Selam { param($isim) Write-Output "Merhaba $isim" } Selam "Ali"|Parametreli PowerShell fonksiyonu.|

-----
**8.6. Görev Zamanlama (Task Scheduling)**

|**Platform**|**Araç**|**Komut**|**Açıklama**|
| :- | :- | :- | :- |
|**Windows**|**Task Scheduler**|schtasks /create /tn "yedek" /tr "C:\yedek.ps1" /sc daily /st 09:00|Her gün saat 09:00’da script çalıştırır.|
|**PowerShell**|**Scheduled Job**|Register-ScheduledJob -Name Yedek -ScriptBlock { Backup-Process } -Trigger (New-JobTrigger -Daily -At 9am)|PowerShell üzerinden planlı görev oluşturur.|
|**Linux/macOS**|**cron**|crontab -e → 0 9 \* \* \* /home/user/yedek.sh|Her sabah 09:00’da script çalıştırır.|

` `**Cron formatı (dakika saat gün ay hafta)**

\* \* \* \* \*  komut

│ │ │ │ │

│ │ │ │ └─ haftanın günü (0-6)

│ │ │ └─── ay (1-12)

│ │ └───── ayın günü (1-31)

│ └─────── saat (0-23)

└───────── dakika (0-59)

-----
**8.7. Parametre ve Kısaltma Tablosu**

|**Parametre / Anahtar**|**Açıklama**|
| :- | :- |
|-File|PowerShell betik dosyası çalıştırır|
|-ExecutionPolicy Bypass|Betik güvenlik kısıtlamasını aşar|
|-sc daily|Windows görev zamanlayıcısında günlük tekrar|
|-st|Başlangıç saati|
|crontab -e|Cron zamanlayıcıyı düzenler|
|@reboot|Sistem açıldığında çalıştır|
|sleep, Start-Sleep|Belirli süre bekletir|

-----
**8.8. Sık Kullanılan Betik Örnekleri**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Otomatik yedekleme|bash tar -czf /yedek/$(date +%F).tar.gz /home/user|Tarihli yedekleme script’i.|
|Günlük log temizleme|bash find /var/log -type f -mtime +7 -delete|7 günden eski logları siler.|
|PowerShell CPU kontrolü|```powershell Get-Process|Sort CPU -Descending|
|Zamanlanmış sistem raporu|schtasks /create /tn "rapor" /tr "C:\rapor.ps1" /sc hourly|Her saat sistem raporu oluşturur.|
|Her açılışta çalıştır|@reboot /home/user/script.sh (cron)|Sistem açıldığında script çalışır.|

-----
**8.9. Betik Hatalarını Loglama**

|**İşlem**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Linux/macOS|bash script.sh > out.log 2> err.log|Hataları ayrı dosyaya kaydeder.|
|PowerShell|.\script.ps1 \*> full.log|Hem hata hem çıktı aynı logta.|
|Zaman damgalı loglama|echo "$(date): script çalıştı" >> /var/log/custom.log|Otomatik log kaydı.|

-----
**8.10. Bölüm Özeti**

Bu bölümde:

- **Bash ve PowerShell betikleriyle otomasyon** kurmayı,
- **Koşullar ve döngüler** ile akış kontrolünü,
- **Görev zamanlama araçları (cron / schtasks)** ile betikleri planlamayı öğrendin.

Artık terminalde sadece komut yazmakla kalmayıp **kendi otomatik sistemini** kurabilirsin 

**9. BÖLÜM – HATA AYIKLAMA, GÜVENLİK ve YAYGIN HATALAR**

Terminal güçlüdür; yanlış bir komut geri döndürülemez sonuçlar doğurabilir.\
Bu bölüm, güvenli çalışmayı öğretir, hataları anlamayı ve çözmeyi kolaylaştırır.

-----
**9.1. Tehlikeli Komutlar ve Uyarılar**

|**Komut**|**Tehlike**|**Açıklama**|
| :- | :- | :- |
|rm -rf /|🔥 Tüm sistemi siler|Dizin farkı gözetmeden tüm dosyaları kaldırır.|
|`:(){ :|:& };:`|⚠️ Fork bombası|
|chmod -R 777 /|🚫 Güvenlik açığı|Herkese tam erişim verir, ciddi risklidir.|
|dd if=/dev/zero of=/dev/sda|💀 Disk silme|Tüm diski sıfırlar.|
|mkfs.ext4 /dev/sda1|💾 Format|Disk bölümünü yeniden biçimlendirir.|

💡 **Altın Kural:**

Komut root (sudo) yetkisiyle çalışacaksa iki kere düşün.

-----
**9.2. Komut Hatalarını Okuma ve Anlama**

|**Hata Tipi**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|command not found|Komut sistemde yüklü değil|curl eksikse → sudo apt install curl|
|Permission denied|Yetki yok|chmod +x script.sh veya sudo ekle|
|No such file or directory|Dosya/dizin mevcut değil|Yol yanlış yazılmış olabilir|
|Syntax error|Komut biçimi hatalı|Fazla boşluk, eksik karakter|
|Is a directory|Dosya yerine klasör üzerinde işlem yapılıyor|rm klasor yerine rm -r klasor|

-----
**9.3. Yetki ve Root Kullanımı**

|**Komut**|**Açıklama**|**Örnek**|
| :- | :- | :- |
|sudo komut|Komutu yönetici yetkisiyle çalıştırır|sudo apt update|
|sudo -i|Root kabuğu açar|Tam yönetici erişimi sağlar|
|su kullanıcı|Kullanıcı değiştirir|su root → root hesabına geçiş|
|whoami|Mevcut kullanıcıyı gösterir|Root olup olmadığını kontrol et|

**Güvenli Kullanım İpuçları**

- sudo sadece **gerekli komutlarda** kullanılmalı
- Betiklerde sudo satırı yazma; kullanıcıya bırak
- Root dizininde (/) silme işlemleri yapma
-----
**9.4. Hata Ayıklama (Debugging) Yöntemleri**

|**Platform**|**Komut / Parametre**|**Açıklama**|
| :- | :- | :- |
|Bash|bash -x script.sh|Her satırı çalışırken gösterir|
|PowerShell|Set-PSDebug -Trace 1|Betik akışını adım adım izler|
|Tümü|echo $VAR|Değişken değerini kontrol et|
|Linux/macOS|set -e|Hata olduğunda script’i durdurur|
|PowerShell|try { } catch { }|Hataları yakalayarak özelleştirir|

**Örnek:**

set -e

echo "Başlıyor"

cp kaynak hedef || echo "Kopyalama başarısız!"

-----
**9.5. Günlük (Log) ve İzleme Dosyaları**

|**Sistem**|**Dosya / Komut**|**Açıklama**|
| :- | :- | :- |
|Linux|/var/log/syslog|Genel sistem logları|
|Linux|/var/log/auth.log|Yetki / oturum logları|
|Linux|dmesg|Kernel mesajları|
|macOS|log show|Sistem loglarını görüntüler|
|Windows|eventvwr.msc|Olay görüntüleyici (Event Viewer)|
|PowerShell|Get-EventLog -LogName Application|Uygulama loglarını listeler|

**Log dosyalarını takip etmek:**

tail -f /var/log/syslog

Canlı olarak yeni log satırlarını gösterir.

-----
**9.6. Güvenli Betik Yazımı**

|**Uygulama**|**Tavsiye**|
| :- | :- |
|**Yedekleme**|rm yerine mv veya trash kullan.|
|**Değişkenler**|Çift tırnak kullan → "$VAR" (boşluk korur).|
|**Girdi kontrolü**|Script’lerde if [ -z "$1" ]; then echo "Parametre eksik"; exit 1; fi ekle.|
|**Yedek al**|Kritik işlem öncesi cp ile dosya kopyala.|
|**Log ekle**|echo "$(date): işlem yapıldı" >> script.log|

-----
**9.7. Yaygın Kullanıcı Hataları**

|**Hata**|**Neden**|**Çözüm**|
| :- | :- | :- |
|sudo: command not found|Minimal sistem kurulumu|apt install sudo|
|Operation not permitted|Dosya kilitli / root izni gerekli|sudo ekle veya chown değiştir|
|device or resource busy|Disk veya süreç kullanıyor|umount -f veya fuser ile bul|
|broken packages (apt)|Bağımlılıklar bozuldu|sudo apt --fix-broken install|
|command hangs|Komut takıldı|Ctrl + C ile durdur|

-----
**9.8. Hata Çözümleme Komutları**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Son log satırlarını gör|tail -n 50 /var/log/syslog|Son 50 satırı listeler.|
|Belirli kelimeyle log ara|grep "error" /var/log/syslog|Hata satırlarını filtreler.|
|Sistemde en son hatalar|journalctl -p 3 -xe|Kritik sistem hataları.|
|Disk hatalarını kontrol et|fsck /dev/sda1|Dosya sistemi bütünlüğünü kontrol eder.|
|Bellek kullanımına göre sıralama|`ps aux --sort=-%mem|head`|

-----
**9.9. Parametre ve Kısaltma Tablosu**

|**Parametre**|**Açıklama**|
| :- | :- |
|-x|Komutları adım adım göster (debug)|
|-e|Hata olduğunda script’i durdur|
|-f|Onay sormadan (force)|
|-R|Alt dizinleri dahil et|
|-p|İzinli / hata seviyesini belirt|
|-n, -t|tail komutunda satır sayısı / takip et|
|-p 3|journalctl’de hata önceliği 3 (error)|

-----
**9.10. Güvenlik ve En İyi Uygulamalar**

**Yap:**

- sudoyu sadece gerektiğinde kullan
- rm -rf yerine trash-cli veya mv kullan
- chmod işlemlerinde 777 yerine 755 / 644 tercih et
- Her betiğe “loglama” ekle
- Otomasyonlarda “try-catch” veya set -e ile hata yakala

**Yapma:**

- / kök dizininde silme
- sudo ile belirsiz script çalıştırma
- İnternetten bulduğun komutu kopyalayıp doğrudan çalıştırma
- Root shell’de uzun süre açık kalma
-----
**9.11. Bölüm Özeti**

Bu bölümde:

- **Tehlikeli komutları** tanıdın (örneğin rm -rf /)
- **Yetki ve root farkını** öğrendin
- **Hata ayıklama araçlarını (bash -x, tail, grep)** kullandın
- **Güvenli çalışma prensiplerini** benimsedin

Artık terminali bilinçli ve güvenli biçimde kullanabilecek seviyedesin 

**10. BÖLÜM – EK KOMUTLAR, KISAYOLLAR ve PLATFORM KARŞILAŞTIRMALARI**

-----
**10.1. Genel Amaçlı Yardımcı Komutlar**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- | :- |
|Ekranı temizle|cls|Clear-Host|clear|Terminal ekranını temizler.|
|Çıkış|exit|exit|exit|Terminal oturumunu kapatır.|
|Tarih/saat göster|date /t|Get-Date|date|Güncel tarihi gösterir.|
|Tarih/saat ayarlama|date 01-01-2025|Set-Date|sudo date -s "2025-01-01 10:00"|Sistemin tarihini değiştirir.|
|Dosya veya metin arama|find /i "metin"|Select-String "metin"|grep "metin"|Belirli kelime veya satırı arar.|
|Dosya farkı karşılaştır|fc dosya1 dosya2|Compare-Object|diff dosya1 dosya2|İki dosya arasındaki farkları listeler.|
|İşlem geçmişi göster|doskey /history|Get-History|history|Daha önce girilen komutları listeler.|

-----
**10.2. Klavye Kısayolları (Terminal)**

|**Kısayol**|**Açıklama**|**Platform**|
| :- | :- | :- |
|Ctrl + C|Çalışan komutu durdur|Tümü|
|Ctrl + D|Oturumu sonlandır|macOS / Linux|
|Ctrl + L|Ekranı temizle (clear)|macOS / Linux|
|Ctrl + R|Geçmişte komut ara|Tümü|
|↑ / ↓|Önceki / sonraki komut|Tümü|
|Tab|Otomatik tamamlama|Tümü|
|Ctrl + U|Satırı temizle|macOS / Linux|
|Ctrl + A|Satır başına git|Tümü|
|Ctrl + E|Satır sonuna git|Tümü|
|Ctrl + Shift + C / V|Kopyala / Yapıştır|Tümü|
|Ctrl + Z|Komutu askıya al|macOS / Linux|
|fg|Askıya alınanı devam ettir|macOS / Linux|

-----
**10.3. Platformlar Arası Komut Karşılaştırması**

|**İşlem**|**Windows CMD**|**PowerShell**|**macOS / Linux**|
| :- | :- | :- | :- |
|Dizin listele|dir|Get-ChildItem|ls|
|Dizin değiştir|cd|Set-Location|cd|
|Dosya oluştur|type nul > a.txt|New-Item a.txt|touch a.txt|
|Dosya sil|del a.txt|Remove-Item a.txt|rm a.txt|
|Kopyalama|copy|Copy-Item|cp|
|Taşıma / yeniden adlandırma|move|Move-Item|mv|
|Dizin oluştur|mkdir|New-Item -ItemType Directory|mkdir|
|İzinleri değiştir|icacls|Set-Acl|chmod|
|Sahip değiştir|icacls /setowner|Set-Acl|chown|
|Ağ durumu|netstat -ano|Get-NetTCPConnection|netstat -tulnp|
|Sistem bilgisi|systeminfo|Get-ComputerInfo|uname -a|
|Paket yöneticisi|choco / winget|Install-Package|apt, yum, brew|

-----
**10.4. Matematik, Zaman ve Sayı İşlemleri**

|**İşlem**|**Komut**|**Platform**|**Açıklama**|
| :- | :- | :- | :- |
|Hesaplama|set /a 5+3|Windows|Basit aritmetik|
|Hesaplama|$x=5+3; $x|PowerShell|Aritmetik işlem sonucu|
|Hesaplama|expr 5 + 3|Linux/macOS|Komut satırında işlem|
|Zaman farkı hesapla|—|Get-Date|Tarih farkı ölçümü|
|Zamanlayıcı|timeout 5|Start-Sleep 5|sleep 5|

-----
**10.5. Dosya Aktarımı ve Uzak Erişim**

|**İşlem**|**Windows**|**macOS / Linux**|**Açıklama**|
| :- | :- | :- | :- |
|Uzak sisteme bağlan|ssh user@ip (PowerShell de destekler)|ssh user@ip|Güvenli terminal bağlantısı|
|Dosya kopyala (uzak sistem)|scp file user@ip:/hedef|scp file user@ip:/hedef|SSH üzerinden dosya gönderir|
|Dosya senkronizasyonu|—|rsync -av kaynak hedef|Klasörleri eşitleme|
|FTP bağlantısı|ftp sunucu|ftp sunucu|FTP sunucusuna bağlanır|
|Dosya indirme|curl -O url|wget url|İnternetten dosya çeker|

-----
**10.6. Kullanışlı Sistem Kısayolları (CLI)**

|**Amaç**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Sistem yeniden başlatma|shutdown /r /t 0|Hemen yeniden başlatır (Windows)|
|Sistem kapatma|shutdown /s /t 0|Bilgisayarı kapatır|
|Linux yeniden başlatma|sudo reboot|Yeniden başlatır|
|Linux kapatma|sudo shutdown now|Kapatır|
|macOS kapatma|sudo shutdown -h now|Anında kapanma|
|Uptime öğren|uptime|Sistem ne kadar süredir açık|
|CPU çekirdek sayısı|nproc|Linux’ta CPU bilgisi|
|Disk kullanımı|du -sh \*|Boyut bazlı özet|

-----
**10.7. Renk, Prompt ve Terminal Özelleştirmeleri**

|**Platform**|**Komut**|**Açıklama**|
| :- | :- | :- |
|Windows CMD|color 0A|Yeşil yazı rengi (0 = siyah zemin, A = yeşil)|
|PowerShell|Set-PSReadLineOption -Colors @{ Command = 'Cyan' }|Komut rengini değiştirir|
|Linux/macOS|PS1="\u@\h:\w$ "|Prompt satırını özelleştirir|
|Linux/macOS|export LS\_COLORS|Liste renk ayarlarını değiştirir|

-----
**10.8. Sık Kullanılan Tüm Sistem Kısayolları (Özet)**

|**Amaç**|**Kısayol / Komut**|**Açıklama**|
| :- | :- | :- |
|Komutu iptal et|Ctrl + C|Çalışan komutu durdurur|
|Terminali temizle|Ctrl + L veya clear|Ekranı temizler|
|Son komutu tekrar et|!!|Son girilen komutu tekrar çalıştırır|
|Kök dizine git|cd /|Dosya sisteminin köküne gider|
|Bir üst klasöre git|cd ..|Üst dizine geçer|
|Kullanıcı dizinine git|cd ~|Home dizinine döner|
|Tüm geçmişi göster|history|Komut geçmişini listeler|
|Belirli komutu ara|Ctrl + R|Geçmişte arama yapar|
|Otomatik tamamlama|Tab|Dosya / komut tamamlar|
|Yardım al|komut --help veya / ?|Komut açıklamasını gösterir|

-----
**10.9. Örnek Karşılaştırmalı Kullanımlar**

|**Amaç**|**Windows (CMD/PowerShell)**|**macOS/Linux**|**Açıklama**|
| :- | :- | :- | :- |
|Ağ bağlantısı testi|ping 8.8.8.8|ping -c 4 8.8.8.8|IP’ye erişim testi|
|Sistem güncellemesi|choco upgrade all -y|sudo apt update && sudo apt upgrade -y|Tüm paketleri günceller|
|Klasör kopyalama|xcopy /s /e kaynak hedef|cp -r kaynak hedef|Alt dizinlerle kopyalar|
|Dosya içeriği görüntüleme|type dosya.txt|cat dosya.txt|Dosya içeriğini gösterir|
|Süreç listesi|tasklist|ps aux|Aktif işlemleri gösterir|
|Dosya arama|dir /s dosya.txt|find . -name dosya.txt|Alt dizinlerde arar|

-----
**10.10. Bölüm Özeti**

Bu bölümde:

- Tüm sistemlerdeki **eşdeğer komutları** öğrendin,
- **Kısayollar** ile terminal hızını artırmayı gördün,
- **Renk, prompt ve kişiselleştirme** yöntemlerine hakim oldun,
- Artık hangi sistemde olursan ol, komut mantığını **tek bakışta** anlayabilirsin

