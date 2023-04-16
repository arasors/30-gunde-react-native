
# 2. GÜN | İlk Componentimiz

### Artık her şeyi ayarladığımıza göre, React Native'de bileşenlerin nasıl çalıştığını inceleyelim.

React'e zaten aşinaysanız, React Native'de nasıl yazacağınızı zaten biliyorsunuz demektir. Bunun nedeni, her ikisinin de temel bir kavramı paylaşmasıdır "arayüzler oluşturmak için bileşenleri kullanmak".

React'i daha önce web için hiç kullanmadıysanız endişelenmenize gerek yok! Şimdi React Native'de bileşenlerin nasıl çalıştığını inceleyelim.

### Bileşen yapısı

```javascript
// App.js
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text>Open up App.js to start working on your app!</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

Dosyanın her bir bölümünü adım adım inceleyelim. Tüm içe aktarmalarımız en başta bildirilir:
```javascript
import React from "react";
import { StyleSheet, Text, View } from "react-native";
```
Tıpkı bir web sayfası için React'te bileşen yazmak gibi, bileşenlerimizi oluşturabilmek için react kütüphanesini içe aktarmamız gerekir. Ancak ikinci satırda, React Native'den bir dizi çekirdek API de içe aktarılır:

### Temel Bileşenler
#### StyleSheet
* Bileşen işlevinin dışında stilleri ayarlamak için kullanılan API
#### Text
* Metin görüntülemek için kullanılır (HTML'deki span etiketine benzer)
#### View
* Düzenleri tanımlamak ve sınırları olan kutular çizmek için kullanılır (HTML'deki div etiketine benzer)

Web'de div ve span gibi temel öğeleri çağırmasınız bile kodunuz çalışacaktır çünkü tarayıcı tarafından otomatik olarak desteklenir. Ancak React Native'de her bileşenin içe aktarılması gerekir.

React Native (ve React) kullanarak bir bileşen tanımlamanın iki yolu vardır:

* Function Component'ler
* Class Component'ler

Performans ve kullanım biçimi açısından Function Componentleri ben daha verimli bulduğum için bu eğitimde Class Component'lere girmeyeceğim.


React Native'de stil oluşturma hakkında daha fazla bilgi edinmeye hazır mısınız? Yarınki makalemizde bu konuyu daha ayrıntılı olarak inceleyeceğiz!

| [← 1. Gün • Proje Kurulumu](./DERS_1.md) | [2. Gün • Bileşenler](./DERS_2.md) | [3. Gün • Stil Tanımlamaları →](./DERS_3.md) |
|------------------------------------------|-----------------------------------:|:--------------------------------------------:|
