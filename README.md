# signature-verification-AKBANK

Veri seti, gerçek ve sahte imzaları içermektedir. Eğitim, doğrulama ve test için stratified split uygulanmıştır. Sınıflar dengeli dağıtılmıştır (≈ %53 genuine, %47 forged)

<img width="771" height="486" alt="image" src="https://github.com/user-attachments/assets/63c77b40-d8ad-4465-8870-e798b5c692c8" />

----
Sıfırdan küçük bir CNN modeli ile baseline kuruldu. Ancak model sahte imzaları hiç yakalayamadı (forged için precision=recall=0). Bu, modelin naive olarak tüm örnekleri genuine sınıfına atadığını gösteriyor. Accuracy ≈ %50 seviyesinde kaldı.

<img width="314" height="668" alt="image" src="https://github.com/user-attachments/assets/9c1eed6d-b706-4e3f-89bd-ebbac4fe57f8" />

--

<img width="423" height="455" alt="image" src="https://github.com/user-attachments/assets/1e923020-76d6-478e-b3dd-c5baa8c35f94" />

------

Grad-CAM ile baseline modelin hangi bölgelere dikkat ettiği incelendi. Model, çoğunlukla rastgele bölgeleri vurguladı ve imzanın ayırt edici kısımlarını yakalayamadı.


<img width="312" height="669" alt="image" src="https://github.com/user-attachments/assets/6ff5a07b-30da-43df-a8e3-91c08d9b0a2a" />

-----


EfficientNetV2B0 ön-eğitimli ağırlıkları dondurulmuş haliyle denendi. Baseline’a göre sahte imzaları yakalamada daha iyi oldu (forged recall %25’e çıktı). ROC-AUC 0.68’e yükseldi.


<img width="221" height="606" alt="image" src="https://github.com/user-attachments/assets/75b80d06-7151-406d-82e5-18f98f0ddac5" />


------

“Threshold tuning ile karar eşiği yeniden ayarlandı. Baseline model tuned durumda %92 accuracy’ye ulaştı, sahte imza recall’ı %0.88 oldu. EfficientNet ise daha istikrarlı sonuçlar verdi ama forged recall düşük kaldı.

<img width="319" height="670" alt="image" src="https://github.com/user-attachments/assets/ef75f944-cda1-493f-9a73-9ac2b5b952a9" />

---


Son adımda EfficientNetV2B0’un son 20 katmanı açılarak ince ayar yapıldı. 3 epoch fine-tuning sonrası en yüksek performans elde edildi: accuracy ≈ %90, ROC-AUC ≈ 0.97. Forged ve genuine sınıflarında dengeli sonuç verdi.

--

Bu çalışmada baseline CNN’den transfer learning’e geçişin etkisi görüldü. Baseline model sahte imzaları hiç yakalayamazken, EfficientNetV2B0 + fine-tuning %90+ doğruluk seviyesine ulaştı. Threshold tuning ve Grad-CAM analizleriyle modelin davranışı derinlemesine incelendi.

-

https://www.kaggle.com/code/ahmetburakkorkut/akbank-bootcamp-ahmet-burak-korkut
https://www.kaggle.com/code/ahmetburakkorkut/akbank-bootcamp-ahmet-burak-korkut
