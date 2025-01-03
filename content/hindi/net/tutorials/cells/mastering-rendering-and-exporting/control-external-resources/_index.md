---
title: .NET के लिए Aspose.Cells के साथ बाह्य संसाधनों को नियंत्रित करें
linktitle: .NET के लिए Aspose.Cells के साथ बाह्य संसाधनों को नियंत्रित करें
second_title: Aspose.Cells .NET एक्सेल प्रोसेसिंग API
description: .NET के लिए Aspose.Cells के साथ अपने Excel से PDF रूपांतरण की पूरी क्षमता को अनलॉक करें। इस व्यापक गाइड में, छवियों जैसे बाहरी संसाधनों को प्रबंधित करना सीखें, यह सुनिश्चित करते हुए कि आपके PDF आपकी सटीक स्वरूपण आवश्यकताओं को दर्शाते हैं।
type: docs
weight: 12
url: /hi/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## परिचय

आज के डिजिटल परिदृश्य में, एक्सेल स्प्रेडशीट को पीडीएफ दस्तावेजों में बदलना एक आम और आवश्यक कार्य है। चाहे आप रिपोर्ट, वित्तीय डेटा या प्रस्तुति सामग्री तैयार कर रहे हों, यह सुनिश्चित करना महत्वपूर्ण है कि आपके पीडीएफ आपके इच्छित प्रारूप को दर्शाते हैं। .NET के लिए Aspose.Cells एक शक्तिशाली लाइब्रेरी प्रदान करता है जो आपको इस रूपांतरण प्रक्रिया को विस्तार से नियंत्रित करने की अनुमति देता है, खासकर जब छवियों जैसे बाहरी संसाधनों से निपटते हैं। इस गाइड में, हम यह पता लगाएंगे कि Aspose.Cells का उपयोग करके एक्सेल से पीडीएफ रूपांतरण प्रक्रिया के दौरान बाहरी संसाधनों को प्रभावी ढंग से कैसे प्रबंधित किया जाए। आइए गोता लगाएँ!

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित चीज़ें तैयार हैं:

1. विजुअल स्टूडियो या कोई भी .NET-संगत IDE: यह आपका विकास वातावरण होगा।
2.  .NET के लिए Aspose.Cells: यदि आपने इसे अभी तक स्थापित नहीं किया है, तो यहां जाएं[Aspose डाउनलोड](https://releases.aspose.com/cells/net/) नवीनतम संस्करण प्राप्त करने के लिए कृपया इस पेज पर जाएँ।
3. C# का बुनियादी ज्ञान: C# से परिचित होना लाभदायक होगा। यदि आपको किसी अवधारणा पर स्पष्टीकरण की आवश्यकता है, तो बेझिझक उन्हें देखें।
4. नमूना एक्सेल फ़ाइल: एक एक्सेल फ़ाइल तैयार करें, जैसे कि "samplePdfSaveOptions_StreamProvider.xlsx", जिसमें वे बाह्य संसाधन हों जिन्हें आप परिवर्तित करना चाहते हैं।
5. परीक्षण के लिए छवि फ़ाइल: रूपांतरण के दौरान बाह्य संसाधन के रूप में "newPdfSaveOptions_StreamProvider.png" जैसी छवि फ़ाइल का उपयोग करें।

## आवश्यक पैकेज आयात करें

आरंभ करने के लिए, आपको Aspose.Cells लाइब्रेरी से आवश्यक नामस्थान आयात करने होंगे। अपनी C# फ़ाइल के शीर्ष पर निम्नलिखित using निर्देश जोड़ें:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

ये नामस्थान आपके कार्यों के लिए आवश्यक कक्षाएं और विधियां प्रदान करते हैं।

## चरण 1: स्ट्रीम प्रदाता क्लास बनाएँ

 सबसे पहले, एक स्ट्रीम प्रदाता वर्ग बनाएं जो कार्यान्वित करता है`IStreamProvider` इंटरफ़ेस। यह क्लास आपको यह नियंत्रित करने में सक्षम करेगा कि बाहरी संसाधन कैसे लोड किए जाएं।

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // छवि को मेमोरी स्ट्रीम में लोड करें
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: यह विधि तब कॉल की जाती है जब स्ट्रीम बंद हो जाती है, वर्तमान में एक डीबग संदेश लॉग कर रही होती है।
- InitStream: यह विधि बाह्य छवि फ़ाइल को बाइट सरणी के रूप में पढ़ती है, इसे मेमोरी स्ट्रीम में परिवर्तित करती है, और इसे असाइन करती है`options.Stream` संपत्ति।

## चरण 2: स्रोत और आउटपुट निर्देशिकाएँ सेट करें

इसके बाद, अपनी एक्सेल फ़ाइल और आउटपुट पीडीएफ के लिए निर्देशिकाएँ परिभाषित करें।

```csharp
// स्रोत निर्देशिका
string sourceDir = "Your Document Directory";
// आउटपुट निर्देशिका
string outputDir = "Your Document Directory";
```

 प्रतिस्थापित करें`"Your Document Directory"` आपके सिस्टम पर उस वास्तविक पथ के साथ जहां आपकी फ़ाइलें स्थित हैं।

## चरण 3: अपनी एक्सेल फ़ाइल लोड करें

अब, वह एक्सेल फ़ाइल लोड करें जिससे आप पीडीएफ बनाना चाहते हैं।

```csharp
// बाह्य छवियों वाली स्रोत Excel फ़ाइल लोड करें
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

`Workbook` Aspose.Cells से क्लास आपकी एक्सेल फ़ाइल का प्रतिनिधित्व करता है, जिसमें छवियों जैसे विभिन्न बाहरी संसाधन शामिल हो सकते हैं।

## चरण 4: पीडीएफ सेव विकल्प सेट करें

कार्यपुस्तिका को PDF के रूप में सहेजने से पहले, अपने इच्छित सहेजने के विकल्प निर्दिष्ट करें।

```csharp
// पीडीएफ सेव विकल्प निर्दिष्ट करें - स्ट्रीम प्रदाता
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // प्रत्येक शीट को नए पृष्ठ पर सहेजें
};
```

 इससे एक उदाहरण बनता है`PdfSaveOptions` , जिससे आप पीडीएफ प्रारूप को अनुकूलित कर सकते हैं।`OnePagePerSheet` विकल्प यह सुनिश्चित करता है कि प्रत्येक एक्सेल शीट अंतिम पीडीएफ में एक अलग पृष्ठ पर दिखाई दे।

## चरण 5: अपना स्ट्रीम प्रदाता निर्दिष्ट करें

 अपने`Workbook` उदाहरण के साथ`MyStreamProvider` वह क्लास जिसे आपने पहले बनाया था.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

यह पंक्ति सुनिश्चित करती है कि जब भी रूपांतरण के दौरान बाहरी संसाधनों का सामना होगा, तो आपका कस्टम प्रदाता उन्हें तदनुसार प्रबंधित करेगा।

## चरण 6: कार्यपुस्तिका को PDF के रूप में सहेजें

अब, अपनी एक्सेल वर्कबुक को पीडीएफ के रूप में सेव करें।

```csharp
// कार्यपुस्तिका को PDF में सहेजें
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 फोन करके`Save` वर्कबुक ऑब्जेक्ट पर मेथड का उपयोग करके और पीडीएफ विकल्पों के साथ आउटपुट डायरेक्टरी को पास करके, आप एक्सेल फ़ाइल को एक अच्छी तरह से प्रारूपित पीडीएफ में परिवर्तित कर सकते हैं।

## चरण 7: सफल निष्पादन की पुष्टि करें

अंत में, यह पुष्टि करना अच्छा रहेगा कि प्रक्रिया सफलतापूर्वक पूरी हो गई है।

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

यह संदेश आपको आपके ऑपरेशन की स्थिति के बारे में सूचित करेगा तथा उपयोगी फीडबैक प्रदान करेगा।

## निष्कर्ष

अब आप Aspose.Cells का उपयोग करके Excel से PDF रूपांतरण के दौरान बाहरी संसाधनों को नियंत्रित करने की प्रक्रिया में महारत हासिल कर चुके हैं! इन चरणों का पालन करके, आप यह सुनिश्चित कर सकते हैं कि आपके दस्तावेज़ों में छवियाँ और अन्य बाहरी तत्व सटीक रूप से शामिल हों, जिसके परिणामस्वरूप हर बार एक पॉलिश अंतिम उत्पाद प्राप्त होता है।

## अक्सर पूछे जाने वाले प्रश्न

### Aspose.Cells क्या है?
Aspose.Cells .NET डेवलपर्स के लिए एक शक्तिशाली लाइब्रेरी है जो विभिन्न प्रारूपों में एक्सेल फाइलों के निर्माण, हेरफेर, रूपांतरण और रेंडरिंग को सक्षम बनाती है।

### मैं Aspose.Cells कैसे डाउनलोड करूं?
 आप नवीनतम संस्करण को यहाँ से डाउनलोड कर सकते हैं[लिंक को डाउनलोड करें](https://releases.aspose.com/cells/net/).

### क्या मैं Aspose.Cells को निःशुल्क आज़मा सकता हूँ?
 हाँ! आप यहाँ जाकर निःशुल्क परीक्षण प्राप्त कर सकते हैं[निःशुल्क परीक्षण पृष्ठ](https://releases.aspose.com/).

### मैं Aspose.Cells के लिए समर्थन कहां पा सकता हूं?
 सहायता-संबंधी प्रश्नों के लिए, यहां जाएं[Aspose सहायता मंच](https://forum.aspose.com/c/cells/9).

### मैं Aspose.Cells के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 आप अस्थायी लाइसेंस के लिए आवेदन कर सकते हैं[यहाँ](https://purchase.aspose.com/temporary-license/).
