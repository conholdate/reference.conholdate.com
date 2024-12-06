---
title: Tüm CSS Kurallarını Tek Bir Dosyada Kaydet
linktitle: Tüm Css Kurallarını Tek Bir Dosyaya Yaz
second_title: Aspose.Words Belge İşleme API'si
description: HtmlFixedSaveOptions ile belgeleri kaydederken tüm CSS kurallarını tek bir dosyaya yazmak için Aspose.Words for .NET'i nasıl kullanacağınızı öğrenin. Adım adım rehberlik için bu ayrıntılı öğreticiyi izleyin.
type: docs
weight: 10
url: /tr/net/tutorials/words/html-fixed-save-options/save-all-css-rules-in-single-file/
---
## giriiş

Word belgelerini HTML'e dönüştürürken hiç dağınık bir CSS kuralları dizisiyle uğraştınız mı? Yalnız değilsiniz! Neyse ki, Aspose.Words for .NET tüm CSS kurallarınızı tek bir dosyada birleştirmenize olanak tanıyan güçlü bir özellik sunuyor. Bu yalnızca kodunuzu temizlemekle kalmıyor, aynı zamanda iş akışınızı da basitleştiriyor. Daha temiz, daha verimli HTML çıktısına doğru bir yolculuğa çıkalım!

## Ön koşullar

Kodlamaya başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Words for .NET: Kütüphaneyi şuradan edinin:[Burada](https://releases.aspose.com/words/net/).
2. .NET Geliştirme Ortamı: Visual Studio gibi bir kurulum geliştirme için idealdir.
3. Temel C# Bilgisi: C#'a aşinalık, kodda gezinmenize yardımcı olacaktır.
4. Word Belgesi: Dönüştürülmeye hazır bir .docx dosyanız olsun.

## Ad Alanlarını İçe Aktar

Öncelikle, C# projenize gerekli ad alanlarını içe aktaralım. Bu, Aspose.Words işlevlerine kolayca erişmemizi sağlayacaktır.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Sorunsuz bir dönüşüm sağlamak için bu süreci yönetilebilir adımlara bölelim.

## Adım 1: Belge Dizininizi Ayarlayın

Öncelikle Word belgenizin bulunduğu dizin yolunu ve dönüştürülen HTML'nin nereye kaydedileceğini belirleyin.

```csharp
// Belge dizininize giden yolu tanımlayın
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Adım 2: Word Belgesini Yükleyin

 Daha sonra, Word belgesini kullanarak yükleyin`Document` Aspose.Words kütüphanesinden sınıf.

```csharp
// Word belgesini yükleyin
Document doc = new Document(dataDir + "Document.docx");
```

## Adım 3: HTML Kaydetme Seçeneklerini Yapılandırın

 Şimdi HTML kaydetme seçeneklerini yapılandıralım. Tüm CSS kurallarını tek bir dosyada birleştiren özelliği etkinleştirmek istiyoruz.`SaveFontFaceCssSeparately` ile`false`.

```csharp
// Tüm CSS kurallarını tek bir dosyaya yazmak için HTML kaydetme seçeneklerini yapılandırın
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## Adım 4: Belgeyi HTML'ye Dönüştür

Son olarak, belgeyi belirtilen seçeneklerle bir HTML dosyası olarak kaydedin. Bu, tüm CSS kurallarının tek bir dosyada düzgün bir şekilde düzenlenmesini sağlar.

```csharp
// Belgeyi HTML'ye dönüştür
doc.Save(dataDir + "ConvertedDocument.html", saveOptions);
```

## Çözüm

Tebrikler! Sadece birkaç satır kodla Word belgenizi HTML'ye başarıyla dönüştürdünüz ve tüm CSS kurallarının tek bir dosyada derlenmesini sağladınız. Bu yaklaşım CSS yönetimini basitleştirir ve HTML belgelerinizin sürdürülebilirliğini artırır. Bir dahaki sefere bir Word belgesini dönüştürmeniz gerektiğinde, parmaklarınızın ucunda kolaylaştırılmış bir süreç olacak!

## SSS

### HTML çıktım için neden tek bir CSS dosyası kullanmalıyım?
Tek bir CSS dosyası stil yönetimini basitleştirir, HTML'nizi daha temiz ve bakımı daha kolay hale getirir.

### Gerekirse font yüzü CSS kurallarını ayırabilir miyim?
 Kesinlikle! Ayarlayarak`SaveFontFaceCssSeparately` ile`true`, font yüzü CSS kurallarını ayrı bir dosyaya ayırabilirsiniz.

### Aspose.Words for .NET'i kullanmak ücretsiz mi?
 Aspose.Words indirilebilir ücretsiz bir deneme sunuyor[Burada](https://releases.aspose.com/) . Sürekli kullanım için bir lisans satın almayı düşünün[Burada](https://purchase.aspose.com/buy).

### Aspose.Words for .NET başka hangi formatlara dönüştürülebilir?
Aspose.Words, PDF, TXT ve JPEG ve PNG gibi resim formatları da dahil olmak üzere çeşitli formatları destekler.

### Aspose.Words for .NET hakkında daha fazla kaynağı nerede bulabilirim?
 Kapsamlı kılavuzlar ve API referansları için şuraya göz atın:[belgeleme](https://reference.aspose.com/words/net/).
