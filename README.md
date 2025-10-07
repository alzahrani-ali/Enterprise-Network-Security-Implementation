# Enterprise-Network-Security-Implementation


 # تأمين شبكة متكاملة باستخدام OSPF، VLANs، وحلول أمان متعددة الطبقات







# مشروع تعزيز أمان الشبكة – تطوير لمشروع OSPF_VLAN_DHCP_LAB

## فكرة المشروع  
بعد ما أنهيت مشروع [OSPF_VLAN_DHCP_LAB](https://github.com/Ali-ssz/OSPF_VLAN_DHCP_LAB)، قررت أطور الشبكة من ناحية الأمان بحيث تكون أقرب لبيئة عمل حقيقية.  
ركزت في هذا المشروع على حماية السيرفرات، تأمين المنافذ، وتفعيل مصادقة OSPF بين الراوترات لضمان أن التواصل يتم فقط بين الأجهزة الموثوقة.

<img width="1918" height="992" alt="Topology" src="https://github.com/user-attachments/assets/8f311fbf-1683-454e-bbab-f3fb6c725e3a" />


---



## 1️ حماية الشبكة باستخدام ACL  
- إنشاء **قائمتين للتحكم بالوصول (ACLs)**:
  - الأولى لمنع أجهزة **Guest VLAN** من التواصل مع أي VLAN أخرى، مع السماح لهم فقط بالحصول على IP من DHCP Server.  
  - الثانية لمنع جميع الـ VLANs من التواصل المباشر مع **DHCP Server** باستثناء المنافذ الخاصة بـ **DHCP (ports 67 و68)**.  
- حجب أي محاولة Ping أو اكتشاف من أجهزة خارجية.  
- الحفاظ على استمرارية الخدمات بدون التأثير على أداء الشبكة.

<img width="868" height="229" alt="ACL-Server" src="https://github.com/user-attachments/assets/44d1e507-134f-4b62-8375-73a5bc28be2b" /> <img width="868" height="233" alt="ACL-Guest" src="https://github.com/user-attachments/assets/c2884fc7-be2b-4958-b705-f1e154ccbcd0" />

  
*تطبيق ACL للتحكم في حركة المرور وضمان الوصول المصرح فقط.*

---



## 2️ أمان المنافذ (Port Security)  
- تفعيل **Port Security** على جميع المنافذ.  
 - تم تطبيق إعدادين مختلفين:
 - على منفذ السيرفر وضعنا Shutdown
 - على منافذ المستخدمين لتسجيل الانتهاكات بدون إيقاف المنفذ وضعنا Restrict 
 - ضبط عدد العناوين المسموح بها:
  - **السيرفر:** 1 عنوان MAC فقط.  
  - **الأقسام الأخرى:** 3 عناوين MAC كحد أقصى.  

  <img width="865" height="340" alt="Port-Security-config" src="https://github.com/user-attachments/assets/5004dc54-114f-456d-a8eb-a7cf778c6935" />

*تطبيق Port Security على السويتشات لحماية المنافذ والتحكم بالوصول.*

---

## 3️ تأمين بروتوكول التوجيه (OSPF Authentication)  
- تفعيل مصادقة **MD5** على جميع الراوترات المشاركة في OSPF.  
- ضمان أن تبادل التحديثات يتم فقط بين الراوترات الموثوقة.  
- تقليل احتمالية حقن جداول توجيه مزيفة داخل الشبكة.

<img width="778" height="33" alt="OSPF-Auth" src="https://github.com/user-attachments/assets/15e12e56-2f6c-4940-a20b-0fcb2cf8d8df" />
  
*تفعيل OSPF Authentication باستخدام MD5 لحماية التوجيه الديناميكي.*

---

## 📊 اختبارات الأمان

---
- اختبار منع اتصال Guest VLAN مع الشبكات الأخرى

<img width="863" height="206" alt="Ping-From-Guest" src="https://github.com/user-attachments/assets/57bdd387-84e5-459c-a4f2-b0432e749f8d" />

---

- اختبار حماية منفذ السيرفر (Port Security)

  <img width="866" height="220" alt="Port-Security-Violation" src="https://github.com/user-attachments/assets/5135e228-f5ff-4770-b9e0-862399f1ab6c" />
  
 ---

- اختبار مصادقة OSPF بين الراوترات

<img width="818" height="55" alt="OSPF-Neighbors-Success" src="https://github.com/user-attachments/assets/49bac78f-b4ba-4ba6-b6bf-ea6d3c4daaff" />

---



##  رابط المشروع السابق  
- المشروع الأساسي: [OSPF_VLAN_DHCP_LAB](https://github.com/Ali-ssz/OSPF_VLAN_DHCP_LAB)

---


 # هذا المشروع جزء من سلسلة مشاريع عملية أطورها لتقوية مهاراتي في تصميم وتأمين الشبكات باستخدام Cisco Packet Tracer.

---


LinkedIn : https://www.linkedin.com/in/ali-alzahrani-b8a7a3347/

Email : alzahrani_ali@outlook.com
