
# 1. GÜN | Proje Kurulumu

## Expo ile yeni bir proje oluşturmak

İlk olarak, terminal'inizi açın. Eğer npm kullanıyorsanız, Node v10 veya üst sürümünün kurulu olduğundan emin olun. Ardından 
#### Expo CLI'yi global olarak kuralım:

```terminal
npm install -g expo-cli 
```
yada
```terminal
yarn global add expo-cli 
```

CLI yüklendikten sonra projemizi oluşturuyoruz, "Example" adında yeni bir React Native uygulaması oluşturalım:

#### Projemizi oluşturalım:

```terminal
expo init Example
```

Şimdi uygulama için bir başlangıç şablonu seçmek üzere bir istem görmeliyiz, şuna benzer bir ekran:

```terminal
? Choose a template: (Use arrow keys)
----- Managed workflow ----
> blank
  blank (TypeScript)
  tabs
----- Bare workflow ----
minimal
minimal (TypeScript)
```

Expo, uygulamanızı başlatmak için hem yönetilen hem de çıplak iş akışları için tamamen minimal bir kurulum [1] ve bir TypeScript seçeneği gibi birkaç seçenek sunar. Sekmeler şablonu, react-navigation kütüphanesini kullanarak temel navigasyonu ayarlar. Navigasyon kavramını bu serinin ilerleyen bölümlerinde inceleyeceğiz.

Şimdilik boş seçeneği seçin. Başka bir istem, uygulamanız için ana ekranda görünecek bir ad seçmenizi isteyecektir. Ben şimdilik Example yazıyorum, bunu daha sonra değiştirebiliriz.

Son olarak, npm kullanıyorsanız yarn'ı kullanmanızı isteyen bir istem göreceksiniz. CLI daha sonra gerekli tüm dosyaları indirmek için birkaç dakika sürecektir. Bu işlem tamamlandığında, yeni oluşturulan dizine gidip projeyi başlatacağız.

#### Projeyi Başlatın:

```terminal
cd Example
yarn start
```

Geliştirme sunucunuz başladı ve hazırız.

Artık çalışan yerel bir geliştirme sunucumuz olduğuna göre, tek yapmamız gereken uygulamayı görüntülemek! Expo, geliştiricilerin React Native uygulamasını gerçek cihazımızda veya simülatörümüzde önizlemesine olanak tanıyan bir iOS ve Android uygulaması sağlar.

Uygulamayı görüntülemek için 2 ayrı yönteminiz var, bilgisayarınızla aynı ağa bağlı olduğunuz bir fiziksel cihaz yada bilgisayarınıza kurabileceğiniz simulatörler.

Windows kullanıyorsanız, IOS simulatör'ü bilgisayarınıza kuramayacaksınız o yüzden fiziksel bir iPhone kullanmalısınız.

Mac kullanıyorsanız, bilgisayarınıza XCode kurduğunuzdan emin olun.

#### Fiziksel bir Android cihazınız varsa:

Google Play'den Expo uygulamasını yükleyin,
QR kodunu tara öğesini seçin ve terminaldeki QR kodunu tarayın,

#### Fiziksel bir iOS cihazınız varsa:

App Store'dan Expo istemcisini yükleyin
Kamera uygulaması ile QR kodunu tarayın


#### Eğer bir simülatörde çalıştırmak istiyorsanız:

Android emülatöründe çalıştırmak için a'ya veya iOS simülatöründe çalıştırmak için i'ye basın

Ve şimdi uygulamanın doğrudan cep telefonunuzda çalıştığını görmelisiniz:

Her şeyin beklendiği gibi çalıştığından emin olmak için, App.js dosyasında bir kod satırını değiştirin ve kaydedin. Değişikliğiniz otomatik olarak cihazda görünmeli.

React Native'e nasıl başlayacağımızı öğrendiğimize göre, yarın ilk bileşenimizi yazacağız!

#### Notlar
[1]: Expo yönetimli bir projeyi React Native CLI'ya geçirmek mümkündür. Yani EXPO projesi kursanız bile, ilerleyen süreçte React Native CLI'ya geçmek isterseniz şunu yapmanız yeterli

```terminal
npx expo prebuild
```
