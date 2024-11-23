# Aygaz Veri Analizi Projesi

## Proje Hakkında
NASA Near Earth Objects veri seti kullanılarak yapılan veri analizi projesi.
(Kaggle Linki: https://www.kaggle.com/code/yasincanyilmazoglu/earth-objects-aygaz-data-analysis)

## Veri Seti
- Kaynak: Kaggle NASA NEO Dataset (https://www.kaggle.com/datasets/sameepvani/nasa-nearest-earth-objects)
- Boyut: [9.48 MB]
- Değişken Sayısı: [10]
  ['id', 'name', 'est_diameter_min', 'est_diameter_max', 'relative_velocity', 'miss_distance', 'orbiting_body', 'sentry_object', 'absolute_magnitude', 'hazardous']

## Analiz Adımları
1. Veri Ön İşleme
2. Eksik Veri Analizi
3. Görselleştirmeler
4. İstatistiksel Analizler

## Kullanılan Teknolojiler
- Python
- Pandas
- NumPy
- Seaborn
- Matplotlib

## Veri Ön İşleme ve Temizleme
Veri setine random NaN değerler eklendi ve sayısal değişkenler için median değerleri kullanılarak eksik veriler dolduruldu.

## Eksik Veri Analizi
### Temizleme Öncesi Eksik Değerler

### Temizleme Sonrası Eksik Değerler

## Görselleştirmeler ve Analizler

### Tehlikeli vs Tehlikesiz Asteroidlerin Dağılımı
<img src="img/hazardous_asteroids.png" width="400" height="200">

#### Tehlikeli ve Tehlikesiz Asteroidlerin Dağılım Analizi

Çubuk grafik analizine göre:
- Asteroidlerin büyük çoğunluğu (yaklaşık 75.000) tehlikesiz olarak sınıflandırılmış.
- Çok daha az sayıda (yaklaşık 8.000) asteroid tehlikeli kategorisinde.
- Tehlikesiz ve tehlikeli asteroidler arasında yaklaşık 9:1 oranı mevcut.

**Bu görselleştirme, veri tabanımızdaki asteroidlerin yalnızca küçük bir yüzdesinin Dünya için potansiyel tehlike oluşturduğunu açıkça ortaya koymaktadır.**

### Asteroidlerin Çap Dağılımı Analizi
<img src="img/asteroid_diameters.png" width="400" height="200">

### Hız ve Mesafe İlişkisi
<img src="img/distance-velocity.png" width="400" height="200">

### Box-Plot Diyagramı ve Analizi
<img src="img/box-plot.png" width="400" height="200">

### Korelasyon Matrisi Analizi
<img src="img/Correlation.png" width="400" height="200">

### Güçlü Korelasyonlar
- est_diameter_min ve est_diameter_max arasında mükemmel korelasyon (1.0) bulunması, aynı özelliği ölçtüklerini gösteriyor.
- Mutlak parlaklık (absolute_magnitude) ile çap ölçümleri arasında güçlü negatif korelasyon (-0.55) var, bu büyük objelerin daha düşük mutlak parlaklığa sahip olduğunu gösteriyor.

### Orta Düzey Korelasyonlar
- Göreceli hız (relative_velocity) ve kaçırma mesafesi (miss_distance) arasında orta düzey pozitif korelasyon (0.33).
- Göreceli hız ve mutlak parlaklık arasında orta düzey negatif korelasyon (-0.35).

### Tehlike Sınıflandırması İçin Önemli Bulgular
1. Çap ölçümleri birbiriyle tamamen ilişkili olduğundan birini kullanmak yeterli.
2. Mutlak parlaklık, birçok değişkenle ilişkili olduğu için iyi bir tahmin değişkeni olabilir.
3. Hız ve mesafe arasındaki ilişki, tehlike değerlendirmesinde önemli olabilir.
4. Çoğu değişken birbirinden bağımsız, bu da sınıflandırma için benzersiz bilgiler sağlayabileceklerini gösteriyor.

## Sonuç ve Öneriler

### İş Problemi ve Kullanım Senaryoları
Uzay madenciliği ve savunma şirketleri için asteroidlerin tehlike seviyelerini ve potansiyel değerlerini değerlendiren bir risk analiz sistemi geliştirilebilir. Bu sistem:
- Asteroidlerin Dünya'ya çarpma risklerini değerlendirir.
- Potansiyel tehlikeli asteroidleri erken tespit eder.
- Uzay madenciliği için uygun asteroidleri belirler.

### Önerilen ML Çözümü
**Random Forest veya XGBoost Sınıflandırma** algoritması önerilir çünkü:
- Veri setimizde binary sınıflandırma problemi var (hazardous/non-hazardous)
- Çoklu değişken ilişkilerini iyi yakalar.
- Sayısal ve kategorik değişkenlerle çalışabilir.
- Aykırı değerlere karşı dirençlidir.
- Feature importance (özellik önemi) analizi sağlar. Bu analiz, veri setindeki hangi değişkenlerin hedef sonuç üzerinde en önemli etkiye sahip olduğunu belirlememize yardımcı olan bir tekniktir.

### Kullanılacak Özellikler
- est_diameter_min/max: Asteroid boyutu
- relative_velocity: Göreceli hız
- miss_distance: Dünya'ya olan mesafe
- absolute_magnitude: Parlaklık değeri
