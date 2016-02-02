---
layout: page
title: Proje
---



# MARKA TESCİLLERİNİN YILLARA GÖRE DAĞILIMI VERİSİ ÜZERİNE R PAKET PROGRAMI KULLANARAK YAPILAN BİR ANALİZ ÇALIŞMASI


## 1.Giriş

*Türk Patent Enstitüsü’nden alınan veriler ile açıklayıcı istatistikler ve regresyon analizi yapılmıştır. *
[TPE](http://www.tpe.gov.tr/TurkPatentEnstitusu/statistics/)
*adresinden, Marka Tescillerinin Yıllara Göre Dağılımı isimli veri seti indirildi.Markalar ismiyle Excel Çalışma Kitabı formatında Yıllar değişkeni, şehir isimleri ve yıllara göre bulunan Toplam değerler olarak düzeltildi, kaydedildi ve aşağıdaki kodlar kullanılarak R-Studio’ ya aktarıldı. *

### 2.Histogram



#### 3. Açıklayıcı İstatistikler
*Beş büyük şehir için açıklayıcı istatistiklere hesaplanmıştır(Tablo 3.1). Sırasıyla en küçük, en büyük, ortalama ve standart sapma değerleri tabloda verilmiştir. Tüm şehirlerin 1995-2015 yılları arasındaki toplam tescil sayısı gösterilmiştir(Tablo 3.2).*


*Yıllara göre Toplam tescil sayısının nasıl bir değişime uğradığı histogram grafiği ile incelenmiştir. *
* adasda
* asdasd
   +add 
   +asdada
   +asdasfa

```{r}
require(caret)
evveri$price=as.factor(evveri$price)
ctrl <- trainControl(method = "cv", 
                     number = 10, 
                     savePredictions = TRUE)

lojistikcv<- train(price~lotsize+stories,  data=evveri, 
              method="glm", family="binomial",
                 trControl = ctrl)
```

		

		 