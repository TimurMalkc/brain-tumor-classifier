# brain-tumor-classifier
## Beyin Tümörü Tespiti (MRI Görüntülerinden Derin Öğrenme ile Sınıflandırma)

Son yıllarda yapay zekâ, sağlık alanında en çok ilgi gören teknolojilerden biri haline gelmiştir. Özellikle beyin tümörü gibi erken teşhisi hayati önem taşıyan hastalıkların tanısında bilgisayar destekli sistemler büyük bir kolaylık sağlamaktadır. Bu proje, beyin MRI (Manyetik Rezonans Görüntüleme) görüntülerinden faydalanarak, bir kişide tümör olup olmadığını belirlemeyi amaçlayan basit bir yapay zekâ uygulamasıdır.

Projede, bilgisayarların görsel verileri analiz etmesini sağlayan “derin öğrenme” yöntemlerinden yararlanılmıştır. Derin öğrenme, insan beyninin öğrenme şeklini taklit eden yapay sinir ağları üzerine kuruludur. Model, daha önce pek çok farklı görüntü üzerinde eğitilmiş hazır bir yapıyı (InceptionResNetV2) temel alarak geliştirilmiştir. Bu sayede sıfırdan eğitim gerektirmeden, kısa sürede yüksek doğruluk oranına ulaşılmıştır.

Veri seti, tümör bulunan ve bulunmayan beyin MRI görüntülerinden oluşmaktadır. Görseller bilgisayara tanıtılmış, ardından model bu görüntüleri analiz ederek hangi özelliklerin tümörle ilişkili olduğunu öğrenmiştir. Eğitim tamamlandıktan sonra model test edilerek, yeni bir MRI görüntüsünde tümörün varlığını yaklaşık %85 doğruluk oranıyla tahmin edebilmiştir.

Bu çalışma, tıp alanında yapay zekânın ne kadar etkili olabileceğini küçük bir ölçekte de olsa göstermektedir. Böyle bir sistem doktorların karar verme sürecine destek olabilir, ön tanı koymayı hızlandırabilir ve insan hatasını en aza indirebilir. Gelecekte daha geniş veri setleriyle ve daha gelişmiş modellerle bu tür projelerin doğruluk oranlarının çok daha yüksek seviyelere ulaşması beklenmektedir.

