
# 30 Günde React Native

React.js biliyorsunuz, React Native öğrenmek istiyor ama nereden başlayacağınızdan emin değil misiniz?

Bu seri size soft bir geçiş yapmanız için yardımcı olacak.

Önümüzdeki 30 gün boyunca React Native ile çalışmak için bilmeniz gereken tüm konuları ele alacağız. En başından Navigasyon, Animasyon ve hatta Yerel Modüller gibi konulara kadar.

Bu seride, en temelden başlıyoruz ve React Native'i kullanmaya başlamak için bilmeniz gereken her şeyi gözden geçiriyoruz. Eğer React Native'i öğrenmek istiyorsanız, burası başlamanız gereken yer!





### Youtube dersleri
* [30 Günde React Native Serisi ](https://www.youtube.com/playlist?list=PL4M5dHdsqIrEBa_rtjyizl1Qhci7lX1kf)


#### Eğer bu serinin yararlı olduğunu düşünüyorsanız;
GitHub'ta starlayıp, Youtube'da videoları beğenebilirsiniz. 
Ayrıca soru ve isteklerinizi video altına yorum olarak bırakabilirsiniz.


### Dersler
* [1. GÜN | Proje Kurulumu](./DERS_1.md)


### Derslere geçmeden önce biraz bilgi isterseniz

1. [React Native nedir?](#react-native-nedir)
2. [Neden React Native?](#neden-react-native)
3. [Ne öğreneceksiniz?](#başlarken)

    3.1. [React Native CLI](#react-native-cli-1)
    
    3.2. [EXPO](#react-native-cli-1)


## React Native nedir?

React Native, iOS ve Android için tek bir dil ve çerçevede mobil uygulama oluşturmamızı sağlar.

React Native'in 30 gününe hoş geldiniz! 30 günlük yolculuğumuzda her gün farklı bir React Native konusunu ele alacağız. Makalelerin çoğu bir önceki günün materyalleri üzerine inşa edilecek ve sonunda React Native kullanarak kendi mobil uygulamanızı oluşturmak için ihtiyacınız olan tüm kavramları ele almış olacağız.

Takipçilerin bileşenler gibi temel React kavramlarına zaten aşina olmalarını bekliyoruz. Eğer değilseniz, temel React dersleri hakkında youtube'da yada medium gibi platformlarda bir çok ders var önce onlara bir gözatmanızı tavsiye ederim. CSS gibi web kavramlarının da temel düzeyde bilmeniz gerekiyor.

Kapsanan materyallerden herhangi birini anlamak için mobil uygulama oluşturma deneyimine sahip olmanız gerekmez. Mobil geliştirme deneyiminiz varsa ve bir konuyu zaten biliyorsanız, ilerlemekten çekinmeyin.

#### Peki, React Native nedir?
React, kullanıcı arayüzleri oluşturmak için kullanılan bir JavaScript kütüphanesidir. React Native, React kullanarak yerel Android ve iOS uygulamaları oluşturmaya yönelik bir çerçevedir.

React Native'in (ve React'in) temel kavramlarından biri, kullanıcı arayüzlerini farklı bileşenler açısından temsil etmektir. İşte React Native'deki bir bileşen örneği:


```javascript import React, { Component } from 'react';
import { View, StyleSheet, Image, Button, Text } from 'react-native';

export default class IntroComponent extends Component {
  state = { count: 0 }

  render() {
    return (
      <View style={styles.container}>
        <Image style={styles.image} source={require('./assets/logo.png')} />
        <Button
          title={"Click me!"} 
          color={"#D70089"} 
          onPress={() => {
            this.setState({ count: this.state.count + 1 })
          }} 
        />
        <Text style={styles.text}>
          Clicked {this.state.count} times
        </Text>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
    backgroundColor: 'black',
  },
  image: {
    width: 200,
    height: 200,
    marginBottom: 20,
  },
  text: {
    marginTop: 10,
    color: 'rgba(255,255,255,0.5)'
  }
});

```


Bu bileşen, IntroComponent, içinde 3 küçük bileşen içerir: bir Image bileşeni, bir Buton ve bir Text etiketi. Butona bastığımızda etiket güncellenir (hadi, deneyin). React Native ile çok şey yapmak için oldukça az kod gerekir! Bu bileşenlerin her birinin nasıl çalıştığını bu haftanın ilerleyen günlerinde inceleyeceğiz.

React Native'deki "native" terimi, uygulamamızın kullanıcı arayüzünün altta yatan platformun yerleşik UI öğeleriyle oluşturulduğu anlamına gelir. Web'de arayüzler HTML öğeleriyle oluşturulur - HTML öğeleri web tarayıcısı tarafından sağlandığı için web platformuna özgü olarak kabul edilir. Benzer şekilde, Apple ve Google mobil işletim sistemleri için yerleşik bir UI bileşenleri seti sağlar. React Native, JavaScript ve React kullanarak bu arayüzleri oluşturmamıza yardımcı olur.
## Neden React Native?

Birçok geliştirici, iOS için Swift/Objective-C ve Android için Java/Kotlin gibi platform destekli dilleri kullanarak yerel mobil uygulamalar yazmaktadır. React Native, her iki platform için farklı dillerde yazmak yerine, uygulamanızın bazı bölümlerini (veya tamamını) tek bir dilde (JavaScript) ve çerçevede (React) oluşturmanıza olanak tanır. Bu da hem iOS hem de Android'i desteklemek için gereken tüm farklı dillere, araç zincirlerine ve geliştirme ortamlarına aşina olma yükünü en aza indirir. Başka bir deyişle, yerel mobil uygulamalar oluştururken web uygulamaları oluştururken edindiğiniz React ve JavaScript bilgilerini yeniden kullanabilirsiniz.

React Native, iOS ve Android arasında kod paylaşımını kolaylaştırmanın yanı sıra, geliştiricilerin bir platforma özgü bileşenler veya işlevler oluşturmasına da olanak tanır. Yerel bileşenler ve API'ler yazabilir ve JavaScript arayüzüne bir "köprü" tanımlayabiliriz. Bu esneklik, React Native'i hem yepyeni projeler hem de mevcut yerel uygulamalar için kullanabileceğimiz anlamına geliyor.

### React Native'in hibrit uygulama platformlarından farkı nedir?

Ionic ve Phonegap gibi hibrit uygulama platformları da web teknolojilerini kullanarak mobil uygulamalar oluşturmayı mümkün kılıyor. Örneğin Ionic, bileşenler şeklinde (isteğe bağlı olarak React kullanarak bile) UI yapı taşları oluşturmamıza zaten izin veriyor. Ancak bu araçlar React Native'den farklıdır çünkü kullanıcı arayüzünü sunmak için WebView'lere güvenirler. WebView, yerel bir uygulamaya gömülü bir web sayfasıdır. Sonuç olarak kullanıcı arayüzü genellikle tipik bir yerel deneyim gibi hissettirmez. Kamera rulosu gibi belirli cihaz API'lerine hala erişilebilmesine rağmen aslında çok az yerel kod kullanılır. Öte yandan React Native, yerel UI API'leri için bir dizi JavaScript bağlamasıdır. Başka bir deyişle, bir React Native uygulamasındaki kullanıcı arayüzü tamamen yereldir.

Yarın, ilk projemizi kurarak React Native uygulamalarını önyüklemenin ne kadar hızlı olduğunu göstereceğiz.
## Başlarken

Bu makalenin sonunda, gerçek bir cihaz veya simülatör üzerinde çalışan bir uygulamaya sahip olacağız!

Farklı React Native kavramlarını ele almaya başlamadan önce, yepyeni bir uygulamayı nasıl çalıştıracağımızı bilmemiz gerekecek. Bu, gerekli bağımlılıkları yüklemeyi ve çalışan bir geliştirme ortamı kurmayı içerir.

React Native'de bir uygulama oluşturmaya başlamanın iki yolu vardır:
##### React Native CLI
##### Expo


#### Her iki durumda da uygulamamız için aynı React Native kodunu yazabiliriz. Ancak, her iki yaklaşımın iş akışları arasında farklılıklar vardır. Hadi içeri dalalım!

### React Native CLI

React Native CLI, React Native uygulamaları oluşturmak ve çalıştırmak için kullanılan bir komut satırı arayüzüdür. CLI'yi kullanmak, bir uygulamayı çalıştırmak ve oluşturmak için iOS (Xcode) ve Android (Android Studio) için özel geliştirme ortamlarının kurulmasını ve ayarlanmasını gerektirir.

### EXPO 

Expo, React Native uygulamaları oluşturma ve dağıtma sürecini basitleştirmek için bir dizi araç ve hizmet sağlayan bir platformdur. React için React Create App'a benzer şekilde Expo, herhangi bir derleme yapılandırması olmadan yeni bir React Native uygulaması başlatmanıza olanak tanır.


### Hangi seçeneği kullanmalıyım?

React Native, herhangi bir yerel kod yazmadan herkesin her iki mobil platform için de derleme yapmasına izin verse de, CLI herhangi bir uygulamayı derlemek ve dağıtmak için özel geliştirme ortamlarının (iOS için Xcode ve Android için Android Studio) kullanılmasını gerektirir.

Öte yandan Expo, tüm derleme süreciyle ilgilenen eksiksiz bir yönetilen iş akışı sağlar. Bu, yalnızca birkaç farklı IDE'yi indirmek ve yapılandırmak zorunda kalmadan uygulama oluşturmayı ve yayınlamayı kolaylaştırmakla kalmaz, aynı zamanda geliştiricilerin bir Mac bilgisayara sahip olmadan iOS uygulamaları oluşturmasına da olanak tanır.

Eskiden Expo ile geliştirilen projelerde bazı özel paketleri kullanmak yada yeni paketler oluşturmak mümkün değildi bu yüzden React Native CLI tercih ediliyordu. Fakat SDK 48 ile bunu büyük ölçüde aşılmış durumda. Expo ile başlayıp, gerektiği aşamada "expo prebuild" ile Native moda geçebiliyorsunuz. Tabi bunu yapsanız bile bazı farklılıklar oluyor, projenize göre tercih edebilirsiniz.

> __Note__
💡 Belgeler, Expo'nun neden her uygulama için en iyi seçenek olmayabileceğinin diğer nedenleriyle birlikte bunu açıklamaktadır.
>

Hangi seçeneği kullanacağınıza karar vermek, yepyeni bir mobil uygulama oluşturmayı mı yoksa React Native'i mevcut bir uygulamaya entegre etmeyi mi planladığınıza bağlı olabilir. Emin değilseniz, aşağıdakileri öneririz:

```
• Sıfırdan yeni bir React Native uygulaması oluşturuyorsanız, Expo'nun yönetilen iş akışını kullanın. Gelecekte bir noktada platform tarafından sağlanmayan bir şeye ihtiyacınız olursa, her zaman çıkarabilirsiniz.
• React Native'i mevcut bir iOS veya Android uygulamasına entegre ediyorsanız, React Native CLI kullanın çünkü Expo, özel yerel kodu çıkarmak veya "çıplak" iş akışını kullanmaksızın köprülemek için kullanılamaz (daha fazla ayrıntı aşağıda).
```

"Native Modules" hariç bu serideki her makale Expo'ya dayanacak çünkü her bölüm için yeni uygulamalar oluşturacağız. Hadi platforma nasıl başlayacağımızı keşfedelim!
