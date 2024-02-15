### Temel Türler & Null Güvenliği Cevaplar

1. **val ile var arasındaki fark nedir?**
    - `val`, değeri bir kez atanıp daha sonra değiştirilemeyen (değişmez) bir değişkeni tanımlar.
    - `var`, değeri atandıktan sonra değiştirilebilen bir değişkeni tanımlar.

2. **Bir var değişkeni val gibi davranmasını nasıl sağlayabiliriz val kelimesini kullanmadan? Bunu neden yapmak isteriz? Örnek bir senaryo verin.**
    - `val` yerine bir değişkenin değişmez olmasını sağlamak için `const` veya `final` anahtar kelimeleri kullanılabilir. Bu, sabit bir değer atanmış bir değişken oluşturur. Örneğin, bir sabit olan pi sayısını tanımlamak için:
      ```kotlin
      const val PI = 3.14159
      ```

3. **"Değişmez" (Immutable) ve "Salt Okunur" (ReadOnly) kavramlarını açıklayın. val değişkenler neden aslında "değişmez" değil de "salt okunur" olarak açıklanmalıdır?**
    - Değişmez değişkenler, değerlerinin atanmasından sonra değiştirilemeyen değişkenlerdir. Salt okunur değişkenler ise değerleri atanır atanmaz değiştirilemeyen değişkenlerdir. `val` değişkenleri salt okunur olarak adlandırılır, çünkü sadece bir kez değer atanabilirler, ancak bu değer sonradan değişebilir.

4. **"Tip Çıkarımı" (Type inference) kavramını açıklayın. Hangi durumlarda tip belirtmek kesin olarak gereklidir?**
    - Tip çıkarımı, bir değişkenin tipinin derleyici tarafından otomatik olarak belirlendiği bir özelliktir. Genellikle Kotlin'de tip belirtmek gerekli değildir, çünkü derleyici değişkenin tipini çıkarabilir. Ancak, bazı durumlarda netlik için tip belirtmek gerekebilir, özellikle karmaşık ifadeler veya karşılaşılabilecek potansiyel belirsizlikler söz konusu olduğunda.

5. **Kotlin'de tüm değişkenlerin sınıf olarak bulunması, "ilkel tip" (primitive type) olmadıkları anlamına gelir mi? Arka planda neler oluyor?**
    - Evet, Kotlin'de ilkel tipler (primitive types) yoktur. Bunun yerine, tüm veri türleri nesne olarak temsil edilir. Ancak, Kotlin derleyicisi, performans optimizasyonları için ilkel tipleri kullanır ve bunları Java'nın ilkel tiplerine dönüştürür.

6. **"Tip Güvenliği" (Type Safety) kavramını açıklayın.**
    - Tip güvenliği, bir dilin tiplerini güvenli bir şekilde kullanmasını sağlayan bir özelliktir. Bu, tip uyumsuzluğundan kaynaklanan hataları en aza indirir. Kotlin, tip güvenli bir dil olarak bilinir, çünkü derleme zamanında ve çalışma zamanında tip uyumsuzluklarını önler.

7. **Bir değişkeni nullable yapmak için ne yapmalıyız?**
    - Bir değişkeni nullable yapmak için tipin sonuna bir soru işareti (?) eklenir. Örneğin:
      ```kotlin
      var nullableString: String? = null
      ```

8. **"Null Güvenliği" (Null Safety) kavramını açıklayın.**
    - Null güvenliği, bir dilin veya bir dilin kütüphanesinin null referanslarından kaynaklanan hataları önlemek veya en aza indirmek için sağladığı özelliktir. Kotlin, null güvenli bir dil olarak tasarlanmıştır ve nullable ve non-nullable türler arasında net bir ayrım yapar.

9. **Bir değişkene null değer atanır ve tip belirtilmezse Kotlin bu değişkeni nasıl yorumlar?**
    - Bu durumda, değişken nullable olarak kabul edilir. Kotlin'de tüm değişkenler non-nullable olarak varsayılan olarak kabul edilir, ancak bir değişkene null değer atanması durumunda nullable hale gelir.

10. **İlkel bir değişkenin nullable olması ile null değer alamaması arasında bellek yönetimi açısından nasıl farklar vardır?**
    - İlkel bir değişken nullable değilse, bellekte null değer alamaz ve bu nedenle bellekten tasarruf edilebilir. Ancak, nullable bir ilkel değişken null değer alabilir ve bu durumda bellekte ek bir değer tutulur.

11. **Nullable bir değişkenin bir değere sahip olması ile null olması arasında bellek yönetimi açısından nasıl bir fark vardır? Null değer almış bir değişken bellekte yer kaplamaz diyebilir miyiz?**
    - Bir nullable değişken bir değere sahipse, bellekte bir değer tutulur. Ancak null olduğunda, bellekte herhangi bir değer tutulmaz. Dolayısıyla, null değer almış bir değişkenin bellekte yer kaplamadığını söyleyebiliriz.

12. **Nullable bir değişkenle çalışırken hangi operatörleri kullanırız? Bu operatörlerin kullanım farkları nelerdir? Hangisini ne zaman kullanmak daha anlamlıdır?**
    - Nullable bir değişkenle çalışırken `?.`, `?:`, `!!.` operatörlerini kullanabiliriz.
        - `?.` (safe call operator): Değişken null değilse işlemi gerçekleştirir, null ise null döner.
        - `?:` (elvis operator): Değişken null ise

alternatif bir değeri döndürür.
- `!!.` (not-null assertion operator): Değişkenin null olmadığına güvendiğimizde kullanılır. Eğer değişken null ise NullPointerException fırlatılır.
- `?.` operatörü, güvenli bir şekilde nullable değişkenler üzerinde işlem yapmak için kullanılmalıdır. `?:` operatörü, bir değerin null olması durumunda bir alternatif değer döndürmek için kullanılır. `!!.` operatörü, null olmayan bir değere güvenildiğinde kullanılır, ancak dikkatli kullanılmalıdır çünkü null değer aldığında NullPointerException fırlatır. Bu nedenle, mümkünse `?.` ve `?:` operatörlerini kullanmak daha güvenlidir.
---
### Sayılar Cevaplar
1. **Kaç farklı tipte "number" sınıfı miras alan "alt sınıf" (child class) vardır? Bunların değer aralıkları neden önemlidir?**
    - Kotlin'de `Number` sınıfı, `Double`, `Float`, `Long`, `Int`, `Short` ve `Byte` gibi alt sınıflara sahiptir. Bu alt sınıflar farklı veri tiplerini temsil eder. Değer aralıkları, hangi türün kullanılacağını belirlemekte önemlidir çünkü bazı veri tipleri daha büyük değerler alabilirken bazıları daha küçük değerlere sahiptir.

2. **Eğer bir değişkene tip belirtimi yapılmaz ve bir değer atanırsa, Kotlin tip çıkarımını nasıl yapar?**
    - Kotlin, değişkenin ilk atanmış değerine bakarak tip çıkarımı yapar. Atanan değere göre değişkenin tipini belirler.

3. **Float değişken oluştururken F ve f harfleri varken, Long değişken oluştururken neden küçük l harfi yoktur?**
    - Kotlin'de, `Long` değişken oluşturmak için "L" kullanmak istendiğinde karışıklık olabileceği düşünüldüğünden, "L" yerine otomatik olarak tam sayı değeri kabul edilir.

4. **Tek duyarlıklı (Single precision) ve Çift duyarlıklı (Double precision) kavramlarını açıklayın.**
    - Tek duyarlıklı (Single precision) veri türleri, daha az bellek kullanarak daha düşük hassasiyetle kayan noktalı sayıları temsil ederken, çift duyarlıklı (Double precision) veri türleri, daha yüksek hassasiyet ve daha geniş bir değer aralığı sağlamak için daha fazla bellek kullanır.

5. **Double ve Float değişkenlerle çalışırken ondalık ayıraçı olarak hangi işaretler kullanılır? Bu ayıraçların kullanımında nelere dikkat etmek gerekir?**
    - Double ve Float değişkenlerle çalışırken ondalık ayıraçı olarak nokta (.) kullanılır. Dikkat edilmesi gereken nokta, sayıların doğru biçimlendirilmesi ve veri türlerinin sınırları içinde kalınmasıdır.

6. **Double ve Float değişkenler ondalık kısımda kaç basamağa kadar işlem yaparlar? Bu sınırın üzerinde gelen ondalık bilgileri için nasıl davranırlar? Hangi durumlar için Float ve hangi durumlar için Double kullanılmalıdır?**
    - Float 7 basamağa kadar, Double ise 15-16 basamağa kadar işlem yapabilir. Bu sınırların üzerinde gelen ondalık bilgiler yuvarlanır veya kesilir. Genel olarak, daha fazla hassasiyet gerektiren hesaplamalarda Double kullanılmalıdır, ancak bellek ve işlemci kaynaklarından tasarruf etmek istendiğinde Float tercih edilebilir.

7. **Ondalık(Decimal), Onaltılık (Hexadecimal) ve İkilik (Binary) değişkenleri Kotlin'de nasıl tanımlayabilirsiniz?**
    - Ondalık sayılar için herhangi bir ön ek gerekmez. Örneğin: `val decimalNumber = 10`
    - Onaltılık sayılar için ön ek olarak `0x` kullanılır. Örneğin: `val hexNumber = 0x1F`
    - İkilik sayılar için ön ek olarak `0b` kullanılır. Örneğin: `val binaryNumber = 0b1010`

8. **Sekizlik (Octal) değişkenler Java'da nasıl tanımlanır? Kotlin'de Sekizlik değişken tanımlanabilir mi?**
    - Java'da, sekizlik sayılar için ön ek olarak `0` kullanılır. Örneğin: `int octalNumber = 012`
    - Kotlin'de ise sekizlik sayılar için özel bir ön ek yoktur ve bu nedenle sekizlik sayılar kolayca tanımlanabilir.

9. **"Geleneksel Notasyon" (Conventional Notation) gösterimi nasıl yapılır?**
    - Geleneksel notasyon, sayıları normal şekilde gösterme şeklidir. Örneğin: `123`

10. **Sayısal değişkenlerde alt çizgi (underscore) nasıl kullanılır? Kotlin bunu nasıl yorumlar?**
    - Alt çizgi, büyük sayıları okunabilirliği artırmak için kullanılabilir. Kotlin, alt çizgileri sadece okuma kolaylığı için kullanır ve derleme sürecinde bunları yok sayar.

11. **== ile neyi karşılaştırırız? === ile neyi karşılaştırırız?**
    - `==` operatörü, değerleri karşılaştırırken `===` referansları karşılaştırır.

12. **=== operatörü ile karşılaştırma yaparken Byte değer aralığı neden önemlidir? Kotlin bu aralığa göre neden özel bir davranış sergiler?**
    - Byte değer aralığı -128 ile 127 arasındadır. Kotlin, bu aralıkta değerlerin aynı referansa sahip olmasını sağlamak için özel bir davranış sergiler. Bu nedenle, bu aralıktaki iki Byte değeri `===` operatörü ile karşılaştırıldığında true döner.

13. **Sayısal değişkenlerde hangi matematiksel operatörler kullanılabilir?**
    - Toplama (+), çıkarma (-), çarpma (*), bölme (/), kalanı bulma (%), arttırma (++), azaltma (--) gibi matematiksel operatör
---
### İşaretsiz Sayılar Cevaplar
1. **"İşaretsiz" (Unsigned) değişkenler ne demektir? İşaretli olanlarla aralarındaki fark nedir?**
    - "İşaretsiz" (Unsigned) değişkenler, negatif değerleri temsil etmek için işaret biti kullanmayan değişkenlerdir. İşaretli değişkenler ise negatif veya pozitif değerleri temsil etmek için bir işaret biti kullanırlar. Örneğin, bir 8 bitlik işaretli bir değişken -128 ile 127 arasında değer alırken, işaretsiz bir 8 bitlik değişken 0 ile 255 arasında değer alır.

2. **"İşaretsiz" değişkenler nasıl bir sınıf yapısında tutulurlar? Bu neden önemlidir?**
    - "İşaretsiz" değişkenler, değerlerini temsil etmek için ilgili veri türünün tüm bitlerini kullanır. Bu nedenle, işaretsiz değişkenlerle daha geniş bir değer aralığı elde edilebilir. Örneğin, işaretsiz 8 bitlik bir değişken, 0 ile 255 arasındaki tüm değerleri temsil edebilir.

3. **"İşaretsiz" değişkenlerin harf gösterimi nasıldır?**
    - İşaretsiz değişkenlerin harf gösterimi, ilgili veri tipine 'u' eklenerek yapılır. Örneğin, UInt için `u` ve ULong için `uL` kullanılır.

4. **"val a1 = 42u ve val a2 = 0xFFFF_FFFF_FFFFu" değişkenlerin tipleri ne olur? Neden?**
    - `val a1 = 42u` ifadesinde `a1` değişkeni UInt türünde olur, çünkü `u` eki UInt türünü ifade eder.
    - `val a2 = 0xFFFF_FFFF_FFFFu` ifadesinde ise `a2` değişkeni ULong türünde olur, çünkü bu ifade UInt türünün sınırlarını aşar ve daha geniş bir veri aralığına sahip olan ULong türünü gerektirir.

5. **"İşaretsiz" "Long" harf gösterimi nasıl yapılır?**
    - İşaretsiz Long türünün harf gösterimi `uL` şeklindedir.

6. **"İşaretsiz" değişkenlerin kullanım amaçları nelerdir?**
    - İşaretsiz değişkenler genellikle pozitif değerleri temsil etmek için kullanılır. Özellikle veri aralığının sıfırın altında olmadığı durumlarda ve bellek tasarrufu veya veri doğruluğu gerektiren yerlerde kullanışlıdır.

7. **"İşaretsiz" değişkenlerle yapılan matematiksel işlemlerde, özellikle büyük sayılarla çalışırken karşılaşılabilecek taşma (overflow) ve taşma olmaması (underflow) durumları için Kotlin nasıl bir yönetim sağlar?**
    - Kotlin, işaretsiz değişkenlerle yapılan matematiksel işlemlerde taşma durumlarını kontrol eder. Taşma durumunda, değer sınırlara getirilir veya hata fırlatılır.

8. **"İşaretsiz" değişkenlerin sınırlamaları nelerdir?**
    - İşaretsiz değişkenlerin sınırları, kullanılan veri türünün bit sayısına bağlıdır. Örneğin, bir 8 bitlik işaretsiz değişken 0 ile 255 arasındaki tüm değerleri alabilir.

9. **"İşaretsiz" değişken türleri (UInt, ULong vs.) kullanırken, Java API'leri ile uyumluluk konusunda ne gibi sorunlar olabilir? Bunları çözmek için neler yapabilirsiniz?**
    - Java'da işaretsiz veri türleri doğrudan desteklenmediği için, Kotlin'de işaretsiz veri türlerini Java ile etkileşimde kullanırken bazı uyumluluk sorunları yaşanabilir. Bu sorunları çözmek için, işaretsiz değişkenlerin uygun işaretli değişkenlere dönüştürülmesi veya işaretli değişkenlerin işaretli olmayan veri türlerine dönüştürülmesi gerekebilir.
---
### Tür Dönüşümü Cevapları
1. **is ve !is operatörlerinin kullanımını açıklayın.**
    - `is` operatörü, bir nesnenin belirli bir türe ait olup olmadığını kontrol eder. Örneğin:
      ```kotlin
      val x: Any = "hello"
      if (x is String) {
          println(x.length) // Güvenli bir şekilde String türüne dönüşüm yapıldı.
      }
      ```
    - `!is` operatörü, bir nesnenin belirli bir türe ait olmadığını kontrol eder.

2. **"Akıllı Dönüşüm" (Smart Cast) ne demektir? Farklı kod örnekleri ile açıklayın. Bu özelliğin sınırlamaları nelerdir?**
    - Akıllı Dönüşüm, bir türden başka bir türe dönüşüm yaparken kodun otomatik olarak ilgili türe dönüştürülmesidir. Örneğin:
      ```kotlin
      val x: Any = "hello"
      if (x is String) {
          println(x.length) // x artık String türünde olduğu için length özelliğine erişilebilir.
      }
      ```
    - Akıllı dönüşümün sınırlamaları, dönüşümün sadece belirli durumlarda gerçekleşebileceği ve karmaşık kontrol yapılarıyla kullanıldığında etkisiz olabileceğidir.

3. **"Güvenli & Güvensiz" operatörler nelerdir?**
    - Güvenli dönüşüm operatörü (`as?`), dönüşümün başarısız olması durumunda null döndürür.
    - Güvensiz dönüşüm operatörü (`as`), dönüşümün başarısız olması durumunda bir `ClassCastException` fırlatır.

4. **Sayısal değişkenlerde örtük tip genişletme (implicit widening conversions) ne demektir? Kotlin'de bu neden yapılamaz?**
    - Örtük tip genişletme, bir veri tipinin daha büyük bir veri tipine dönüştürülmesidir. Kotlin'de bu işlem otomatik olarak yapılmaz çünkü bu, veri kaybına neden olabilir ve istenmeyen sonuçlara yol açabilir.

5. **"val b: Byte = 1 ile val i: Int = b ve son olarak print(b == i) gibi bir kod yazıldığında çıktı ne olur? Neden böyle bir çıktı aldığınızı açıklayın.**
    - Bu durumda, derleme hatası alırsınız çünkü Kotlin kesin tür dönüşümü yapmaz. `b` değişkeni Byte türünde olduğu için Int türüne doğrudan atanamaz.

6. **"val b: Byte = 1 ile val i: Int = b.toInt() ve son olarak print(b == i) gibi bir kod yazıldığında çıktı ne olur? Neden böyle bir çıktı aldığınızı açıklayın.**
    - `b` değişkeni Byte türünde olduğu için Int türüne dönüştürülmelidir. Dolayısıyla, `b.toInt()` ifadesi kullanılır. Ancak, bu durumda yine de `print(b == i)` ifadesi false dönecektir çünkü Byte ve Int türlerinin değer aralıkları farklıdır.

7. **Sayısal değişkenlerde açık dönüşüm (Explicit Type Conversion) yaparken hangi fonksiyonları kullanabilirsiniz?**
    - Sayısal değişkenlerde açık dönüşüm için `toByte()`, `toShort()`, `toInt()`, `toLong()`, `toFloat()`, `toDouble()`, `toChar()` gibi fonksiyonlar kullanılabilir.

8. **"val result = 1L + 3" // "Long + Int" gibi bir işlemin sonucunda "result" değişkeninin tipi ve değeri ne olur? Neden böyle olduğunu açıklayın.**
    - `result` değişkeninin tipi Long olur çünkü en az bir operatör Long türünde olduğunda sonuç Long türünde olur. Sonuç 4L olur.

9. **"val result = Int.MAX_VALUE + Int.MAX_VALUE" gibi bir işlemin sonucunda "result" değişkeninin tipi ve değeri ne olur? Neden böyle olduğunu açıklayın.**
    - Bu durumda, taşma (overflow) olur ve sonuç beklenenden farklı olur. Sonuç negatif bir değer olur çünkü taşma meydana gelir.

10. **"val x = 5 / 2 println(x == 2)" gibi bir işlemin sonucu ve tipi nedir? Neden böyle olduğunu açıklayın.**
    - Bu işlemin sonucu 2'dir çünkü bölme işlemi iki tam sayı arasında gerçekleşir ve sonuç tam sayı olarak hesaplanır.

11. **"val x = 5L / 2 println(x == 2L)" gibi bir işlemin sonucu ve tipi nedir? Neden böyle olduğunu açıklayın.**
    - Bu durumda, x'in tipi Long olur çünkü en az bir operand Long türünde olduğunda sonuç Long türünde olur. Sonuç 2L olur.

12. **"val x = 5 / 2.toDouble() println(x == 2.5)" gibi bir işlemin sonucu ve tipi nedir? Neden böyle olduğunu açıklayın.**
    - Bu işlemin sonucu 2.5 olur çünkü 5 ve 2 sayıları önce tamsayı olarak bölünür ve sonuç daha sonra Double türüne dönüştürülür.

13. **Kotlin'de tür dönüşümü yapılırken, dönüşümün başarısız olması durumunda TypeCastException