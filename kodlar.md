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




*Buna göre 1995’ten 2015’ e gidildikçe tescil sayısında artış görülmüştür.*

##### 3. Açıklayıcı İstatistikler
*Beş büyük şehir için açıklayıcı istatistiklere hesaplanmıştır(Tablo 3.1). Sırasıyla en küçük, en büyük, ortalama ve standart sapma değerleri tabloda verilmiştir. Tüm şehirlerin 1995-2015 yılları arasındaki toplam tescil sayısı gösterilmiştir(Tablo 3.2).*




*Tablo 3.1*





*Tablo 3.2*





###### 4. 5 Büyük Şehir ve Diğer Şehirlerin Marka Tescillerinin Dağılımları;







*Tablo3.1*

*İstanbul’ un en büyük pasta dilimine sahip olduğunu görülür. 5 büyük şehirdeki toplam tescil sayısının tüm toplam tescil sayısına oranı 0,3944816 olarak bulunmuştur.*
#######5. Regresyon Modeli ile Yılları Kullanarak Toplam Tahminleme;

*Buradaki amaç yıllara göre değişen toplam değerleri ile veri setinde yer almayan yıllar için bir toplam değeri tahminlemektir. Tüm tablolar Excel ile düzenlenmiştir. 











*Bu çıktıya göre model sabiti olan β_0 -6566561’dır ve bir birimlik yıllar değişkenindeki artışın tahmin edilen Y ̂ üzerinde〖  β〗_1=3290 kadar bir artışa neden olduğu görülür.   *





*ANOVA tablosuna göre p-value değeri alpha=0.05 ten oldukça küçüktür. Bu durumda ‘Model anlamlı değildir.’ H_0hipotezi reddedilir. Modelin %95 güven ile istatistiksel olarak anlamlı ve kullanıma uygun olduğu ve Yıllar bağımsız değişkeni katsayısının anlamlı olduğu çıkarımında bulunulur. *







*F testi istatistiği burada da görülmektedir. P-value değerinin mümkün olduğunda 0’a yakın olması beklenir. Regresyon o kadar anlamlıdır. R-square değeri 0 ile 1 arasında değişmektedir ve denklemin bağımlı değişkeni ölçme gücünü gösterir. 0,8753 yüksek açıklama oranı olduğu için modelin kullanılması uygundur. Başka bir bağımlı değişken eklendiğinde, bağımlı değişkenler arasında çoklu korelasyon sorunu olursa özet bilgide görülen Adjusted  R-Square değeri R-square değerinde hem çok farklı hem de küçük olur. Bu analizde ise tek değişken kullanılması küçük bir değişime neden olmuş ancak modelin gücünü teyit edebilmiştir.( Adj-R-square= 0.8688) Tek bir bağımlı değişken ile bağımsız değişkenin yaklaşık %86’ sını açıklayabilmektedir. *
*Artık değerleri, regresyon analizinin varsayımlarından, Normal dağılıma uymaktadır. 
20 yıl içerisinde en fazla marka tescili alan İstanbul’un bağımlı değişkenin toplam tahminlemesinde rolü olup olmadığını görmek için modele İstanbul da eklenmiştir.
*




*Çıktıda sırasıyla β_0, Yıllar değişkenin katsayısı ve İstanbul değişkenin katsayısı görülmektedir.*

*ANOVA daki p-value değeri 0.05’ten küçük olması nedeniyle bu kurulan denklemin de anlamlı olduğu söylenir. Yıllar ve İSTANBUL bağımsız değişkenleri model için anlamlıdır.*










*İki değişken ile açıklama oranı %99 gibi bir değer çıkmıştır ki bu şaşırtacak kadar iyi bir orandır. Adj-R-square ile bu da doğrulanır. 
Artık değerler normal dağılıma uymaktadır.
*



########6. R Kodları;


```{r}
#install.packages("xlsx")
library(xlsx)
#install.packages("dplyr")
library(dplyr)
#install.packages("ggplot2")
library(ggplot2)
#install.packages("readxl")
library(readxl)
#install.packages("plotrix")
library(plotrix)

#veri aktarımı;
veri<-read_excel("c:\\k3.xlsx")
veri
options(dplyr.width=Inf)

#histogram cizimi;
ggplot(data=veri)+geom_bar(aes(x=Yıllar, y=Toplam),stat="identity",fill="green")

#descriptiveStatistics;
ds1<-veri %>%
group_by("Yıllar") %>%
  summarise(Adana_Min=min(ADANA),Adana_Max=max(ADANA),Adana_Mean=mean(ADANA),Adana_Sd=sd(ADANA))
write.xlsx2(data.frame(ds1),"ds1.xlsx")

ds2<-veri %>%
group_by("Yıllar") %>%
  summarise(Ankara_Min=min(ANKARA),Ankara_Max=max(ANKARA),Ankara_Mean=mean(ANKARA),Ankara_Sd=sd(ANKARA))
write.xlsx2(data.frame(ds2),"ds2.xlsx")

ds3<-veri %>%
group_by("Yıllar") %>%
  summarise(Bursa_Min=min(BURSA),Bursa_Max=max(BURSA),Bursa_Mean=mean(BURSA),Bursa_Sd=sd(BURSA))
write.xlsx2(data.frame(ds3),"ds3.xlsx")

ds4<-veri %>%
group_by("Yıllar") %>%
  summarise(İzmir_Min=min(İZMİR),İzmir_Max=max(İZMİR),İzmir_Mean=mean(İZMİR),İzmir_Sd=sd(İZMİR))
write.xlsx2(data.frame(ds4),"ds4.xlsx")

ds5<-veri %>%
group_by("Yıllar") %>%
  summarise(İstanbul_Min=min(İSTANBUL),İstanbul_Max=max(İSTANBUL),İstanbul_Mean=mean(İSTANBUL),İstanbul_Sd=sd(İSTANBUL))
write.xlsx2(data.frame(ds5),"ds5.xlsx")

#5 şehrin diğer şehirler ile oranı için pie3d;

t1<-c(sum(veri["Toplam"])-sum(sum(veri["İSTANBUL"]),sum(veri["İZMİR"]),sum(veri["BURSA"]),sum(veri["ADANA"]),sum(veri["ANKARA"])))
t2<-c(sum(veri["İSTANBUL"]),sum(veri["İZMİR"]),sum(veri["BURSA"]),sum(veri["ADANA"]),sum(veri["ANKARA"]),t1)
lbls<-c("İstanbul","İzmir","Bursa","Adana","Ankara","Diğer")
,main="5 İlin Diğer Şehirler ile Karşılaştırılması",init.angle=100,explode=0.1)
pie3D(t2,labels=lbls,explode=0.1,main="5 Büyük iller ve Diğer illerin Marka Tescil Oranları",col=terrain.colors(6))

#Tüm şehirlerin ayrı ayrı toplamları ve Türkiye genelini toplamı;
sehirtoplam<-veri %>%
summarise_each(funs(sum),-Yıllar)
write.xlsx2(data.frame(sehirtoplam),"sehirtoplam.xlsx")

#5 büyük şehrin toplam tescil sayısının toplam tescil sayısına oranı;
ttop<-c(sum(veri["İSTANBUL"]),sum(veri["İZMİR"]),sum(veri["BURSA"]),sum(veri["ADANA"]),sum(veri["ANKARA"]))
sum(ttop)
t1<-sum(veri["Toplam"])-sum(sum(veri["İSTANBUL"]),sum(veri["İZMİR"]),sum(veri["BURSA"]),sum(veri["ADANA"]),sum(veri["ANKARA"]))
oran<-t1/sum(ttop)
oran

#lineer models;
regmodel<-lm(veri$Toplam ~ veri$Yıllar ) # Yıllar ile tahminleme
regmodel #katsayılar
summary(regmodel) #F, Residuals  ve R^2 
anova(regmodel)


regmodel2<-lm("Toplam-İSTANBUL~Yıllar+İSTANBUL",veri)  #yıllar ve istanbul verileri ile istanbulutahminleme
regmodel2 #katsayılar
summary(regmodel2) # F, Residuals ve R^2
anova(regmodel2)

predicted=predict(regmodel,veri[1,])
print(c(veri$Toplam[1],predicted))

```

		

		 