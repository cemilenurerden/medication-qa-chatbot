**Medication QA Chatbot**

Bu proje, ilaçlarla ilgili soruları yanıtlayan bir sohbet botu geliştirmeyi amaçlamaktadır. Temel olarak kullanıcının sorusuna en benzer soruyu eğitim verisinde bulup karşılık gelen cevabı döndüren bir retrieval sistemi üzerine kurulmuştur.

**Veri Seti**

Hugging Face üzerindeki truehealth/medicationqa veri seti kullanılmıştır. Bu veri seti ilaçlara yönelik gerçek kullanıcı sorularını ve yanıtlarını içermektedir.

**Nasıl Çalışır**

Önce sorular ve cevaplar vektöre dönüştürülür. Kullanıcı bir soru sorduğunda bu soru da vektöre çevrilir ve eğitim setindeki en benzer soruyla cosine similarity kullanılarak eşleştirilir. Bulunan sorunun cevabı kullanıcıya döndürülür.

Bunun yanında kullanıcının sorusunun hangi kategoriye girdiği (doz, yan etki, etkileşim vb.) Logistic Regression ile tahmin edilir ve cevaba eklenir.

**Model**

sentence-transformers/all-MiniLM-L6-v2 modeli kullanılmış ve soru-cevap çiftleri üzerinde MultipleNegativesRankingLoss ile 3 epoch fine-tune edilmiştir. Eğitim Google Colab T4 GPU üzerinde yapılmıştır.



**Çalıştırma**

Notebook Google Colab'da açılıp sırayla çalıştırılabilir. İlk hücre gerekli kütüphaneleri otomatik olarak yükler. Son hücre Gradio arayüzünü başlatır ve konsolda bir public URL üretir.

**Gereksinimler**

transformers, datasets, gradio, torch, scikit-learn, rouge-score, sentence-transformers
