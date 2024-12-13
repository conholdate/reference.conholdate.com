---
title: XLS और XLSX प्रारूपों में अधिकतम पंक्तियाँ और कॉलम खोजें
linktitle: XLS और XLSX प्रारूपों में अधिकतम पंक्तियाँ और कॉलम खोजें
second_title: Aspose.Cells .NET एक्सेल प्रोसेसिंग API
description: जानें कि .NET लाइब्रेरी के लिए Aspose.Cells का उपयोग करके Excel में बड़े डेटासेट को कुशलतापूर्वक कैसे प्रबंधित किया जाए। यह मार्गदर्शिका XLS और XLSX फ़ाइल स्वरूपों द्वारा समर्थित पंक्तियों और स्तंभों की अधिकतम संख्या की पहचान करने के लिए चरण-दर-चरण दृष्टिकोण प्रदान करती है।
type: docs
weight: 11
url: /hi/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## परिचय

Excel में बड़े डेटासेट को प्रबंधित करना चुनौतीपूर्ण हो सकता है, खासकर विभिन्न फ़ाइल स्वरूपों की सीमाओं के संबंध में। यह ट्यूटोरियल आपको XLS (Excel 97-2003) और XLSX (Excel 2007 और बाद के) प्रारूपों द्वारा समर्थित पंक्तियों और स्तंभों की अधिकतम संख्या निर्धारित करने के लिए Aspose.Cells for .NET लाइब्रेरी का उपयोग करने के माध्यम से मार्गदर्शन करेगा। अंत तक, आप Excel से संबंधित कार्यों को कुशलतापूर्वक संभालने के लिए सुसज्जित हो जाएँगे।

## आवश्यक शर्तें

शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:

1. [.NET फ्रेमवर्क](https://dotnet.microsoft.com/en-us/download) या[.NET कोर](https://dotnet.microsoft.com/en-us/download) आपके सिस्टम पर स्थापित है.
2. [.NET के लिए Aspose.Cells](https://releases.aspose.com/cells/net/) आपके प्रोजेक्ट में डाउनलोड और संदर्भित लाइब्रेरी (आप इसे इसके माध्यम से भी इंस्टॉल कर सकते हैं)[नुगेट](https://www.nuget.org/packages/Aspose.Cells/)).

## आवश्यक पैकेज आयात करना

Aspose.Cells लाइब्रेरी से आवश्यक पैकेज आयात करने के लिए अपनी C# फ़ाइल के शीर्ष पर निम्नलिखित using कथन जोड़ें:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## चरण 1: XLS प्रारूप के लिए अधिकतम पंक्तियाँ और कॉलम

आइए XLS प्रारूप द्वारा समर्थित अधिकतम पंक्तियों और स्तंभों का पता लगाने से शुरुआत करें।

```csharp
// XLS प्रारूप के बारे में संदेश मुद्रित करें.
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// XLS प्रारूप में एक कार्यपुस्तिका बनाएँ.
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

// अधिकतम पंक्तियाँ और कॉलम पुनः प्राप्त करें.
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

// परिणाम प्रदर्शित करें.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. यह बताने के लिए एक संदेश प्रिंट करें कि हम XLS प्रारूप के साथ काम कर रहे हैं।
2.  एक बनाने के`Workbook` XLS प्रारूप का उपयोग करने के लिए उदाहरण`FileFormatType.Excel97To2003`.
3.  अधिकतम पंक्तियाँ और कॉलम प्राप्त करें`wb.Settings.MaxRow` और`wb.Settings.MaxColumn`, 1 जोड़ें क्योंकि ये शून्य-आधारित हैं।
4. कंसोल पर अधिकतम पंक्तियाँ और कॉलम आउटपुट करें.

## चरण 2: XLSX प्रारूप के लिए अधिकतम पंक्तियाँ और कॉलम

आगे, हम XLSX प्रारूप द्वारा समर्थित अधिकतम पंक्तियों और स्तंभों का पता लगाएंगे।

```csharp
// XLSX प्रारूप के बारे में संदेश मुद्रित करें।
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// XLSX प्रारूप में एक कार्यपुस्तिका बनाएँ.
wb = new Workbook(FileFormatType.Xlsx);

// अधिकतम पंक्तियाँ और कॉलम पुनः प्राप्त करें.
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

// परिणाम प्रदर्शित करें.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. एक संदेश प्रिंट करें जो यह बताए कि हम XLSX प्रारूप के साथ काम कर रहे हैं।
2.  एक बनाने के`Workbook` XLSX प्रारूप का उपयोग करने के लिए उदाहरण`FileFormatType.Xlsx`.
3. पहले की तरह अधिकतम पंक्तियों और स्तंभों को पुनः प्राप्त करें और आउटपुट करें।

## चरण 3: सफलता संदेश प्रदर्शित करना

चरणों को निष्पादित करने के बाद, सफलता का संकेत दें।

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## निष्कर्ष

इस ट्यूटोरियल में, आपने सीखा कि XLS और XLSX फ़ाइल फ़ॉर्मेट द्वारा समर्थित अधिकतम पंक्तियों और स्तंभों को खोजने के लिए Aspose.Cells for .NET लाइब्रेरी का उपयोग कैसे करें। प्रभावी Excel डेटा प्रबंधन के लिए इन सीमाओं को समझना आवश्यक है, यह सुनिश्चित करना कि आपके डेटासेट फ़ॉर्मेट क्षमताओं के साथ संरेखित हों।

## अक्सर पूछे जाने वाले प्रश्न

### XLS प्रारूप द्वारा समर्थित पंक्तियों की अधिकतम संख्या कितनी है?
XLS प्रारूप द्वारा समर्थित पंक्तियों की अधिकतम संख्या 65,536 है।

### XLS प्रारूप द्वारा समर्थित स्तंभों की अधिकतम संख्या क्या है?
XLS प्रारूप द्वारा समर्थित स्तंभों की अधिकतम संख्या 256 है।

### XLSX प्रारूप द्वारा समर्थित पंक्तियों की अधिकतम संख्या कितनी है?
XLSX प्रारूप द्वारा समर्थित पंक्तियों की अधिकतम संख्या 1,048,576 है।

### XLSX प्रारूप द्वारा समर्थित स्तंभों की अधिकतम संख्या क्या है?
XLSX प्रारूप द्वारा समर्थित स्तंभों की अधिकतम संख्या 16,384 है।

### क्या मैं अन्य Excel फ़ाइल स्वरूपों के साथ Aspose.Cells for .NET लाइब्रेरी का उपयोग कर सकता हूँ?
 हां, Aspose.Cells for .NET विभिन्न फ़ाइल स्वरूपों का समर्थन करता है, जिसमें XLS, XLSX, ODS, और बहुत कुछ शामिल है।[प्रलेखन](https://reference.aspose.com/cells/net/) समर्थित सुविधाओं और कार्यात्मकताओं के विवरण के लिए.