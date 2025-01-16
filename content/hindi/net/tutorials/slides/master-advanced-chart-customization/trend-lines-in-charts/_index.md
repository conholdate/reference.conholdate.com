---
title: .NET के लिए Aspose.Slides के साथ चार्ट में ट्रेंड लाइन्स
linktitle: .NET के लिए Aspose.Slides के साथ चार्ट में ट्रेंड लाइन्स
second_title: Aspose.Slides .NET पावरपॉइंट प्रोसेसिंग API
description: Aspose.Slides for .NET का उपयोग करके चार्ट में ट्रेंड लाइन जोड़ने और उन्हें कस्टमाइज़ करने का तरीका जानें। यह व्यापक गाइड आपके डेटा विज़ुअलाइज़ेशन को बढ़ाने के लिए एक्सपोनेंशियल, लीनियर, लॉगरिदमिक, पॉलीनोमियल और मूविंग एवरेज ट्रेंड लाइनों को कवर करती है।
type: docs
weight: 12
url: /hi/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## परिचय  

चार्ट में ट्रेंड लाइन जोड़ना डेटा ट्रेंड का विश्लेषण करने और भविष्य के मूल्यों का पूर्वानुमान लगाने की एक महत्वपूर्ण तकनीक है। .NET के लिए Aspose.Slides के साथ, आप अपने प्रेजेंटेशन चार्ट में ट्रेंड लाइन को आसानी से जोड़ और कस्टमाइज़ कर सकते हैं, जिससे आपका डेटा विज़ुअलाइज़ेशन बेहतर हो जाता है। यह गाइड Aspose.Slides for .NET का उपयोग करके PowerPoint प्रेजेंटेशन में विभिन्न चार्ट प्रकारों में ट्रेंड लाइन जोड़ने के लिए विस्तृत जानकारी प्रदान करता है।  

## आवश्यक शर्तें  

इससे पहले कि हम कार्यान्वयन में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित सेटअप है:  

1.  Aspose.Slides for .NET: लाइब्रेरी को डाउनलोड करें और इंस्टॉल करें[डाउनलोड पृष्ठ](https://releases.aspose.com/slides/net/).  
2. विकास वातावरण: कोडिंग के लिए विजुअल स्टूडियो जैसे IDE का उपयोग करें।  
3. बुनियादी C# ज्ञान: इस ट्यूटोरियल का अनुसरण करने के लिए C# प्रोग्रामिंग से परिचित होना आवश्यक है।  

## आवश्यक नामस्थान आयात करना  

आरंभ करने के लिए, अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करें:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## चरण 1: प्रस्तुति सेट करना  

सबसे पहले, एक खाली प्रेजेंटेशन को इनिशियलाइज़ करें। यह आपके चार्ट के लिए कंटेनर के रूप में काम करेगा।  

```csharp
string dataDir = "Your/Documents/Directory";

// सुनिश्चित करें कि निर्देशिका मौजूद है
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// एक नया प्रस्तुतिकरण बनाएं
Presentation presentation = new Presentation();
```

## चरण 2: स्लाइड में चार्ट जोड़ना  

अब, एक स्लाइड जोड़ें और अपने डेटा को दृश्यमान करने के लिए एक क्लस्टर कॉलम चार्ट शामिल करें।  

```csharp
// रिक्त स्लाइड जोड़ें
ISlide slide = presentation.Slides[0];

// क्लस्टर कॉलम चार्ट जोड़ें
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## चरण 3: चार्ट डेटा भरना  

चार्ट को नमूना डेटा से भरें.  

```csharp
// डिफ़ॉल्ट चार्ट डेटा कार्यपुस्तिका तक पहुँचें
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// डिफ़ॉल्ट श्रेणियाँ और श्रृंखला मान अपडेट करें
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## चरण 4: ट्रेंड लाइन्स जोड़ना  

### घातांकीय प्रवृत्ति रेखा  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### रेखीय प्रवृत्ति रेखा  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### लघुगणकीय प्रवृत्ति रेखा  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### चलती औसत प्रवृत्ति रेखा  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### बहुपद प्रवृत्ति रेखा  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### पावर ट्रेंड लाइन  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## चरण 5: प्रस्तुति को सहेजना  

अंत में, अपने चार्ट में जोड़ी गई सभी प्रवृत्ति रेखाओं के साथ प्रस्तुति को सहेजें।  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## निष्कर्ष  

.NET के लिए Aspose.Slides का उपयोग करके, अपने चार्ट में ट्रेंड लाइन जोड़ना एक सीधा काम बन जाता है। यह सुविधा आपको डेटा ट्रेंड को प्रभावी ढंग से प्रस्तुत करने और अपनी प्रस्तुतियों में पेशेवर स्पर्श जोड़ने की अनुमति देती है। विभिन्न ट्रेंड लाइन प्रकारों को शामिल करने और अपने डेटा विज़ुअलाइज़ेशन को बढ़ाने के लिए ऊपर दिए गए चरणों का पालन करें।  

## अक्सर पूछे जाने वाले प्रश्न  

### क्या मैं ट्रेंड लाइनों के स्वरूप को अनुकूलित कर सकता हूँ?  
 हां, आप ट्रेंड लाइनों के रंग, मोटाई और शैली को अनुकूलित कर सकते हैं`Format.Line` संपत्ति।  

### क्या अन्य चार्ट प्रकारों के लिए समर्थन उपलब्ध है?  
हां, Aspose.Slides for .NET विभिन्न चार्ट प्रकारों का समर्थन करता है, जिसमें बार, पाई और लाइन चार्ट शामिल हैं।  

### मैं समीकरण और R-स्क्वायर्ड मान कैसे प्रदर्शित करूँ?  
 सक्षम`DisplayEquation` और`DisplayRSquaredValue` चार्ट पर इन मानों को प्रदर्शित करने के लिए प्रवृत्ति रेखा के गुण।  

### क्या मैं अन्य भाषाओं के साथ .NET के लिए Aspose.Slides का उपयोग कर सकता हूँ?  
हां, लाइब्रेरी VB.NET और F# सहित किसी भी .NET समर्थित भाषा के साथ संगत है।  

### मैं आगे का दस्तावेज़ कहां पा सकता हूं?  
 दौरा करना[.NET दस्तावेज़ीकरण के लिए Aspose.Slides](https://reference.aspose.com/slides/net/) अधिक जानकारी के लिए.