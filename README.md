# brain-tumor-classifier
## Beyin Tümörü Tespiti (MRI Görüntülerinden Derin Öğrenme ile Sınıflandırma)

Yapılan çalışmalar, elde edilen veriler, görüntüler, istatistikler ve sonuçlar "brain-tumor-classifier.ipynb" dosyası içerisinde görülebilmektedir. "brain_tumor_dataset.rar" ise çalışma için kullanılmış olan veri setidir.

Son yıllarda yapay zekâ, sağlık alanında en çok ilgi gören teknolojilerden biri haline gelmiştir. Özellikle beyin tümörü gibi erken teşhisi hayati önem taşıyan hastalıkların tanısında bilgisayar destekli sistemler büyük bir kolaylık sağlamaktadır. Bu proje, beyin MRI (Manyetik Rezonans Görüntüleme) görüntülerinden faydalanarak, bir kişide tümör olup olmadığını belirlemeyi amaçlayan basit bir yapay zekâ uygulamasıdır.

Projede, bilgisayarların görsel verileri analiz etmesini sağlayan “derin öğrenme” yöntemlerinden yararlanılmıştır. Derin öğrenme, insan beyninin öğrenme şeklini taklit eden yapay sinir ağları üzerine kuruludur. Model, daha önce pek çok farklı görüntü üzerinde eğitilmiş hazır bir yapıyı (InceptionResNetV2) temel alarak geliştirilmiştir. Bu sayede sıfırdan eğitim gerektirmeden, kısa sürede yüksek doğruluk oranına ulaşılmıştır.

Veri seti, tümör bulunan ve bulunmayan beyin MRI görüntülerinden oluşmaktadır. Görseller bilgisayara tanıtılmış, ardından model bu görüntüleri analiz ederek hangi özelliklerin tümörle ilişkili olduğunu öğrenmiştir. Eğitim tamamlandıktan sonra model test edilerek, yeni bir MRI görüntüsünde tümörün varlığını yaklaşık %85 doğruluk oranıyla tahmin edebilmiştir.

Bu çalışma, tıp alanında yapay zekânın ne kadar etkili olabileceğini küçük bir ölçekte de olsa göstermektedir. Böyle bir sistem doktorların karar verme sürecine destek olabilir, ön tanı koymayı hızlandırabilir ve insan hatasını en aza indirebilir. Gelecekte daha geniş veri setleriyle ve daha gelişmiş modellerle bu tür projelerin doğruluk oranlarının çok daha yüksek seviyelere ulaşması beklenmektedir.

## Elde Edilen Sonuçlar ve Görseller

Proje kapsamında model, beyin MRI görüntülerini inceleyerek tümörlü ve tümörsüz örnekleri birbirinden ayırmayı öğrenmiştir. Eğitimin ardından yapılan testlerde yaklaşık %85 doğruluk oranı elde edilmiştir. Bu sonuç, küçük bir veri setiyle çalışılmış olmasına rağmen modelin genel olarak doğru tahminlerde bulunabildiğini göstermektedir.

Eğitim süreci boyunca modelin başarı ve kayıp değerleri grafikler halinde izlenmiştir. Bu grafiklerde, her dönem (epoch) sonunda modelin hatalarının azaldığı ve doğruluğun arttığı görülmüştür. Ayrıca rastgele seçilen örnek MRI görüntüleri görselleştirilmiş, her birinin doğru şekilde “tümör var” veya “tümör yok” olarak sınıflandırıldığı gözlemlenmiştir.
