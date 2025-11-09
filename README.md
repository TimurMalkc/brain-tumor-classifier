# brain-tumor-classifier
Beyin Tümörü Tespiti (MRI Görüntülerinden Derin Öğrenme ile Sınıflandırma)
##1. Projenin Amacı

Bu projenin amacı, derin öğrenme yöntemleri kullanarak beyin MRI (Manyetik Rezonans Görüntüleme) görüntülerinden bir kişide beyin tümörü olup olmadığını otomatik olarak tespit eden bir model geliştirmektir. Tıp alanında, MRI görüntülerinin incelenmesi uzmanlık gerektiren ve zaman alan bir işlemdir. Bu nedenle, bu tür bir otomatik sınıflandırma sistemi doktorlara yardımcı olabilir ve teşhis sürecini hızlandırabilir.

Bu proje, öğrenci düzeyinde uygulanabilir basit bir yaklaşımla, önceden eğitilmiş bir derin öğrenme modelinden (transfer learning yöntemiyle) yararlanarak gerçekleştirilmiştir.

##2. Kullanılan Teknolojiler ve Araçlar

Python – temel programlama dili

TensorFlow / Keras – derin öğrenme modeli oluşturmak için

OpenCV (cv2) – görüntüleri işlemek için

Pandas, NumPy – veri düzenleme ve analiz için

Matplotlib – veri görselleştirme için

Ayrıca modelin eğitimi için kullanılan veri seti, “Brain MRI Images for Brain Tumor Detection” adlı açık kaynaklı bir veri kümesidir. Bu veri setinde “yes” (tümör var) ve “no” (tümör yok) olmak üzere iki sınıf bulunmaktadır.

##3. Veri Seti ve Ön İşleme

Veri seti iki klasörden oluşmaktadır:

yes/ → Beyin tümörü bulunan MRI görüntüleri

no/ → Beyin tümörü bulunmayan MRI görüntüleri

Toplamda 253 adet görüntü mevcuttur:

155 adet “Yes”

98 adet “No”

Veriler önce bir pandas DataFrame’e aktarılmış, ardından rastgele örnekler çizdirilerek görsel olarak kontrol edilmiştir. Daha sonra veriler, %95 eğitim / %5 test oranında bölünmüş, eğitim verisi içinden de %10 doğrulama (validation) verisi ayrılmıştır.

Modelin daha iyi genelleme yapabilmesi için ImageDataGenerator sınıfı kullanılarak görüntüler üzerinde bazı veri artırma (data augmentation) işlemleri uygulanmıştır:

Döndürme (rotation)

Kaydırma (width/height shift)

Yakınlaştırma (zoom)

Ayna çevirme (flip)

Bu sayede model farklı açılardan gelen görüntülerle karşılaşmış olur ve aşırı öğrenme (overfitting) engellenir.

##4. Modelin Yapısı

Bu projede transfer learning yöntemi kullanılmıştır. Yani sıfırdan bir ağ eğitmek yerine, daha önce büyük veri setlerinde eğitilmiş bir model alınmış ve üzerine birkaç katman eklenmiştir.

Kullanılan temel model:

InceptionResNetV2 (önceden ImageNet veri setinde eğitilmiştir)

Bu modelin son sınıflandırma katmanı kaldırılmış (include_top=False) ve 200x200 boyutundaki MRI görüntüleriyle yeniden eğitilmiştir.

Üzerine eklenen katmanlar:

GlobalAveragePooling2D – özellikleri sıkıştırmak için

Dense (128, ReLU) – öğrenilen özellikleri sınıflandırmak için

BatchNormalization ve Dropout(0.2) – aşırı öğrenmeyi azaltmak için

Dense (1, Sigmoid) – iki sınıf (tümör var/yok) için çıktı katmanı

##5. Modelin Eğitimi

Model, binary_crossentropy kayıp fonksiyonu ve Adam optimizasyon algoritmasıyla derlenmiştir.
Eğitim sırasında şu geri çağırma (callback) fonksiyonları kullanılmıştır:

ModelCheckpoint: En iyi doğrulama sonuçlarını veren ağı kaydetmek için

EarlyStopping: Doğrulama kaybı 3 epoch boyunca iyileşmezse eğitimi durdurmak için

Model toplam 5 epoch boyunca eğitilmiştir ve sonuçlar şu şekildedir:

Epoch	Doğruluk (train)	Doğruluk (val)	Kayıp (val_loss)
1	%76	%87	0.37
2	%86	%75	0.46
3	%87	%79	0.45
4	%87	%79	0.38

Model 4. epoch sonunda erken durdurma ile eğitimi tamamlamıştır.

##6. Sonuçlar

Model, test veri seti üzerinde şu sonuçları vermiştir:

Kayıp (loss): 0.38

Doğruluk (accuracy): %84.6

Bu sonuç, basit bir öğrenci projesi için oldukça başarılıdır. Model, küçük bir veri setine rağmen MRI görüntülerinden beyin tümörünü ayırt etmede %80’in üzerinde doğruluk sağlamıştır.

##7. Sonuç ve Gelecekteki Geliştirmeler

Bu proje, derin öğrenmenin sağlık alanında nasıl kullanılabileceğine dair küçük ama etkili bir örnektir. Daha büyük ve dengeli bir veri setiyle model yeniden eğitilirse doğruluk oranı artırılabilir. Ayrıca modelin çıktılarına Grad-CAM gibi görselleştirme teknikleri eklenerek hangi bölgelerin tümör olarak algılandığı da açıklanabilir.

Özetle:
Bu proje, öğrenci düzeyinde TensorFlow ve Keras kullanılarak hazırlanmış, beyin MRI görüntülerinden beyin tümörü tespiti yapan bir derin öğrenme modelidir. Transfer learning yöntemi sayesinde kısa sürede eğitilmiş, doğrulama ve test setlerinde %80’in üzerinde başarı elde edilmiştir.
