# Winden-Archa: Windows'tan, Arch Linux'a Geçmek İçin Basit Bir Rehber

| 📝 **Söz** |
|--------------|
| "Özgürlükten doğan bunalımlar ne kadar büyük olursa olsun, hiçbir zaman fazla baskının sağladığı sahte güvenlikten daha tehlikeli değildir." |

## Giriş

**Winden-Archa**, benim tarafımdan; Windows 10/11 sistemlerinden Arch-Linux bazlı bir sisteme geçmek isteyen, işletim sistemine gereksiz yazılım katmadan ve aynı zamanda süreci mümkün olduğunca basit tutmak isteyen kişilere yardımcı olmak amacıyla yazılmıştır.

Bunu yapmanın en iyi yolunun ise deneyim paylaşmak olduğunu düşünüyorum. Dolayısıyla, bu rehber; bu yola çıkmış olan herhangi birine uyacak şekilde, çoğunlukla kendi deneyimime dayanarak hazırlandı.

> **⚠ DİKKAT:** Winden-Archa, GNU/Linux hakkında belli bir bilgiye sahip olan ve uçbirimi kullanmakta rahat olan kişileri hedef almakta. Bu belge her ne kadar Arch'ı kullanıcı dostu ve görsel yapmayı hedeflese de sorunları çözmek ve paketler/uygulamalar indirmek için uçbirimi kullanman gerekeceğinden lütfen geçiş yapmayı denemeden önce GNU/Linux uçbirimi hakkında yeterli araştırmayı yapmış olduğundan emin ol.
>
> Gelecekte yaşanabilecek karmaşaları önlemek için herhangi bir adımı denemeye yeltenmeden önce rehberin tamamını okumak önerilir.
>
> Bu rehberde kullanılması hedeflenen her şey **tamamen özgür ve açık-kaynak yazılımıdır.**

---

## Arch Kurulumunu Hazırlama

Arch Linux'un kendi bünyesinde herhangi bir grafik arayüzüne sahip kurulum ekranı bulunmamaktdır, bu durum Arch'ın basit ve hafif doğasını fazla uğraşmadan veya risk almadan deneyimlemek isteyenler için zorluklar oluşturabilir.

Bu nedenle mevcut duruma en uygun olarak **EndeavourOS** kullanılabilir. EndeavourOS, Arch tabanlı bir işletim sistemidir ve Arch ile aynı prensipleri takip eder. Aynı zamanda güncel olarak Distrowatch'a göre en popüler Arch tabanlı işletim sistemidir.

Arch'ı (EndeavourOS'i) kurmak için önyüklenebilir bir bellek kullanabilirsiniz. Önerilen yöntem ise (en az **2GB önerilir**) bir USB belleği EndeavourOS'i kurmak için önyüklenebilir belleğe çevirmektir.

Windows 10 veya 11 sistemlerinde bu işlemi gerçekleştirebilicek **Ventoy** ve **Rufus** gibi programlar bulunmaktadır. Bu rehberde ise önerilen program Rufus'tur, çünkü kendi deneyimlerimde Rufus'u kullandım. Fakat istediğiniz ve kullanmayı bildiğiniz başka herhangi bir programı kullanmaktan çekinmeyin.

### Önyüklenebilir USB Belleği Oluşturmanın Adımları

#### 1. Rufus'u İndirin
- [Rufus'un resmi sitesini](https://rufus.ie/) ziyaret edin ve sisteminize uygun olan sürümünü indirin.
- Standart ve taşınabilir sürümlerden istediğinizi seçebilirsiniz.

#### 2. EndeavourOS'in ISO Dosyasını İndirin
- [EndeavourOS'in resmi sitesini](https://endeavouros.com/) ziyaret edin ve listelenmiş aynalardan sisteminize uygun olan en güncel ISO dosyasını indirin.
- Üçüncü adım için **imza dosyasını** indirmeyi göz önünde bulundurun.
- İşlemi hızlandırmak için coğrafi konumunuza en yakın olan aynayı tercih edebilirsiniz.

#### 3. ISO Dosyasını Doğrulayın (İsteğe bağlı fakat şiddetle tavsiye edilir)
İndirilen ISO dosyasının özgünlüğünü ve güvenirliğini doğrulamak için **GPG**'yi kullanabilirsiniz. Bu rehberde GPG'yi kullanmanın önerilen yolu ise **WSL (Linux için Windows Alt Sistemi)** aracığıyladır.

   ```powershell
   wsl --install -d Debian
   ```
3. Kurulum tamamlandığında bilgisayarınızı yeniden başlatın.
4. Şunu çalıştırarak GPG'nin kurulduğundan emin olun:
   ```bash
   sudo apt install gpg
   ```
   Eğer GPG kurulu değilse üstteki komutu kullanarak kurun.
5. EndeavourOS'in sitesindeki yönergeleri izleyerek **sha512** ve **gpg** komutlarını kullanarak ISO dosyasını doğrulayın.
6. Eğer doğrulama **"OK"** geri dönütünü verirse bir sonraki adıma devam edin.

#### 4. Rufus'u Kullanarak Önyüklenebilir USB Bellek Oluşturma
1. **USB belleğinizi** takın ve **Rufus**'u açın.
2. Rufus USB belleğinizi kendiliğinden tespit edemezse USB belleğinizi kendiniz seçin.
   > **⚠ DİKKAT:** **SÜRÜCÜDEKİ TÜM VERİLER SİLİNECEK** bu yüzden doğru sürücüyü seçtiğinizden emin olun.
3. "Imaj Seçeneği," altından **EndeavourOS ISO** dosyasını seçin (imza dosyasına doğrulamadan sonra ihtiyaç yok).
4. Uygun olan disk bölüm düzenini seçin:
   - Eğer bilgisayarın **UEFI**'yi destekliyorsa şunları seçin:
     - Disk bölüm düzeni olarak **GPT**.
     - Hedef sistem olarak **UEFI (CSM yok)**.
   - Bilgisayarınız **çok eski** ise ve UEFI'yi **desteklemiyorsa** şunları seçin:
     - Disk bölüm düzeni olarak **MBR**.
     - Hedef sistem olarak **BIOS ya da UEFI**.
5. Diğer seçenekleri olduğu gibi bırakın.
6. **BAŞLAT**'a tıklayın. İstendiği takdirde,  Rufus "ISO Imaj modunda yaz" seçeneğini önerse bile bu seçeneği şu anda seç**me**yin.
   - Bu rehber ileride yaşanabilecek sorunları önlemek için **"DD Imaj modunda yaz" seçeneğini tercih etmenizi önerir**.

   > **⚠ DİKKAT:** Bu seçeneği tercih etmek ISO'yu USB belleğe yazdıktan sonra belleğe erişememenize sebep olabilir, bu nedenle **yalnızca bu görevin amaçları için olan** bir USB bellek kullandığınızdan emin olun.

7. Veri kaybı hakkındaki uyarıları onaylayın ve işlemin tamamlanmasını bekleyin.
8. Tamamlandığında **"HAZIR."** yazan yeşil bir kutu göreceksiniz.
9. Başarıyla önyüklenebilir bir USB bellek oluşturdunuz. Artık gerekiyorsa belleği çıkartabilirsiniz.

---

## EndeavourOS aracılığıyla Arch'ı Kurma

- EndeavourOS'i sisteminize kurmak için tercih ettiğiniz cihaza, cihaz kapalıyken önyüklenebilir USB sürücüyü takın.

Sisteminizi çalıştırın ve devamlı olarak BIOS/UEFI arayüzüne girmek için olan doğru tuşa basın. Doğru tuşun hangisi olduğunu bilmiyorsanız bilgisayarınızın / anakartınızın üreticisinin websitesinde arayabilir veya DEL, F2, F10 ve ESC gibi bazı yaygın tuşları deneyebilirsiniz.

> **⚠ DİKKAT:** GNU/Linux'u, kötü amaçlı yazılımla enfekte olmuş bir Windows sistemine kuruyorsanız doğru tuşu bildiğinizden emin olun. USB sürücü takılıyken yanlışlıkla enfekte olmuş işletim sistemini açarsanız kötü amaçlı yazılımın türüne ve davranışına bağlı olarak USB sürücünün de enfekte olmasına sebep olabilirsiniz. Bu rehber; BIOS/UEFI'nize büyük bir risk almadan, güvenli bir şekilde girip giremeyeceğinizi kontrol etmek için enfekte sisteminizin hiçbir şekilde ağınıza erişemediğinden emin olmanızı ve **USB takılıyken sistemi açmadan önce** doğru tuşu denemenizi önerir.
>
> Bu yöntem önyükleyicisi / BIOS/UEFI'si enfekte olmamış yalnızca işletim sistemi enfekte olmuş cihazlar için genellikle güvenlidir.
>
> Sisteminiz enfekte değilse bu uyarıyı görmezden gelebilirsiniz.

Önyüklenebilir USB sürücünüz takılıyken güvenli bir şekilde BIOS/UEFI'nizi açtığınızda önyükleme menüsünden USB sürücünüzü seçerek devam edebilirsiniz. Yerini bulmakta zorlanıyorsanız bilgisayarınızın / anakartınızın üreticisinin kaynaklarına göz atmanız gerekebilir. Once you safely boot up to your BIOS/UEFI with your bootable USB drive inserted, you can proceed by selecting the USB drive from the boot menu. If you have trouble locating it, you may need to check the sources of the manifacturer of your computer / motherboard.


EndeavourOS, görsel arayüzlü bir yükleyici olan Calamares sistem yükleyicisi ile birlikte gelir.

EndeavourOS, güvenliği sağlayan ve tam bir Arch sistemine sahip olmada katkıda bulunan yalnızca şu paketler ile birlikte gelir: Firefox, Pacman, Yay, FirewallD, Pipewire, Nvidia installer, Dracut, Power-Profiles-Daemon.

Yükleme süreci boyunca çoğu seçenek tercih ettiğiniz dilde gayet anlaşılabilir olacak.


- Masaüstü ortamı seçme kısmında; bu rehber,  tamamlanmış bir masaüstü ortamı olması ve Windows gibi basit özelliklere, benzer hissiyat ve görünüşte bir uygulama ekosistemine sahip olması sebebiyle KDE Plasma'yı tercih etmenizi önerir. Aynı zamanda KDE Plasma, yüksek oranda özelleştirilebilirdir. Yine de istediğiniz masaüstü ortamını ya da pencere yöneticisini tercih etmekten çekinmeyin.

> **⚠ DİKKAT:** Yüklemenin **"Bölme"** kısmı sırasında sürücünüzün bölmelerini düzenlemeniz ve işletim sistemini kuracağınız bölmeyi seçmeniz istenecek.
>
> Windows ile Arch'ı çift-önyükleme yapmayı tercih ederseniz, Windows'un bölmesini tutarken yeni bir bölme oluşturabilirsiniz. Bunun için EndeavourOS'in websitesinde önerilen en düşük boyut 15 GB.
>
> However, if you prefer to completely wipe your drive (recommended for users who do not want to keep Windows on their system), you may delete all of the listed partitions, and install EndeavourOS on one of them.
>
> Please make sure to **backup any data from your system that you would like to keep** before proceeding.

You will also be presented with the choice to encrypt your disk. 

Disk encryption is an option which you can choose to completely encrypt your drive, which will lead you to enter passwords more than usual. If you want to protect your data from being accessed when your drive is stolen, you should enable this option. Especially recommended for laptop users.


When you're done with the disk partitioning, you may move on with the next steps and finish the installation.


## Booting into Arch
 
When your installation process is finished, you will be prompted to restart your system. Once you restart you should be greeted with your new Arch installation. If not, you may need to boot into your BIOS/UEFI and change the boot order priority, or check the boot menu settings.

> **NOTE:** EndeavourOS is esentially just Arch Linux with a graphical installation screen to make process simpler and a few packages pre-installed (that have been mentioned before), which you may choose to not install most of them during the installation screen. After the installation your system will be running Arch Linux. 

This guide mentions that the software that is used in this guide will be completely free and open-source.

For Nvidia users: If you would also like all of the software in your system to be free and open-source, you would want to use the open source Nouveau drivers instead of the closed-source proprietary Nvidia drivers. To achieve this, you can run `sudo nvidia-inst -n` in your preferred terminal and proceed. 

If you are not using an Nvidia graphics card and want to keep your system fully free and open-source, you may search for any packages that might be included in your system that are related to the proprietary Nvidia drivers as the latest EndeavourOS ISO releases ship with them, and remove them.

---

**Thank you for following this guide in your journey, and congratulations on your new Arch system!**
