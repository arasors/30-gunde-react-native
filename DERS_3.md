# 3. GÜN | Stil Tanımlamaları

Uygulamalarımızın harika görünmesini sağlamak için stilleri kullanırız. Stiller, bileşenlerimizin arka plan rengi gibi görsel özelliklerinin yanı sıra düzenlerini, yani ekrandaki konumlarını ve boyutlarını yapılandırmamızı sağlar.

React Native stilleri CSS'i temel alır: stil özellik adlarının ve değerlerinin çoğu React.js'de ve React Native'de aynıdır. Bu, web uygulamaları oluştururken edindiğimiz mevcut bilgilerin çoğunu yeniden kullanabileceğimiz için kullanışlıdır.

Bununla birlikte, CSS ve React Native stilleri arasında bazı önemli farklar vardır. En büyük fark, CSS dosyalarının olmamasıdır!

Fakat bunun için öğrenmemiz gereken özel bir dil ya da söz dizimi yok; tüm stillerimiz JavaScript kullanılarak tanımlanıyor.

Bileşen stillerini tanımlamanın iki yaygın yolu vardır:
* [Satır içi stiller]
* [StyleSheets]
  Bu iki yaklaşımı da inceleyerek başlayacağız.

### Satır içi stiller
Yerleşik React Native bileşenlerinin çoğu (View, Text, Image, vb.) bir prop olarak bir stil nesnesini kabul eder. Bu şekilde stil oluşturma web için React'e benzer: anahtarlar camel-cased CSS özellik adlarıdır ve değerler tipik CSS değerleridir. Örneğin, bir View'in backgroundColor'ını style prop olarak { backgroundColor: "#0088FF" } geçirerek yapılandırabiliriz.


Aşağıdaki örnekte, bir satır içi stil nesnesi kullanarak bir Görünümün backgroundColor, genişlik ve yüksekliğini ayarlıyoruz:
```javascript
import React from 'react';
import { View } from 'react-native';

export default () => (
    <View style={{ width: 200, height: 200, backgroundColor: 'skyblue' }} />
);
```
Satır içi stiller, oluşturma kodumuzla birlikte konumlandırıldıkları için prototip oluşturma açısından kullanışlıdır. Ayrıca, render fonksiyonu çağrılana kadar prop'larımızın değerlerini bilmediğimiz için dinamik stilleri, örneğin prop'lara dayalı stilleri tanımlarken satır içi stilleri kullanmamız gerekir.

Ancak satır içi stiller birkaç satırdan çok fazla koda dönüşebilir ve bu da render yöntemimizi karmaşıklaştırarak kodumuzu takip etmeyi zorlaştırır. Bunları başka bir yere taşıyabilseydik daha kullanışlı olmaz mıydı? İşte StyleSheets burada devreye giriyor.



### StyleSheets
StyleSheet API, stillerimizi bileşen tanımımızın dışında tanımlamak için bize tutarlı bir yol sunar. Ayrıca StyleSheet, satır içi stillerle mümkün olmayan önemli performans optimizasyonları içerir. Bu nedenlerden dolayı, satır içi stiller yerine mümkün olan her yerde genellikle StyleSheet API'sini kullanmalıyız.

İşte StyleSheets kullanarak yukarıdaki ile aynı örnek:
```javascript
import React from 'react';
import { View, StyleSheet } from 'react-native';

export default () => <View style={styles.myStyle} />;

const styles = StyleSheet.create({
    myStyle: {
        width: 200,
        height: 200,
        backgroundColor: 'skyblue',
    },
});
```

StyleSheet.create'i iç içe stil nesneleri içeren üst düzey bir nesne ile çağırırız. StyleSheet daha sonra stillerimizi optimize edecek ve bize geri döndürecektir. Üst düzey nesnenin anahtarları isteğe bağlıdır, ancak optimize edilmiş stillerimizin adlarını belirleyecektir. Daha sonra render metodumuzda bunlara ismiyle referans verebiliriz, örneğin styles.myStyle.

Bir React Native StyleSheet, sınıf adları içeren bir CSS stil sayfasına benzer - bunları bileşen kodumuzdan ayrı olarak tanımlarız ve bu stili istediğimiz her yerde aynı tanımı yeniden kullanabiliriz.

Bazen bir bileşene aynı anda birden fazla stil uygulamak isteyebiliriz (CSS stillerindeki "basamaklandırmaya" benzer) ve neyse ki React Native bunu yapmak için kolay bir yol sağlar.

#### Çoklu stil uygulama

İki Text bileşeni oluşturmak istediğimizi varsayalım. Biri "standart" bir metin stili kullanmalı, diğeri ise "standart" metin stiline ek bir stil almalı.

Web'de, muhtemelen ek stil tanımayacağımız metin bileşenimize iki sınıf adı iletirdik: biri standart stil için diğeri ekstra stil için. Mesela:
```html
<div>
    <span class="standard-text fancyText">Başlık</span>
    <span class="standard-text">Açıklama</span>
</div>
```

React Native, aynı şeyi gerçekleştirmek için bir bileşene bir array dizisi olarak stil iletmemize izin verir.

İşte iki Text bileşeni içeren örneğimiz:
#### Çoklu stil örneği
```javascript
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

export default () => (
    <View style={styles.myStyle}>
        <Text style={[styles.standardText, styles.fancyText]}>Açıklama</Text>
        <Text style={styles.standardText}>Başlık</Text>
    </View>
);

const styles = StyleSheet.create({
    myStyle: {
        width: 200,
        height: 200,
        backgroundColor: 'skyblue',
    },
    standardText: {
        fontSize: 24,
        color: '#333',
    },
    fancyText: {
        fontStyle: 'italic',
        color: 'rgb(0,125,255)',
    },
});
```

Burada süslü metnin "standart" metnin boyutunu kullandığını, ancak iki ek stil özelliği eklediğini görebiliriz. Stil dizisinde en son aktardığımız için "standart" stilin rengini geçersiz kıldığına dikkat edin. Ayrıca bu dizide satır içi stil nesnelerini ve StyleSheet stillerini karıştırıp eşleştirebileceğimizi de unutmayın.

Bu yaklaşım, stillerimizin bazı kısımlarını birden fazla yerde yeniden kullanarak karmaşık bileşenlerin karmaşıklığını yönetmemize yardımcı olur.

Yarın, bileşenlerimiz için duyarlı düzenler tanımlamak üzere stil oluşturmayı bir adım öteye taşıyacağız.

| [← 2. Gün • Bileşenler](./DERS_2.md)  | [3. Gün • Stil Tanımlamarı](./DERS_3.md) | [4. Gün • Flex Düzeni →](./DERS_4.md) |
|:--------------------------------------|-----------------------------------------:|:-------------------------------------:|
