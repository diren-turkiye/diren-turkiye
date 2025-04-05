# İçindekiler
- [SANSÜRLE MÜCADELE REHBERİ](#sans%C3%BCrle-m%C3%BCcadele-rehberi%CC%87)
  * [VPN nedir? Ne işe yarar?](#vpn-nedir-ne-işe-yarar)
  * [Önerilen VPNler listesi](#önerilen-vpnler-listesi)
  * [DNS nedir?](#dns-nedir)
    + [DNS over HTTPS / DNS over TLS](#dns-over-https--dns-over-tls)
      - [Android](#android)
      - [iOS](#ios)
      - [Windows 11](#windows-11)
      - [macOS (Big Sur ve sonrası)](#macos-big-sur-ve-sonrası)
  * [Tor](#tor)
- [GÜVENLİ İLETİŞİM REHBERİ](#g%C3%BCvenli%CC%87-i%CC%87leti%CC%87%C5%9Fi%CC%87m-rehberi%CC%87)
  * [Uçtan uca şifreleme nedir?](#uçtan-uca-şifreleme-nedir)
  * [Hangi mesajlaşma sistemlerini veya uygulamalarını kullanmaktan kaçınmalıyım?](#hangi-mesajlaşma-sistemlerini-veya-uygulamalarını-kullanmaktan-kaçınmalıyım)
  * [Hangi mesajlaşma uygulamalarını kullanmalıyım?](#hangi-mesajlaşma-uygulamalarını-kullanmalıyım)
    + [Peki ya WhatsApp?](#peki-ya-whatsapp)

# SANSÜRLE MÜCADELE REHBERİ

## VPN nedir? Ne işe yarar?

Normalde bir internet servis sağlayıcı (İSS), internet trafiğinizi. HTTPS gibi şifreleme protokolleri internette yaygın olarak kullanıldığı için ne yazdığınız veya okuduğunuzu tam olarak göremeseler de eriştiğiniz siteler hakkında bir fikir edinebilirler. Bu şekilde, devletler sansür uygulamaktadır.

VPN kullanarak, ilk olarak başka bir ülkedeki bir sunucuya, ardından bağlanmak istediğiniz yere bağlanabilirsiniz. Bu şekilde İSS'niz yalnızca bir VPN'e bağlı olduğunuzu görür ve içeriği hakkında bilgi edinemez. Bu şekilde devletler inernete erişiminizi sansürleyemez.

## Önerilen VPNler listesi

1) **ProtonVPN (ücretsiz):** [Android: Google Play Store](https://play.google.com/store/apps/details?id=ch.protonvpn.android&hl=tr), [iOS: App Store](https://apps.apple.com/tr/app/proton-vpn-fast-secure/id1437005085), [macOS](https://github.com/ProtonVPN/ios-mac-app/releases), [Windows](https://github.com/ProtonVPN/win-app/releases)

- Eğer uygulama Google Play Store'dan kaldırılırsa Proton VPN'in [GitHub reposundan](https://github.com/ProtonVPN/android-app/releases) da indirilebilir. 
- Proton VPN'i kullanırken, ilk olarak "Connect" tuşuna basarak bağlanmayı deneyin. Eğer bu başarısız olursa, Settings -> Protocol -> Stealth seçeneğini seçtikten sonra bağlanmayı deneyin. Bu özellik, VPN bağlantınızı gizlemeye çalışacaktır.

- Eğer bu da çalışmaz ise, Settings -> Advanced Settings -> Alternative routing'i açıp deneyin.

2) **Mullvad (ücretli):** [Android: Google Play Store](https://play.google.com/store/apps/details?id=net.mullvad.mullvadvpn), [Android: F-Droid](https://f-droid.org/tr/packages/net.mullvad.mullvadvpn/), [iOS: App Store](https://apps.apple.com/tr/app/mullvad-vpn/id1488466513), [macOS](https://github.com/mullvad/mullvadvpn-app/releases/download/2025.4/MullvadVPN-2025.4.exe),  [Windows](https://github.com/mullvad/mullvadvpn-app/releases/download/2025.4/MullvadVPN-2025.4.exe)

- Eğer bağlantı kuramazsanız, sağ üstteki dişli çark ikonuna tıklayıp ayarlara girin ve "VPN Settings" -> "WireGuard obfuscation" altından "UDP-over-TCP" seçeneğini seçin. Bu da başarısız olursa aynı menü altındaki "Shadowsocks" seçeneğini kullanmayı deneyebilirsiniz.

## DNS nedir?

DNS servisleri, bir web sitesini ziyaret etmek istediğinizde, o alan adını IP adresine dönüştüren servislerdir. Örneğin `wikipedia.org`'u ziyaret etmek istediğinizde size `185.15.58.224` IP adresini verecektir.

DNS servisleri, genelde sisteminizin varsayılan ayarlarında şifresiz olarak çalışacaktır. Bu demektir ki, İSS'niz sizin erişmek istediğiniz siteler için yaptğınız DNS isteklerini görebilecek ve bu şekilde sansür veya gözetim uygulayabilecektir.

### DNS over HTTPS / DNS over TLS

DNS over HTTP veya DNS over TLS gibi şifrelenmiş DNS protokolleri kullanarak DNS isteklerinin şifresiz gönderilmesi problemi çözülebilir, bu şekilde sansür ile gözetim daha zor bir hale getirilebilir.

**Not: Şifreli DNS servisleri kullanmak, VPNlerin aksine eriştiğiniz IP adresini İSS'nizden saklamayacaktır. Girilen sitelerin gizli kalması için VPNlerin yerine KULLANILMAMALIDIR. Sansür ve gözetimi zorlaştırmak için tek başına veya VPN'e ek olarak kullanımını tavsiye ediyoruz.**

**Geliştirici notu: Bu tarz yazılımların geliştirilmesi sürecinde Cloudflare'in "Proxied" modunda kullanıldığı A kayıtları, "Full" SSL modu ile orjinal sunucu adresini gizli tutabilir ve ECH(Encrypted Client Hello) özelliğinden faydalanarak DoH kullanıcılarının sansürden etkilenmesini oldukça zorlaştırabilirsiniz.**

#### Android

Eğer telefoununuz Android 9 ve üzeri ise aşağıdaki adımları izleyerek DNS over TLS'i aktif hale getirebilirsiniz:

1. Ayarlar -> Ağ ve İnternet -> Gelişmiş -> Gizli DNS'e tıklayın.
1. "Gizli DNS sağlayıcının ana makine adı" seçeneğini etkin hale getirin ve aşağıdaki alan adlarından birini girin:
    - `dns.quad9.net`
    - `dns.mullvad.net`
    - `one.one.one.one`

#### iOS

1. [Quad9 web sitesinden](https://docs.quad9.net/Setup_Guides/iOS/iOS_14_and_later_%28Encrypted%29/) DNS profilini indirin. Bunu "Download Profile" bölümü altındaki "Recommended: HTTPS (.9)" tuşuna basarak yapabilirsiniz.
1. Telefonunuzdaki Dosyalar uygulamasına gidin, ekranın en alt kısmındaki "Göz At" tuşuna tıklayın ve İndirilenler klasörüne girin. Bu klasörde, indirdiğiniz "Quad9...mobileconfig" dosyasına tıklayın.
1. Ayarlar -> Profil İndirildi seçeneğine tıklayın -> Sağ üst köşedeki yükle tuşuna basın.


#### Windows 11

1. Başlat düğmesine sağ tıklayın ve Ayarlar butonunu seçin -> Soldaki menüden "Ağ ve internet"'i seçin -> Eğer kablosuz internet ile bağlıysanız "Wi-Fi" seçeneğine, kablolu internet ile bağlıysanız "Ethernet" seçeneğine tıklayın.
1. “DNS sunucusu ataması”nın yanındaki ”Düzenle” tuşuna tıklayın -> Menüden "El ile girilen" seçeneğini seçin -> IPv4'ü açın ve aşağıdaki değişiklikleri yapın.

    - Tercih edilen DNS: `9.9.9.9` (Eğer olmazsa: `194.242.2.2`)
    - HTTPS üzerinden DNS: Açık (otomatik şablon)
    - Altetnatif DNS: `149.112.112.112` (Eğer olmazsa: `1.1.1.1`)
    - HTTP üzerinden DNS: Açık (otomatik şablo)

#### macOS (Big Sur ve sonrası)

1. [Quad9 web sitesinden](https://docs.quad9.net/Setup_Guides/MacOS/Big_Sur_and_later_%28Encrypted%29/) DNS profilini indirin. Bunu "Download Profile" bölümü altındaki "Recommended: HTTPS (.9)" tuşuna basarak yapabilirsiniz.
1. İndirilenler klasörüne gidin, ve indirdiğiniz "Quad9...mobileconfig" dosyasına tıklayın.
1. Sistem Tercihleri -> Profiller'e tıklayın > Sağ üst köşedeki yükle tuşuna basın.

## Tor

**Uyarı: Eğer Tor kullanacaksanız köprüleri etkinleştirdiğinizden emin olun. Aksi takdirde İSS'niz, Tor kullandığınızı kolayca tespit edebilir. Köprü kullansanız dahi, İSS'niz çeşitli trafik analizi teknikleriyle Tor kullandığınızı tespit edebilir ve bu ekstra dikkat çekebilir.**

Köprüleri etkinleştirmek için aşağıdaki adımları takip edin:

Tor Browser: Tor Browser'ı açtıktan sonra Bağlantıyı yapılandır tuşuna basın ve "Köprüler kullanılsın" seçeneğini etkinleştirin. Eğer varsayılan köprüler çalışmıyorsa "Köprüler isteyin" tuşu ile veya [Tor'un Telegram botuyla](https://t.me/GetBridgesBot) yeni köprü adresleri alabilirsiniz.

Orbot: Orbot'u açtıktan sonra "Nasil bağlanılacağını seç" tuşuna basın ve "Tor'dan köprü (Obfs4)" seçeneğini seçip "Sonraki" tuşuna girin ve ekrandaki karakterleri girdikten sonra Bağlan tuşuna basın.

- Tor Browser:  [Android: Google Play Store](https://play.google.com/store/apps/details?id=org.torproject.torbrowser&hl=tr), [Windows, macOS, Linux, Android: Tor web sitesi](https://www.torproject.org/tr/download/)
- Orbot: [Android: Google Play Store](https://play.google.com/store/apps/details?id=org.torproject.android&hl=tr), [iOS, macOS: App Store](https://apps.apple.com/us/app/orbot/id1609461599?platform=iphone)

Tor Browser, trafiğinizi Tor ağından geçiren bir tarayıcıyken Orbot, cihazınızın tüm trafiğini Tor üzerinden geçirir. Bu demektir ki Orbot kullandığınızda Twitter, WhatsApp vb. gibi uygulamaları yasaklı olsa dahi kullanabilirsiniz.

Eğer VPN servislerine erişmekte zorluk çekiyorsanız Tor ağı aracılığıyla sansürü aşabilirsiniz. 

Tor üzerinden internet bağlantısı kurduğunuzda trafiğiniz, konumunuzu ve etkinliğinizi sizi izlemeye çalışanlardan gizleyen ve dünya çapındaki gönüllüler tarafından işletilen bir aktarıcı ağı üzerinden geçirilir.

# GÜVENLİ İLETİŞİM REHBERİ

**Uyarı: Android ve iOS, varsayılan olarak 2G kullanımına izin vermektedir. 2G, içerisinde birçok zafiyet bulunan eski bir protokol olduğu için bağlantınız 2G'ye düşürülüp sonrasında çeşitli zafiyetler istismar edilerek hedef alınabilirsiniz. Bu sebeple telefonunuzda 2G kullanımını kapamanızı şiddetle tavsiye ediyoruz.**

- **Android:** Ayarlar -> Ağ ve internet -> SIM'ler -> Kullandığınız SIM kartını veya profilini seçin -> "2G'ye izin ver" seçeneğini devre dışı bırakın. 
- **iOS :** iOS, 2G kullanımının devre dışı bırakılmasına doğrudan izin vermese de kilit modunu etkinleştirerek 2G kullanımını engelleyebilirsiniz. Kilit modu, telefonunuzda hedef alınabilecek birçok özelliği kısıtlayarak telefon güvenliğini arttıran bir özelliktir. Kilit modu, Ayarlar -> Gizlilik ve Güvenlik -> Kilit Modu menüsüne tıklandıktan sonra "Kilit Modu'nu Aç" seçeneği seçilerek açılabilir.

## Uçtan uca şifreleme nedir?

Uçtan uca şifreleme, yalnızca birbiriyle iletişim kuran kullanıcıların katılabildiği güvenli bir iletişim yöntemidir. Uygulama yöneticileri, internet servis sağlayıcıları, telekom sağlayıcıları, veya kötü niyetli aktörler de dahil olmak üzere hiç kimse mesajları okumak veya göndermek için gereken kriptografik anahtarlara erişemez. **Uçtan uca şifreleme kullanılmayan bir mesajlaşma uygulaması kullandığınızda mesajlarınızı uygulama yöneticileri okuyabilir veya devlet otoritelerinin talebi üzerine teslim edebilir.**

## Hangi mesajlaşma sistemlerini veya uygulamalarını kullanmaktan kaçınmalıyım?

1) **SMS ve normal arama:** Herhangi bir uçtan uca şifreleme bulunmamaktadır. Otoritelerin dinleme yapması için mekanizmalar halihazırda mevcuttur (Lawful Intercept). **Bu kanallar üzerinden yaptığınız arama ve mesajlaşmalar çeşitli kurumlar tarafından kayıt altına alınabilir ve görüntülenebilir.** Buna ek olarak telekomünikasyon ağları, farklı aktörler tarafından aktif olarak hedef alınmaktadır. 

2) **Telegram**: Güvenli bir mesajlaşma uygulaması olarak tanıtılıp pazarlansa da aslında Telegram güvenli iletişime uygun bir uygulama değildir. **Uçtan uca şifreleme varsayılan olarak kapalıdır** ve yalnızca bir "Gizli sohbet" başlatırsanız aktif hale gelir. Buna ek olarak, **Telegram'da gruplarda uçtan uca şifreleme olanağı bulunmamaktadır.** Eğer Telegram kullanmak zorundaysanız, güvenli bir mesajlaşma uygulamasından ziyade hassas konuların konuşulmadığı bir sosyal medya uygulaması olarak kullanmalısınız.

## Hangi mesajlaşma uygulamalarını kullanmalıyım?

**Özet:** 

- WhatsApp ve Telegram yerine Signal
- Büyük kanalların olduğu topluluklar için Discord yerine Element 
- İnternet erişiminin ciddi anlamda kısıtlandığı veya devre dışı bırakıldığı durumlar için Briar kullanmanızı öneriyoruz.

1) **Signal:**  [Android: Google Play Store](https://play.google.com/store/apps/details?id=org.thoughtcrime.securesms&hl=tr), [iOS: App Store](https://apps.apple.com/tr/app/signal-private-messenger/id874139669), [macOS, Windows, Linux](https://signal.org/tr/download/)

- Açık kaynaklı Signal protokolü ile desteklenen Signal uygulaması, mesajlarınızı ve aramalarınızı varsayılan olarak uçtan uca şifreleyerek güvende tutar. Buna ek olarak Signal, kar amacı gütmeyen bağımsız bir kuruluştur. Signal, güvenlik uzmanlarının en çok önerdiği güvenli mesajlaşma uygulamalarından biridir.
- Signal hesabı açmak için telefon numarası gerekse de kullanıcı bir kullanıcı adı oluşturarak diğer kişilerle telefon numaranızı paylaşmadan konuşabilirsiniz. Bunu yapmak için Ayarlar -> Profil (Telefon numaranızın yazdığı kısım) -> @ işareti yanındaki kullanıcı adı seçeneğine tıkllayın ve "Kullanıcı adını düzenle" seçeneği ile bir kullanıcı adı oluşturun.
- Eğer rehberinizdeki kişilerin sizi telefon numaranızdan bulmasını istemiyorsanız Ayarlar -> Gizlilik -> Telefon numarası kısmından "Kimler beni numaram ile bulabilir?" seçeneğini "Hiç kimse" olarak seçebilirsiniz.
- Eğer telefon konuşması gerçekleştirdiğiniz kişiler güvenilir değilse ve IP adresinizi görmesini istemiyorsanız Ayarlar -> Gizlilik -> Gelişmiş -> "Aramaları her zaman aktar" seçeneğini aktif hale getirebilirsiniz.
- Eğer Signal Türkiye'de yasaklanırsa, aynı menüdeki "Sansür atlatma" seçeneğini aktif hale getirip Signal'e bağlanmayı deneyebilirsiniz.

2) **Matrix (Element):** [Android: Google Play Store](https://play.google.com/store/apps/details?id=im.vector.app&hl=tr), [iOS: App Store](https://apps.apple.com/tr/app/element-messenger/id1083446067), [Bilgisayar için tarayıcı uygulaması](https://app.element.io/)

- Element uygulaması, güvenli anlık mesajlaşma protokolü Matrix'in en büyük istemcisidir. Element, mesajlarınızı ve konuşmalarınızı varsayılan olarak uçtan uca şifreleyerek güvende tutar. Matrix'in varsayılan sunucusu olan matrix.org'u kullanabilirsiniz. Eğer daha gelişmiş bir kullanıcıysanız Matrix, kendi sunucunuzu kurmanızı ve verinizi oradan aktarmanıza da olanak sağlar.
- Element, Signal'e kıyasla daha fazla topluluk özelliği sağlar. Farklı odalar oluşturabilir, yüzlerce/binlerce üyenin aktif ve düzenli bir şekilde iletişimde kalmasını sağlayabilirsiniz. Eğer amacınız Discord'a yakın bir işlev elde etmekse Signal'e kıyasla daha iyi bir seçim olacaktır.

3) **Briar:** [Android: Google Play Store](https://play.google.com/store/apps/details?id=org.briarproject.briar.android&hl=tr), [Android: F-Droid](https://f-droid.org/tr/packages/org.briarproject.briar.android/)

- Briar, merkezi bir sunucu kullanmak yerine diğer kullanıcıların cihazlarına Tor üzerinden bağlanarak mesjalaşmayı sağlayan bir uygulamadır. Mesajlarınız varsayılan olarak uçtan uca şifrelenerek güvende tutulur.
- İnternet üzerinden kullanıma ek olarak, internet bağlantısının kesildiği veya sansürlendiği durumlarda Briar, mesajların Bluetooth veya Wi-Fi üzerinden senkronize edilmesine olanak sağlar. Birçok kişinin Briar kullandığı bir durumda birbiriyle mesajlaşmak isteyen
- Briar, iOS kullanan cihazlarda desteklenmemektedir.

### Peki ya WhatsApp?

Ülkemizde en aktif kullanılan mesajlaşma uygulaması olan WhatsApp, ne çok iyi bir seçenek ne de çok kötü. WhatsApp, şu anda mesajlarınızı Signal protokolü ile uçtan uca şifrelese de üstverinizi, yani kiminle ne zaman mesajlaştığınızı veya konuştuğunuzun verisini toplar. Bu veri, devletlerin talebi üzerine verilebilir.

Buna ek olarak, WhatsApp açık kaynak kodlu bir uygulama olmadığı için uygulamanın tamamen nasıl çalıştığına dair detaylara sahip değiliz. Bu, WhatsApp'ta bir arka kapı olması ihtimalini arttıran bir durumdur.

Eğer WhatsApp kullanıyorsanız, mesajlarınızı bulut servisine yedeklemediğinizden, yedekliyorsanız yedeklerde uçtan uca şifrelemeyi aktive ettiğinizden emin olun. Devletler, Google ve Apple'dan şifrelenmemiş mesajlaşma yedeklerinizi isteyerek konuşmalarınızı ele geçirebilirler. Bunu aşağıdaki adımları takip ederek yapabilirsiniz.

**Android:** Sağ üstteki üç noktaya tıklayın ve "Ayarlar" seçeneğine tıklayın

**iOS:** Sağ alttaki ayarlar bölümüne tıklayın ve aşağıdaki adımları takip edin:

Sohbetler -> Sohbet yedeği -> Uçtan uca şifrelenmiş yedekleme -> "Aç" seçeneğini seçin.
Sohbet yedeği menüsünden Google veya iCloud hesabınıza yedekleme yapıp yapmadığınızı kontrol edebilir ve bu özelliği devre dışı bırakabilirsiniz.

**Bir sonraki rehberlerimiz için adresimizi takipte kalın!**
