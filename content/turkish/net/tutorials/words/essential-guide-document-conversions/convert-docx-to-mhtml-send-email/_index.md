---
title: DOCX'i MHTML'e Dönüştürün ve .NET için Aspose.Words Kullanarak E-posta Gönderin
linktitle: DOCX'i MHTML'e Dönüştürün ve .NET için Aspose.Words Kullanarak E-posta Gönderin
second_title: Aspose.Words Belge İşleme API'si
description: Bu kapsamlı kılavuz, .NET'te Aspose.Words ve Aspose.Email kütüphanelerini kullanarak DOCX belgelerini MHTML formatına dönüştürme ve e-postayla gönderme konusunda adım adım bir eğitim sağlar.
type: docs
weight: 10
url: /tr/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## giriiş

Günümüzün dijital ortamında, belgeleri formatlar arasında dönüştürmek ve e-postayla göndermek yaygın bir görevdir. Bu kılavuz, .NET için güçlü Aspose.Words ve Aspose.Email kütüphanelerini kullanarak bir DOCX dosyasını MHTML formatına dönüştürme ve e-postayla gönderme konusunda size yol gösterecektir. Her adımı açıkça açıklayacağız ve kolayca takip edebilmenizi sağlayacağız. Başlayalım!

## Ön koşullar

İşleme başlamadan önce aşağıdaki ayarların yapıldığından emin olun:

1.  Aspose.Words for .NET: Kütüphaneyi şu adresten indirin ve kurun:[Aspose sürüm sayfası](https://releases.aspose.com/words/net/).
2.  Aspose.Email for .NET: Bu kütüphaneyi şu adresten indirin ve yükleyin:[Aspose sürüm sayfası](https://releases.aspose.com/email/net/).
3. .NET Framework: Bilgisayarınızda .NET Framework'ün yüklü olduğundan emin olun.
4. SMTP Sunucusu: E-posta göndermek için bir SMTP sunucusuna erişmeniz gerekecektir.

## Gerekli Ad Alanlarını İçe Aktarma

Projenizde Aspose.Words ve Aspose.Email'i kullanmak için gerekli ad alanlarını içe aktarmalısınız. Aşağıdaki using yönergelerini C# dosyanızın en üstüne ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Adım 1: DOCX Belgesini Yükleyin

 Dönüştürmek istediğiniz DOCX belgesini yükleyerek başlayın.`Document` Bunu başarmak için Aspose.Words sınıfından faydalanabilirsiniz.

```csharp
// Belge dizininize giden yolu belirtin.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Adım 2: Belgeyi MHTML olarak kaydedin

 Sonra, yüklenen belgeyi MHTML biçimine dönüştürün. Bu, şu şekilde yapılır:`Save` yöntemi`Document` sınıf.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Okuma için akış konumunu başa sıfırlayın.
    stream.Position = 0;
}
```

## Adım 3: Bir E-posta Mesajı Oluşturun

Şimdi, Aspose.Email kullanarak MHTML akışından bir e-posta mesajı oluşturun.`MailMessage` Bu amaçla sınıf.

```csharp
// MHTML akışını bir Aspose.Email MIME e-posta mesajına yükleyin.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Adım 4: E-postayı gönderin

 Son olarak, e-postayı bir SMTP istemcisi kullanarak gönderin. SMTP istemcisini sunucu ayrıntılarınızla yapılandırın ve`Send` mesajı gönderme yöntemi.

```csharp
// Aspose.Email kullanarak mesajı yapılandırın ve gönderin.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Çözüm

Tebrikler! Bir DOCX belgesini MHTML'ye başarıyla dönüştürdünüz ve Aspose.Words ve Aspose.Email for .NET kullanarak e-postayla gönderdiniz. Bu işlem belgeyi yüklemeyi, MHTML'ye dönüştürmeyi, bir e-posta mesajı oluşturmayı ve bir SMTP istemcisi aracılığıyla göndermeyi içerir. Bu adımlarla, uygulamalarınızda belgelerin dönüştürülmesini ve e-postayla gönderilmesini sorunsuz bir şekilde otomatikleştirebilirsiniz.

## SSS

### Bu yöntemi diğer belge biçimlerini dönüştürmek için kullanabilir miyim?
Kesinlikle! Aspose.Words çok çeşitli formatları destekler ve DOC, DOCX, RTF ve daha fazlasını MHTML'ye dönüştürmenize olanak tanır.

### E-postaya nasıl ek ekleyebilirim?
 Eklentileri kullanarak kolayca ekleyebilirsiniz.`Attachments` mülkiyeti`MailMessage` sınıf.

### Aspose.Words .NET Core ile uyumlu mu?
Evet, Aspose.Words .NET Core ile uyumludur ve bu sayede .NET Core uygulamalarında kullanılmaya uygundur.

### Aspose.Words ve Aspose.Email için lisansa ihtiyacım var mı?
 Evet, her iki kütüphane de lisans gerektirir. Değerlendirme amaçlı geçici bir lisansı şuradan alabilirsiniz:[Aspose satın alma sayfası](https://purchase.conholdate.com/temporary-license/).

### Daha fazla dokümanı nerede bulabilirim?
 Ayrıntılı dokümantasyon için Aspose.Words'e göz atın[Burada](https://reference.aspose.com/words/net/) ve Aspose.E-posta[Burada](https://reference.aspose.com/email/net/).