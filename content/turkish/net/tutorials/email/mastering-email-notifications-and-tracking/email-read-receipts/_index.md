---
title: Aspose.Email for .NET ile E-posta Okundu Bilgileri
linktitle: Aspose.Email for .NET ile E-posta Okundu Bilgileri
second_title: Aspose.Email .NET E-posta İşleme API'si
description: Aspose.Email for .NET kullanarak e-posta okundu bilgisi istemeyi öğrenin. Geliştiricilerin C# dilinde okuma izlemeyi uygulaması için adım adım kılavuz.
type: docs
weight: 11
url: /tr/net/tutorials/email/mastering-email-notifications-and-tracking/email-read-receipts/
---
## giriiş

Hiç bir e-posta gönderip alıcının ne zaman açtığını bilmeyi istediniz mi? E-posta okundu bildirimlerini girin; bu özellik, mesajınızın okunup okunmadığını takip etmenizi sağlar. Bu eğitimde, .NET için Aspose.Email kullanarak e-posta okundu bildirimlerini nasıl isteyeceğinizi adım adım anlatacağız. Geliştiriciyseniz, bu, yalnızca birkaç satır kodla e-posta iletişimini kolaylaştırma şansınız!

Ortamınızı kurmaktan e-postayı izleme etkinleştirilmiş şekilde göndermeye kadar her adımı açıklayacağız. Bu eğitimin sonunda, bu özelliği uygulamada profesyonel olacaksınız!

## Ön koşullar

Koda dalmadan önce aşağıdakilerin hazır olduğundan emin olun:

1.  Aspose.Email for .NET kütüphanesi kuruldu.[Buradan indirin](https://releases.aspose.com/email/net/).
2. Kimlik bilgilerine sahip geçerli bir SMTP sunucusu (ana bilgisayar, kullanıcı adı, şifre).
3. Visual Studio veya uyumlu herhangi bir IDE.
4. .NET Framework kurulu.
5.  A[geçici lisans](https://purchase.aspose.com/temporary-license/) eğer deneme sürümünü kullanıyorsanız.

## Paketleri İçe Aktar

Başlamak için, projenize gerekli ad alanlarını eklemeniz gerekir. Bu ad alanları, e-posta göndermek ve okundu bilgisi istemek için gereken sınıfları ve yöntemleri sağlar.

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Smtp;
using Aspose.Email.Mime;
```

## Adım 1: Bir E-posta Mesajı Oluşturun

 İlk adım, bir örnek oluşturmaktır`MailMessage` Göndermek istediğiniz e-postayı temsil eden sınıf.

```csharp
MailMessage message = new MailMessage();
```

 The`MailMessage` nesne, gönderici, alıcı, konu, gövde ve başlıklar gibi özellikleri ayarlayacağınız boş tuvalinizdir. Bunu, en sevdiğiniz istemcide bir e-posta taslağı hazırlamak olarak düşünün.

## Adım 2: Gönderen ve Alıcı Ayrıntılarını Ayarlayın

Gönderenin e-posta adresini, alıcının e-posta adresini ve konu ve gövde gibi diğer önemli özellikleri belirtin.

```csharp
message.From = "sender@sender.com";
message.To.Add("receiver@receiver.com");
message.Subject = "Requesting Read Receipt";
message.HtmlBody = "<html><body>This is the HTML body</body></html>";
```

Burada, göndericinin ve alıcının e-posta adreslerini atıyoruz. Ayrıca, cilalı görünmesi için HTML kullanarak e-postanın konusunu ve gövdesini tanımlıyoruz.

## Adım 3: Teslimatı ve Okundu Bildirimlerini Etkinleştirin

Teslimat ve okundu bildirimleri istemek için başlıklar ekleyin. Bu başlıklar, alıcının e-posta sunucusuna e-posta teslim edildiğinde veya açıldığında sizi bilgilendirmesini söyler.

```csharp
message.DeliveryNotificationOptions = DeliveryNotificationOptions.OnSuccess;
message.Headers.Add("Return-Receipt-To", "sender@sender.com");
message.Headers.Add("Disposition-Notification-To", "sender@sender.com");
```

- DeliveryNotificationOptions: E-posta başarıyla teslim edildiğinde bir onay ister.
- Return-Receipt-To: E-posta okunduğunda bir makbuz ister.
- Disposition-Notification-To: Okundu bilgisi için kullanılan özel bir başlık.

## Adım 4: SMTP İstemcisini Yapılandırın

 Bir örneğini oluşturun`SmtpClient` sınıfını açın ve SMTP sunucunuzun ayrıntılarıyla yapılandırın.

```csharp
SmtpClient client = new SmtpClient
{
    Host = "smtp.server.com",
    Username = "Username",
    Password = "Password",
    Port = 25
};
```

 The`SmtpClient` e-postanızın gönderilmesini yönetir. Değiştir`"smtp.server.com"`, `"Username"` , Ve`"Password"` SMTP sunucunuzun bilgileriyle.

## Adım 5: E-postayı gönderin

 Kullanın`Send` yöntemi`SmtpClient` E-postanızı göndermek için. Sorunsuz yürütmeyi sağlamak için istisnaları işleyin.

```csharp
try
{
    client.Send(message);
    Console.WriteLine("Message sent");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

- client.Send(mesaj): Hazırlanan e-postayı gönderir.
- İstisna İşleme: Hatalı sunucu bilgileri veya bağlantı sorunları gibi sorunları günlüğe kaydeder.

## Çözüm

Ve işte bu kadar! Aspose.Email for .NET kullanarak e-posta okundu bildirimleri istemek için bir sistemi başarıyla uyguladınız. Bu özellik, önemli e-postaların hak ettikleri ilgiyi görmesini sağlamak için oyunun kurallarını değiştiriyor. İster işlemsel e-postalar ister önemli iş güncellemeleri gönderiyor olun, okundu bildirimlerini izlemek fazladan bir hesap verebilirlik katmanı sağlar.

## SSS

### E-postalarda okundu bilgisi nedir?
Okundu bildirimleri, alıcı e-postanızı açtığında aldığınız bildirimlerdir. Mesajınızın okunduğuna dair onay sağlarlar.

### Tüm e-postalar için okundu bilgisi talep edebilir miyim?
Tüm e-posta istemcileri okundu bildirimlerini desteklemez ve alıcılar bunları göndermeyi reddedebilir.

### Aspose.Email for .NET ücretsiz mi?
 Bir tane kullanabilirsiniz[ücretsiz deneme sürümü](https://releases.aspose.com/) veya bir lisans satın alın[Aspose web sitesi](https://purchase.aspose.com/buy).

### Aspose.Email e-posta göndermek için ne kadar güvenli?
Aspose.Email, güvenli e-posta iletişimi için SSL/TLS şifrelemesi de dahil olmak üzere güçlü güvenlik özellikleri sunar.

### E-posta başlıklarını daha fazla özelleştirebilir miyim?
Evet, Aspose.Email belirli gereksinimler için özel başlıklar eklemenize olanak tanır.[belgeleme](https://reference.aspose.com/email/net/) Ayrıntılar için.