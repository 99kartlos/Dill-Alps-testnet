
![GXbm5mtaEAAzb4q](https://github.com/user-attachments/assets/d5b850d4-866b-4904-9857-93b584dd1dac)

------

# Validatör Donanım Gereksinimleri
| Donanım | Light Validatör | Full Validatör |
| ------------- | ---------------- | ---------------- |
İşlemci | 2 Cores | 4 Cores
İşletim Sistemi Mimarisi | x86-64 (x64, x86_64, AMD64, ve Intel 64) | x86-64 (x64, x86_64, AMD64, ve Intel 64)
Ram | 2 GB | 8 GB
İşletim Sistemi | Ubuntu 22.04.2 ya da daha yüksek versiyon (x86-64) | Ubuntu 22.04.2 ya da daha yüksek versiyon (x86-64)
Disk Boyutu | 20 GB | 256 GB
İnternet Bant Genişliği | 1MB/s | 64Mb/s

# Dill Public Testnet (Alps Testnet) Ağ Bilgileri
| Network Name     | Dill Testnet Alps |
| ------------- | ---------------- |
Ağ Adı | Alps Testnet
Rpc URL | https://rpc-andes.dill.xyz/
Chain ID | 102125
Currency Symbol | DILL
Explorer URL | https://andes.dill.xyz/


## Kurulum Talimatları

1- Aşağıda ki komutu çalıştırın.
```ABNF
curl -sO https://raw.githubusercontent.com/DillLabs/launch-dill-node/main/dill.sh  && chmod +x dill.sh && ./dill.sh
```
2- Kurulumu başlattıktan sonra ```Please choose an option for mnemonic source [1, From a new mnemonic, 2, Use existing mnemonic] [1]:``` seçimi gelecek karşınıza. Eğer yeni bir mnemonic ilr kurulum yapacaksanız  1 yazıp, var olan bir mnemonic ile kurulum yapacaksanız 2 yazıp entere basın. 

3- Gerekli dosyaları indirmeye başlayacak. ```Step 1 Completed. Press any key to continue...``` çıktsını aldıktan sonra herhangi bir tuşa basın ve devam edin.

4- Kurulum sırasında Mnemonic kısmına geldik. Eğer yeni Mnemonic oluşturacaksınız 1'i seçin ya da Andres testnetinden kalma Mnemoniclerinizi kullanacaksınız 2'yi seçerek enter'a basın. Kelimelerinizi kaydetmeyi unutmayın. Ayrıca oluşan Mnemonicleriniz ```dill/validator_keys/mnemonic-xxxxxx.txt``` dizininde bu dosyada görebilirsiniz.

> [!CAUTION]
> ```dill/validator_keys/mnemonic-xxxxxx.txt```dosyasını yedekleyemeyi kesinlikle unutmayın. Eğer node'nuzu başka bir sunucuya taşımak isterseniz bu lazım olacak.

5- Mnemonic'i oluştuktan sonra random olarak Validatör Keystore şifrenizi oluşturulacak. Bunu da kaydedin. Yine aynı şekilde random oluşan şifrenizi ```dill/validator_keys/keystore_password.txt``` dosyasında görebilirsiniz. Tekrar herhangi bir tuşa basın.

6- Full validatör ve light validatör kurulumunu için token stake miktarları değişiktir. Bunun için karşınıza şöyle bir seçenecek gelecek, ```Please choose an option for deposit token amount [1, 3600, 2, 36000]``` Siz ligth validatör için seçildiyseniz 1, eğer full validatör için seçildiyseniz 2 yazıp entere basın.

7- Bu adımda ```Please enter your withdrawal address:``` seçeneği gelecek. Dill Discord'unda ki faucetten hangi adresinize tokenleri talep ettiyseniz o adresinizi 2 kere girin.

8- ```Step 2 Completed. Press any key to continue...``` çıktısını alınca tekrar herhangi bir tuşa basın ve kuruluma devam edin.

9- En sonda kurulum sorunsuz tamamlandığı zaman ```node running, congratulations``` çıktısı verecek. Ayrıca çıktı da validator_pubkeyinizide verecek.


## Staking

1- Öncelikle, Alps kanalında ki faucet botundan token talep edin ($request cüzdanadresiniz). Düğümünüzde (Node) oluşturduğunuzdan cüzdandan farklı bir cüzdan kullanın.

2- https://staking.dill.xyz/ adresini ziyaret edin.

> [!CAUTION]
> Düğümünüz (Node) senkronize olduktan sonra staking işlemlerini yapmanız tavsiye edilir. Düğümün (Node) senkronize durumunu kontrol etmek için reponun en altında ki komutları kullanın lütfen.
> Faucet'ten yalnızca bir kez token talep edebileceğinizi unutmayın!

![image](https://github.com/user-attachments/assets/3c24ea5d-c728-4ee7-87f3-b2a42abd5dd5)

3- Bu siteye ```deposit_data-xxxxx.json``` dosyanızı yükleyeceksiniz. Bu dosyayı sunucunuzun içinde ```/dill/validator_keys``` dizininden bulup alabilirsiniz.(WinSCP, Mobaxterm gibi uygulamarı kullanabilirsiniz.)

4- ```Deposit_data-xxxx.json``` dosyasını siteye yükledikten sonra MetaMask'a Bağlana tıklayın, yeterli test tokeniniz olduğundan emin olun (>3600 DILL)

 ![image](https://github.com/user-attachments/assets/f8238c5a-b216-476c-a5a3-18fc919211b6)

5- Cüzdanı bağladıktan sonra Continue'ya basarak devam edin. Ardından ```Confirm Deposit```'e basarak tokenleri yatırın.

![Ekran görüntüsü 2024-09-14 075934](https://github.com/user-attachments/assets/8f9bcb6a-ddfd-41cf-b202-fc99e5bba489)

6- Staking sürecini tamamladıktan sonra, validator public anahtarınızı kullanarak sayfada validatör bilgilerinizi arayabilirsiniz. Validatörünüzün görünmesi 30 dk. ile 1 saat arasında sürebilir.

![Ekran görüntüsü 2024-09-14 080323](https://github.com/user-attachments/assets/1539f0ca-324c-4188-97ea-a279b50d28ab)


# Mevcut Node'a Validator Ekleme

- Eğer fazladan WL'niz varsa bunu mevcut Node'unuza yeni bir validator olarak ekleyebilirsiniz. Bunun için:
  - Sunucunuza girin ve ```dill/2_add_validator.sh``` komutunu çalıştırın.
  - Ardıdan mnemonic'leri gireceksiniz. Yeni bir mnemonic oluşturmak için ```1```'i seçin (bunu güvenli bir şekilde kaydettiğinizden emin olun).
Zaten bir mnemonic'iniz varsa ve kullanmak istiyorsanız ```2```'yi seçin.
```ABNF
    ********** Step 1: Generating Validator Keys **********
Validator Keys are generated from a mnemonic
Please choose an option for mnemonic source [1, From a new mnemonic, 2, Use existing mnemonic] [1]:
```
 - Şimdi Yatırılacak token miktarını seçeceğiz ve withdraw adresimizi gireceğiz. Light Validator için (3600 DILL) ```1```. seçeneği Full Validator (36000 DILL) için ```2```. seçeneği seçin. Ardından Withdraw adresinizi girin enter deyip tekrar girin ve onaylayın.
 - 
   > [!IMPORTANT]
   > Şimdi önemli kısma geldik. Burada bize ```Index``` numarası soracak. Mevcut Node'uzu index:0 olarak kabul edeceksiniz. Bu yüzden ekleyeceğiniz validatorün index'i ```1``` olacak. (Bundan sonra ekleyeeğiniz      validatörün indexi n+1 şeklinde gidecek. Yani 3. Validator için 2 olacak.).
 - Sonuç olarak ```1``` diyoruz!!!Dikkat etmeniz gereken bir husus daha Her validatorun PubKeyi farklı olacak. Indexleri doğru girerseniz zaten farklı olacaktır.
  
 - Evet Validator ekleme basitçe bu şekilde. Stake aşamasına geçebilirsiniz.
 - Mevcut Validatorlerinizi ```dill``` dizini içinde aşağıdaki komutu kullanarak görebilirsiniz:
   ```./show_pubkey```

## Önemli Komutlar

- Eğer Dill dizininde değilseniz, bu komutla Dill dizinine geçebilirsiniz. (Komutları "dill" dizininde çalıştırmanız gerekiyor)
```ABNF
cd dill 
```

- Node'un çalışıp çalışmadığını kontrol etmek için
```Processing
./health_check.sh -v
```

- Node sync olup olmadığını kontrol etmek için. Eğer bunun gibi bir çıktı alıyorsanız node sync olmuş demektir. ({"head_slot":"173420","sync_distance":"0","is_syncing":false,"is_optimistic":false,"el_offline":false}}
```ABNF
curl -s localhost:3500/eth/v1/node/syncing
```
