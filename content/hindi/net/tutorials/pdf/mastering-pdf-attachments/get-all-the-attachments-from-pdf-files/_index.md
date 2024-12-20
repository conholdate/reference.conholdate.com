---
title: पीडीएफ फाइलों से सभी अनुलग्नक प्राप्त करें
linktitle: पीडीएफ फाइलों से सभी अनुलग्नक प्राप्त करें
second_title: .NET API संदर्भ के लिए Aspose.PDF
description: इस चरण-दर-चरण मार्गदर्शिका में जानें कि .NET के लिए Aspose.PDF का उपयोग करके PDF फ़ाइलों से एम्बेडेड अनुलग्नकों को आसानी से कैसे निकाला जाए।
type: docs
weight: 40
url: /hi/net/tutorials/pdf/mastering-pdf-attachments/get-all-the-attachments-from-pdf-files/
---
## परिचय

हमारी डिजिटल दुनिया में, PDF फ़ाइलें दस्तावेज़ों को साझा करने के लिए आवश्यक हैं - वे बहुमुखी, सुरक्षित हैं, और उनमें एम्बेडेड अटैचमेंट सहित विभिन्न प्रकार की जानकारी हो सकती है। क्या आपको कभी PDF से उन छिपे हुए रत्नों को निकालने की ज़रूरत पड़ी है? आप सही जगह पर हैं! इस ट्यूटोरियल में, हम यह पता लगाएंगे कि PDF फ़ाइल से सभी अटैचमेंट निकालने के लिए .NET के लिए Aspose.PDF का उपयोग कैसे करें। चाहे आप एक अनुभवी डेवलपर हों या अभी शुरुआत कर रहे हों, यह गाइड आपको चरण दर चरण प्रक्रिया के माध्यम से ले जाएगा।

## आवश्यक शर्तें

इससे पहले कि हम कोड में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1. विजुअल स्टूडियो: सुनिश्चित करें कि यह आपके कंप्यूटर पर स्थापित है।
2.  .NET के लिए Aspose.PDF: लाइब्रेरी को डाउनलोड करें और इंस्टॉल करें[यहाँ](https://releases.aspose.com/pdf/net/).
3. C# का बुनियादी ज्ञान: C# प्रोग्रामिंग से परिचित होने से आपको कोड स्निपेट को अधिक आसानी से समझने में मदद मिलेगी।

## अपना वातावरण स्थापित करना

आरंभ करने के लिए, अपना C# प्रोजेक्ट सेट अप करने हेतु इन चरणों का पालन करें:

### एक नया प्रोजेक्ट बनाएं

विज़ुअल स्टूडियो खोलें, और एक नया कंसोल अनुप्रयोग प्रोजेक्ट बनाएं।

### Aspose.PDF संदर्भ जोड़ें

- समाधान एक्सप्लोरर में अपने प्रोजेक्ट पर राइट-क्लिक करें।
- “NuGet पैकेज प्रबंधित करें” चुनें।
- “Aspose.PDF” खोजें और नवीनतम संस्करण स्थापित करें।

## आवश्यक नामस्थान आयात करें

अपनी प्रोग्राम फ़ाइल के शीर्ष पर, आवश्यक नामस्थान आयात करें:

```csharp
using System.IO;
using Aspose.Pdf;
using System;
```

अब जब सब कुछ सेट हो गया है, तो आइए पीडीएफ से अनुलग्नकों को निकालने का काम शुरू करें।

## चरण 1: अपनी दस्तावेज़ निर्देशिका निर्दिष्ट करें

वह डायरेक्टरी निर्धारित करें जहाँ आपकी PDF फ़ाइल संग्रहीत है। यह प्रोग्राम को बताता है कि आपकी PDF को कहाँ रखना है।

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 प्रतिस्थापित करना सुनिश्चित करें`YOUR DOCUMENT DIRECTORY` वास्तविक पथ के साथ.

## चरण 2: पीडीएफ दस्तावेज़ खोलें

अपना PDF दस्तावेज़ खोलने के लिए Aspose.PDF लाइब्रेरी का उपयोग करें:

```csharp
Document pdfDocument = new Document(dataDir + "GetAlltheAttachments.pdf");
```

सुनिश्चित करें कि फ़ाइल पथ और नाम सही हैं.

## चरण 3: एम्बेडेड फ़ाइल संग्रह तक पहुँचें

पीडीएफ में संलग्नक तक पहुंचने के लिए, एम्बेडेड फ़ाइल संग्रह को पुनः प्राप्त करें:

```csharp
EmbeddedFileCollection embeddedFiles = pdfDocument.EmbeddedFiles;
```

## चरण 4: एम्बेडेड फ़ाइलों की गणना करें

यह जानना उपयोगी है कि कितने अनुलग्नक मौजूद हैं:

```csharp
Console.WriteLine("Total files : {0}", embeddedFiles.Count);
```

## चरण 5: अनुलग्नकों के माध्यम से लूप करें

लूप का उपयोग करके प्रत्येक अनुलग्नक का विवरण निकालें:

```csharp
int count = 1;

foreach (FileSpecification fileSpecification in embeddedFiles)
{
    Console.WriteLine("Name: {0}", fileSpecification.Name);
    Console.WriteLine("Description: {0}", fileSpecification.Description);
    Console.WriteLine("Mime Type: {0}", fileSpecification.MIMEType);
```

## चरण 6: अतिरिक्त फ़ाइल पैरामीटर निकालें

अतिरिक्त पैरामीटर वाले अनुलग्नकों के लिए, आप इन विवरणों की जांच और प्रिंट कर सकते हैं:

```csharp
if (fileSpecification.Params != null)
{
    Console.WriteLine("CheckSum: {0}", fileSpecification.Params.CheckSum);
    Console.WriteLine("Creation Date: {0}", fileSpecification.Params.CreationDate);
    Console.WriteLine("Modification Date: {0}", fileSpecification.Params.ModDate);
    Console.WriteLine("Size: {0}", fileSpecification.Params.Size);
}
```

## चरण 7: अनुलग्नकों को निकालें और सहेजें

अंत में, आइए प्रत्येक निकाले गए अनुलग्नक को एक फ़ाइल में सहेजें:

```csharp
byte[] fileContent = new byte[fileSpecification.Contents.Length];
fileSpecification.Contents.Read(fileContent, 0, fileContent.Length);

using (FileStream fileStream = new FileStream(dataDir + count + "_out" + ".txt", FileMode.Create))
{
    fileStream.Write(fileContent, 0, fileContent.Length);
}
count += 1;
```

यह कोड प्रत्येक अनुलग्नक की सामग्री को बाइट सरणी में पढ़ता है और उन्हें क्रमिक रूप से नाम देते हुए एक नई टेक्स्ट फ़ाइल में सहेजता है (उदाहरण के लिए,`1_out.txt`, `2_out.txt`, वगैरह।)।

## निष्कर्ष

बधाई हो! आपने अभी-अभी .NET के लिए Aspose.PDF का उपयोग करके PDF फ़ाइल से सभी अनुलग्नक निकाले हैं। यह शक्तिशाली लाइब्रेरी PDF दस्तावेज़ हेरफेर को सरल बनाती है और एम्बेडेड फ़ाइलों तक पहुँच को आसान बनाती है - व्यक्तिगत परियोजनाओं और व्यावसायिक प्रयासों दोनों के लिए एक अमूल्य कौशल।

## अक्सर पूछे जाने वाले प्रश्न

### .NET के लिए Aspose.PDF क्या है?
.NET के लिए Aspose.PDF एक लाइब्रेरी है जिसे डेवलपर्स के लिए प्रोग्रामेटिक रूप से PDF दस्तावेज़ बनाने, हेरफेर करने और परिवर्तित करने के लिए डिज़ाइन किया गया है।

### क्या Aspose.PDF का निःशुल्क परीक्षण उपलब्ध है?
 हां, Aspose एक निःशुल्क परीक्षण संस्करण प्रदान करता है जिसका उपयोग आप इसकी विशेषताओं का पता लगाने के लिए कर सकते हैं। इसे एक्सेस करें[यहाँ](https://releases.aspose.com/).

### मैं Aspose.PDF के लिए समर्थन कैसे प्राप्त कर सकता हूं?
 सहायता Aspose फ़ोरम के माध्यम से उपलब्ध है, जिसे आप पा सकते हैं[यहाँ](https://forum.aspose.com/c/pdf/10).

### क्या मैं अस्थायी लाइसेंस प्राप्त कर सकता हूँ?
 हां, आप Aspose.PDF के लिए अस्थायी लाइसेंस का अनुरोध कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).

### मैं Aspose.PDF के लिए दस्तावेज़ कहां पा सकता हूं?
 आप .NET के लिए Aspose.PDF का विस्तृत दस्तावेज़ पा सकते हैं[यहाँ](https://reference.aspose.com/pdf/net/).