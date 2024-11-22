---
title: .NET में Aspose.CAD के साथ DGN फ़ाइल हेरफेर में महारत हासिल करें
linktitle: DGN फ़ाइल हेरफेर में निपुणता
second_title: Aspose.CAD .NET - CAD और BIM फ़ाइल प्रारूप
description: जानें कि DGN फ़ाइलों को कैसे लोड किया जाए, उनके तत्वों के माध्यम से पुनरावृति कैसे की जाए, 2D और 3D दोनों संस्थाओं को कैसे प्रबंधित किया जाए, और उन्हें रेखापुंज छवियों के रूप में कैसे निर्यात किया जाए - यह सब Aspose.CAD लाइब्रेरी की शक्तिशाली सुविधाओं का लाभ उठाते हुए।
type: docs
weight: 18
url: /hi/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## परिचय

क्या आप .NET डेवलपर हैं जो अपने अनुप्रयोगों में DGN फ़ाइलों को एकीकृत करने के लिए उत्सुक हैं? Aspose.CAD for .NET एक शक्तिशाली लाइब्रेरी प्रदान करता है जिसे विशेष रूप से DGN फ़ाइल स्वरूपों के साथ काम करने के लिए डिज़ाइन किया गया है। इस ट्यूटोरियल में, हम यह पता लगाएंगे कि समर्थित तत्वों सहित DGN फ़ाइलों को कुशलतापूर्वक कैसे संभालना है और उन्हें अपने .NET प्रोजेक्ट्स में कैसे हेरफेर करना है।

## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित सेटअप है:

- .NET प्रोग्रामिंग का बुनियादी ज्ञान: C# या VB.NET से परिचित होना लाभदायक होगा।
- विजुअल स्टूडियो: परियोजना विकास के लिए आपकी मशीन पर स्थापित।
-  .NET लाइब्रेरी के लिए Aspose.CAD: इसे यहाँ से डाउनलोड करें[Aspose.CAD](https://releases.aspose.com/cad/net/).

## चरण 1: आवश्यक नामस्थान आयात करें

Aspose.CAD की कार्यक्षमताओं का लाभ उठाने के लिए, अपने प्रोजेक्ट में आवश्यक नामस्थानों को आयात करके प्रारंभ करें।

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## चरण 2: अपनी DGN फ़ाइल लोड करें

 अपने एप्लीकेशन में एक मौजूदा DGN फ़ाइल लोड करके शुरू करें। यह एक इंस्टेंटिएट करके किया जाता है`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // यहां अपने तर्क के साथ आगे बढ़ें
}
```

## चरण 3: DGN तत्वों के माध्यम से पुनरावृति करें

एक बार DGN फ़ाइल लोड हो जाने के बाद, आप इसके तत्वों के माध्यम से पुनरावृति कर सकते हैं। Aspose.CAD आपके हेरफेर के लिए विभिन्न प्रकार के DGN तत्व प्रदान करता है।

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // प्रत्येक तत्व को संसाधित करें
}
```

## चरण 4: 2D और 3D संस्थाओं को संभालें

आप 2D और 3D DGN तत्वों के बीच अंतर कर सकते हैं। नीचे बताया गया है कि उन्हें कुशलतापूर्वक कैसे संभालना है:

### 2D संस्थाओं को संभालें

आप स्विच-केस ब्लॉक के साथ पहले से समर्थित 2D इकाइयों का प्रबंधन कर सकते हैं।

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // अपना प्रसंस्करण तर्क यहां जोड़ें
        break;
}
```

### 3D निकाय संभालें

इसी प्रकार, 3D निकायों को निम्नानुसार संभालें:

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // अपना प्रसंस्करण तर्क यहां जोड़ें
        break;
}
```

## चरण 5: DGN फ़ाइल निर्यात करें

DGN तत्वों में हेरफेर करने के बाद, आप फ़ाइल को रास्टर छवि के रूप में निर्यात करना चाह सकते हैं। यह Aspose.CAD के साथ आसानी से पूरा किया जा सकता है।

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // अपना आउटपुट पथ परिभाषित करें
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## निष्कर्ष

इस ट्यूटोरियल में, हमने सीखा कि DGN फ़ाइलों को प्रभावी ढंग से प्रबंधित करने के लिए .NET के लिए Aspose.CAD का उपयोग कैसे करें। उल्लिखित चरणों का पालन करके, आप आसानी से 2D और 3D DGN तत्वों को संभाल सकते हैं और उन्हें रास्टर छवियों के रूप में निर्यात कर सकते हैं। यह शक्तिशाली लाइब्रेरी आपके .NET अनुप्रयोगों में DGN प्रसंस्करण के सहज एकीकरण को सक्षम करती है, जिससे आपकी परियोजना क्षमताएँ बढ़ती हैं।

## अक्सर पूछे जाने वाले प्रश्न

### मैं .NET के लिए Aspose.CAD का दस्तावेज़ कहां पा सकता हूं?

 विस्तृत दस्तावेज उपलब्ध है[यहाँ](https://reference.aspose.com/cad/net/).

### मैं .NET के लिए Aspose.CAD कैसे डाउनलोड करूं?

 आप लाइब्रेरी का नवीनतम संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.aspose.com/cad/net/).

### क्या .NET के लिए Aspose.CAD का निःशुल्क परीक्षण उपलब्ध है?

 हां, निःशुल्क परीक्षण उपलब्ध है[यहाँ](https://releases.aspose.com/).

### मैं .NET के लिए Aspose.CAD हेतु अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?

 आप अस्थायी लाइसेंस का अनुरोध कर सकते हैं[यहाँ](https://purchase.conholdate.com/temporary-license/).

### क्या मदद की ज़रूरत है या कोई सवाल है?

 सहायता या प्रश्न पूछने के लिए, Aspose.CAD समुदाय पर जाएँ[सहयता मंच](https://forum.aspose.com/c/cad/19).