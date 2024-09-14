
![GXbm5mtaEAAzb4q](https://github.com/user-attachments/assets/d5b850d4-866b-4904-9857-93b584dd1dac)

------

<b> Dill Alps testnet düğümünü (Node) çalıştırmak için minumum donanım gereksinimleri </b>

# Light Validator Donanım Gereksinimleri
| Donanım | Gereksinimleri | Donanım |
| ------------- | ---------------- | ---------------- |
Cpu | 2 Cores | fefe
Architecture | x86-64 (x64, x86_64, AMD64, ve Intel 64)
Memory | 2 GB
Operating System | Ubuntu 22.04.2 LTS or higher versions (x86-64)
Storage | 20 GB
Network Bandwidth | 1MB/s 

# Full Validator Donanım Gereksinimleri
| Donanım | Gereksinimleri |
| ------------- | ---------------- |
Cpu | 4 Cores
Architecture | x86-64 (x64, x86_64, AMD64, ve Intel 64)
Memory | 8 GB
Operating System | Ubuntu 22.04.2 LTS or higher versions (x86-64)
Storage | 256 GB
Network Bandwidth | 64Mb/s 

# Dill Public Testnet (Alps Testnet) Bilgileri
| Network Name     | Dill Testnet Alps |
| ------------- | ---------------- |
Ağ Adı | Alps Testnet
Rpc URL | https://rpc-andes.dill.xyz/
Chain ID | 102125
Currency Symbol | DILL
Explorer URL | https://andes.dill.xyz/


## Kurulum Talimatları

- İlk olarak terminali açın. Daha sonra aşağıdaki komutu çalıştırın.

```
curl -sO https://raw.githubusercontent.com/DillLabs/launch-dill-node/main/dill.sh  && chmod +x dill.sh && ./dill.sh
```
- Kurulumu başlattıktan sonra ```Please choose an option for your purpose [1, Launch a new dill node, 2, Add a validator to existing node]``` seçimi gelecek karşınıza. Buraya 1 yazıp, entere basın. 
- Gerekli dosyaları indirmeye başlayacak. ```Step 1 Completed. Press any key to continue...``` çıktsını aldıktan sonra herhangi bir tuşa basın ve devam edin.
- Yeni bir mnemonic oluşturacaksınız 1'i seçin ya da mevcut Mnemonic'lerinizi kullanacaksınız 2'yi seçerek enter'a basın. Kelimelerinizi kaydetmeyi unutmayın. Ayrıca oluşan kelimelerini ```dill/validator_keys/mnemonic-xxxxxx.txt``` dizininde bu dosyada görebilirsiniz. (bu dosyayı yedekleyemeyi kesinlikle unutmayın. Eğer node'nuzu başka bir sunucuya taşımak isterseniz bu lazım olacak.)
- Kelimeleriniz oluştuktan sonra random olarak Validator Keystore şifrenizi oluşturulacak. Bunu da kaydedin. Gene aynı şekilde random oluşan şifrenizi ```dill/validator_keys/keystore_password.txt``` dosyasında görebilirsiniz. Tekrar herhangi bir tuşa basın.
- Full validator ve light validator kurulumunu için token stake miktarları değişiktir. Bunun için karşınıza şöyle bir seçenecek gelecek, ```Please choose an option for deposit token amount [1, 3600, 2, 36000]``` Siz ligth validator için seçildiyseniz 1, eğer full validator için seçildiyseniz 2 yazıp entere basın.
- Sonra ki adımda ```Please enter your withdrawal address:``` seçeneği gelecek. Burada Dill Discord'unda ki faucette hangi metamask adresinize tokenleri talep ettiyseniz o adresinizi 2 kere girin.
- ```Step 2 Completed. Press any key to continue...``` çıktısını alınca tekrar herhangi bir tuşa basın ve kuruluma devam edin.
- En sonda ```node running, congratulations``` çıktısı validator_pubkeyinizi ve alacaksınız ve kurulum tamamlanacak.

## Staking

Not: Node'unuz sync olduktan sonra staking işlemlerini yapmanız tavsiye edilir. Sync kodunu reponun en altına ekledim. Kontrol edebilirsiniz.

  - Öncelikle, Alps kanalından faucet'ten token talep edin. Node'da oluşturduğunuzdan farklı bir cüzdan kullanın ve faucet'i yalnızca bir kez alabileceğinizi unutmayın ($request xxxxx).
  - https://staking.dill.xyz/ adresini ziyaret edin.

![image](https://github.com/user-attachments/assets/3c24ea5d-c728-4ee7-87f3-b2a42abd5dd5)

- Bu siteye deposit_data-xxxxx.json dosyanızı yükleyeceksiniz. Bu dosyayı sunucunuzun içinde ```/dill/validator_keys``` dizininden bulup alabilirsiniz.(WinSCP, Mobaxterm gibi uygulamarı kullanabilirsiniz.)
- Deposit_data-xxxx.json dosyasını siteye yükledikten sonra MetaMask'a Bağlan'a tıklayın, yeterli test tokeniniz olduğundan emin olun (>3600 DILL)

 ![image](https://github.com/user-attachments/assets/f8238c5a-b216-476c-a5a3-18fc919211b6)

- Cüzdanı bağladıktan sonra Continue'ya basarak devam edin. Ardından Confirm deposit'e basarak depositini gerçekleştirin.

![Ekran görüntüsü 2024-09-14 075934](https://github.com/user-attachments/assets/8f9bcb6a-ddfd-41cf-b202-fc99e5bba489)

- Staking sürecini tamamladıktan sonra, validator public anahtarınızı kullanarak sayfada validator bilgilerinizi arayabilirsiniz. Görünmesi 0,5-1 saat sürebilir.

![Ekran görüntüsü 2024-09-14 080323](https://github.com/user-attachments/assets/1539f0ca-324c-4188-97ea-a279b50d28ab)


## Önemli Komutlar

- Eğer Dill dizininde değilseniz, bu komutla Dill dizinine geçebilirsiniz. (Komutları "dill" dizininde çalıştırmanız gerekiyor)
```
cd dill 
```

- Node'un çalışıp çalışmadığını kontrol etmek için
```
./health_check.sh -v
```

- Node sync olup olmadığını kontrol etmek için. Eğer bunun gibi bir çıktı alıyorsanız node sync olmuş demektir. ({"head_slot":"173420","sync_distance":"0","is_syncing":false,"is_optimistic":false,"el_offline":false}}
```
curl -s localhost:3500/eth/v1/node/syncing
```
