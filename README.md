# Brute-It-CTF
Brute It CTF Write up



اول شي نسوي فحص للخدمات والمنافذ المفتوحة على السيرفر باداة nmap او اي اداة بديلة 

![nmap](https://user-images.githubusercontent.com/73380139/183870835-7ae16a83-cbca-4d32-bb3c-4973f65946f0.png)

ونسوي فحص للمسارات المخفية باداة dirSearch
![dir](https://user-images.githubusercontent.com/73380139/183871211-ed09e4f3-9b4d-4f58-af90-1604265b4050.png)

حصلنا مسار يودي على صفحة دخول الادمن, ولما نسوي انسبكت راح نشوف ملاحظة  
![enspect](https://user-images.githubusercontent.com/73380139/183871465-c2822c2d-04a6-4e9e-bed0-a7fc683f1f2a.png)

الحين راح نسوي هجوم brute force attack عشان نخمن كلمة مرور الادمن باداة hydra او اي اداة بديلة 

![hydra](https://user-images.githubusercontent.com/73380139/183872093-1d9db62c-f724-4152-adc5-4ec70357dafa.png)

نسجل دخول وناخذ العلم web flag
![adminPanel](https://user-images.githubusercontent.com/73380139/183872937-c7d30a07-ba35-4383-8145-93916adce9b7.png)


نحفظ مفتاح RSA حق الادمن عشان نستخدمة في تسجيل دخول SSH

![id_rsa](https://user-images.githubusercontent.com/73380139/183873604-5a3fe2f4-3a93-4c66-89e6-f280ac706cf1.png)

الحين لازم نحول الملف الى هاش بصيغة ملف txt عشان نقدر نكسرة باداة john
في البداية راح نجيب سكربت ssh2john.py ونحول ملف الـRSA الى هاش 

![locate_ssh2john_cp](https://user-images.githubusercontent.com/73380139/183873964-bb40d3a6-ad6b-4ce8-97f1-bcd2070b760b.png)

نحول الـRSA الى هاش باهذا الامر 

![rsaToHash](https://user-images.githubusercontent.com/73380139/183874566-6efdb7fb-f476-4667-b2d4-8acefc28d57a.png)

والحين نخمن الباسورد من خلال الهاش باستخدام brute force attack 

![hashPassCrack](https://user-images.githubusercontent.com/73380139/183873958-bf37d4f6-70db-4c35-a294-5603b0d4a808.png)

الحين نسجل دخول SSH وناخذ user flag 

![sshAndUserFlag](https://user-images.githubusercontent.com/73380139/183884018-5b79089a-2669-44df-b78f-8f1a22579a7a.png)



وعشان نلتقط علم الروت root flag راح نحتاج نصعد صلاحياتنا
من خلال الامر sudo -l راح نلاحظ ان المسار bin/cat له صلاحيات الروت بدون باسورد 


![sudo-l](https://user-images.githubusercontent.com/73380139/183884447-967e6cb1-e126-4150-b4d0-1508c2bca214.png)


من خلال المسار السابق راح نحاول نقراء ملف shadow عشان نحصل على هاش باسورد الروت 

![rootHash](https://user-images.githubusercontent.com/73380139/183892698-d0a485b3-fec0-41de-a4d6-afdc909a49ff.png)


نحفظ هاش الروت في ملف txt ونكسره باداة john


![rootHashBrutF](https://user-images.githubusercontent.com/73380139/183873965-9fa91ccb-0e25-4148-9a70-0b9685f8c5f8.png)


الحين نسوي سويتش من خلال الامر su root ونحط الباسورد اللي حصلنا علية قبل شوي 

![suRoot](https://user-images.githubusercontent.com/73380139/183893549-7c93b430-0d47-4322-bfca-787582b7b38c.png)


والحين حصلنا على العلم الخاص بالروت root flag


![rootFlag](https://user-images.githubusercontent.com/73380139/183893792-f595f572-ef9c-4f8d-92ae-547a0a041c12.png)





