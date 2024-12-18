---
title: हस्ताक्षरित एक्सेल फ़ाइल में नया डिजिटल हस्ताक्षर जोड़ना
linktitle: हस्ताक्षरित एक्सेल फ़ाइल में नया डिजिटल हस्ताक्षर जोड़ना
second_title: Aspose.Cells .NET एक्सेल प्रोसेसिंग API
description: जानें कि Aspose.Cells for .NET का उपयोग करके किसी मौजूदा हस्ताक्षरित Excel फ़ाइल में नया डिजिटल हस्ताक्षर कैसे जोड़ें। यह व्यापक गाइड सभी पूर्वापेक्षाएँ, चरण-दर-चरण निर्देश और कोड उदाहरण को कवर करती है।
type: docs
weight: 12
url: /hi/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## परिचय

आज के डिजिटल परिदृश्य में, दस्तावेजों की प्रामाणिकता और अखंडता सुनिश्चित करना पहले से कहीं अधिक महत्वपूर्ण है। डिजिटल हस्ताक्षर यह सत्यापित करने का एक विश्वसनीय तरीका प्रदान करते हैं कि किसी दस्तावेज़ में कोई बदलाव नहीं किया गया है और यह किसी वैध स्रोत से आया है। यदि आप .NET में Excel फ़ाइलों के साथ काम कर रहे हैं और पहले से हस्ताक्षरित किसी फ़ाइल में नया डिजिटल हस्ताक्षर जोड़ने की आवश्यकता है, तो यह मार्गदर्शिका आपके लिए है! हम .NET के लिए Aspose.Cells का उपयोग करके मौजूदा हस्ताक्षरित Excel फ़ाइल में डिजिटल हस्ताक्षर जोड़ने की प्रक्रिया से गुजरेंगे।

## आवश्यक शर्तें

इससे पहले कि हम कार्यान्वयन में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1.  .NET के लिए Aspose.Cells: Aspose.Cells को डाउनलोड करें और इंस्टॉल करें[रिलीज़ पेज](https://releases.aspose.com/cells/net/).
2. .NET फ्रेमवर्क: सुनिश्चित करें कि आपकी मशीन में .NET फ्रेमवर्क सेटअप है और आप बुनियादी .NET प्रोग्रामिंग अवधारणाओं से परिचित हैं।
3. डिजिटल प्रमाणपत्र: .pfx प्रारूप में एक वैध डिजिटल प्रमाणपत्र प्राप्त करें। परीक्षण के लिए, आप एक स्व-हस्ताक्षरित प्रमाणपत्र बना सकते हैं।
4. विकास वातावरण: अपने C# कोड को लिखने और निष्पादित करने के लिए Visual Studio जैसे IDE का उपयोग करें।
5. नमूना एक्सेल फ़ाइल: एक मौजूदा एक्सेल फ़ाइल रखें जो पहले से ही डिजिटल रूप से हस्ताक्षरित हो, जो एक नया हस्ताक्षर जोड़ने का लक्ष्य होगा।

इन पूर्व-आवश्यकताओं के साथ, आइए कोड में प्रवेश करें!

## आवश्यक पैकेज आयात करें

अपनी C# फ़ाइल के शीर्ष पर, आवश्यक क्लासों और विधियों तक पहुँचने के लिए निम्नलिखित नामस्थान शामिल करें:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## चरण 1: अपनी निर्देशिकाएँ परिभाषित करें

अपनी स्रोत फ़ाइलों के लिए निर्देशिकाएँ और आउटपुट फ़ाइल को कहाँ सहेजना है, निर्दिष्ट करें:

```csharp
// स्रोत निर्देशिका
string sourceDir = "Your Document Directory"; // अपनी वास्तविक निर्देशिका से प्रतिस्थापित करें
// आउटपुट निर्देशिका
string outputDir = "Your Document Directory"; // अपनी वास्तविक निर्देशिका से प्रतिस्थापित करें
```

## चरण 2: मौजूदा हस्ताक्षरित कार्यपुस्तिका लोड करें

पहले से हस्ताक्षरित Excel कार्यपुस्तिका लोड करें:

```csharp
// वह कार्यपुस्तिका लोड करें जो पहले से ही डिजिटल रूप से हस्ताक्षरित है
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## चरण 3: डिजिटल हस्ताक्षर संग्रह बनाएं

अपने डिजिटल हस्ताक्षरों को प्रबंधित करने के लिए एक संग्रह बनाएं:

```csharp
//डिजिटल हस्ताक्षर संग्रह बनाएं
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## चरण 4: अपना प्रमाणपत्र लोड करें

अपना डिजिटल प्रमाणपत्र लोड करें, जिसका उपयोग नया हस्ताक्षर बनाने के लिए किया जाएगा:

```csharp
// प्रमाणपत्र फ़ाइल और उसका पासवर्ड
string certFileName = sourceDir + "AsposeDemo.pfx"; // आपकी प्रमाणपत्र फ़ाइल
string password = "aspose"; // आपका प्रमाणपत्र पासवर्ड

// नया प्रमाणपत्र बनाएं
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## चरण 5: नया डिजिटल हस्ताक्षर बनाएं

अब, एक नया डिजिटल हस्ताक्षर बनाएं और उसे अपने संग्रह में जोड़ें:

```csharp
// नया डिजिटल हस्ताक्षर बनाएं और उसे संग्रह में जोड़ें
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## चरण 6: कार्यपुस्तिका में हस्ताक्षर संग्रह जोड़ें

कार्यपुस्तिका में डिजिटल हस्ताक्षर संग्रह जोड़ें:

```csharp
// कार्यपुस्तिका में डिजिटल हस्ताक्षर संग्रह जोड़ें
workbook.AddDigitalSignature(dsCollection);
```

## चरण 7: कार्यपुस्तिका सहेजें

नए डिजिटल हस्ताक्षर के साथ कार्यपुस्तिका को सहेजें:

```csharp
// कार्यपुस्तिका सहेजें
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## चरण 8: सफलता की पुष्टि करें

सफल निष्पादन पर प्रतिक्रिया दें:

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## निष्कर्ष

बधाई हो! आपने .NET के लिए Aspose.Cells का उपयोग करके पहले से हस्ताक्षरित Excel फ़ाइल में सफलतापूर्वक एक नया डिजिटल हस्ताक्षर जोड़ लिया है। यह प्रक्रिया आपके दस्तावेज़ों की सुरक्षा को बढ़ाती है और उनकी प्रामाणिकता और अखंडता सुनिश्चित करती है।

## अक्सर पूछे जाने वाले प्रश्न

### डिजिटल हस्ताक्षर क्या है?

डिजिटल हस्ताक्षर एक गणितीय योजना है जो डिजिटल संदेशों या दस्तावेजों की प्रामाणिकता और अखंडता को सत्यापित करती है, यह सुनिश्चित करती है कि उनमें कोई परिवर्तन नहीं किया गया है और हस्ताक्षरकर्ता की पहचान की पुष्टि करती है।

### क्या मुझे डिजिटल हस्ताक्षर बनाने के लिए किसी विशेष प्रमाणपत्र की आवश्यकता है?

हां, वैध डिजिटल हस्ताक्षर बनाने के लिए विश्वसनीय प्रमाणपत्र प्राधिकारी (सीए) द्वारा जारी डिजिटल प्रमाणपत्र की आवश्यकता होती है।

### क्या मैं परीक्षण के लिए स्व-हस्ताक्षरित प्रमाणपत्र का उपयोग कर सकता हूँ?

बिल्कुल! आप विकास और परीक्षण उद्देश्यों के लिए स्व-हस्ताक्षरित प्रमाणपत्र का उपयोग कर सकते हैं, लेकिन उत्पादन के लिए, किसी विश्वसनीय CA से प्रमाणपत्र का उपयोग करना उचित है।

### यदि मैं किसी गैर-हस्ताक्षरित दस्तावेज़ में हस्ताक्षर जोड़ने का प्रयास करूं तो क्या होगा?

यदि आप किसी ऐसे दस्तावेज़ में डिजिटल हस्ताक्षर जोड़ने का प्रयास करते हैं, जिस पर पहले से हस्ताक्षर नहीं है, तो यह बिना किसी समस्या के काम करेगा, लेकिन मूल हस्ताक्षर मौजूद नहीं होगा।

### मैं Aspose.Cells के बारे में अधिक जानकारी कहां पा सकता हूं?

 विस्तृत गाइड और API संदर्भों के लिए, देखें[Aspose.Cells दस्तावेज़ीकरण](https://reference.aspose.com/cells/net/).