---
title: Aspose.Slides .NET में डेटा पॉइंट पर चार्ट मार्कर विकल्प
linktitle: Aspose.Slides .NET में डेटा पॉइंट पर चार्ट मार्कर विकल्प
second_title: Aspose.Slides .NET पावरपॉइंट प्रोसेसिंग API
description: जानें कि .NET के लिए Aspose.Slides का उपयोग करके कस्टमाइज़्ड मार्कर विकल्पों के साथ अपने पावरपॉइंट चार्ट को कैसे बेहतर बनाया जाए। यह चरण-दर-चरण मार्गदर्शिका पूर्वापेक्षाएँ, चार्ट निर्माण, डेटा पॉइंट फ़ॉर्मेटिंग और बहुत कुछ को कवर करती है।
type: docs
weight: 11
url: /hi/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## परिचय

प्रभावशाली संचार के लिए प्रस्तुतियों में दृश्य सहायता को शामिल करना आवश्यक है। Aspose.Slides for .NET चार्ट बनाने और उन्हें अनुकूलित करने के लिए मजबूत उपकरण प्रदान करता है, जिससे डेवलपर्स को अपने डेटा प्रस्तुतियों को बेहतर बनाने में मदद मिलती है। सबसे बढ़िया विशेषताओं में से एक डेटा बिंदुओं पर चार्ट मार्कर विकल्पों का उपयोग करने की क्षमता है, जो पेशेवर दिखने वाले चार्ट के लिए सटीक अनुकूलन की अनुमति देता है। यह लेख आपको इसे प्राप्त करने के लिए आवश्यक हर चरण से अवगत कराएगा।

## आवश्यक शर्तें

आगे बढ़ने से पहले, निम्नलिखित सुनिश्चित करें:

-  Aspose.Slides for .NET स्थापित: इसे यहाँ से डाउनलोड करें[यहाँ](https://releases.aspose.com/slides/net/).
- मूल सेटअप: आपकी कार्यशील निर्देशिका में एक प्रस्तुति फ़ाइल, जैसे "Test.pptx".
- विकास परिवेश: विजुअल स्टूडियो या समतुल्य, .NET के लिए कॉन्फ़िगर किया गया।

## आवश्यक नामस्थान आयात करना

निर्बाध विकास के लिए अपनी परियोजना में आवश्यक नामस्थान जोड़ें:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## चरण 1: अपनी प्रस्तुति में एक चार्ट बनाएं

अपनी प्रस्तुति की पहली स्लाइड पर एक डिफ़ॉल्ट चार्ट बनाकर आरंभ करें:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 इससे एक`LineWithMarkers` चार्ट को निर्दिष्ट आयामों के साथ अपनी स्लाइड पर जोड़ें।

## चरण 2: चार्ट डेटा वर्कशीट इंडेक्स पुनः प्राप्त करें

आगे के अनुकूलन के लिए डिफ़ॉल्ट चार्ट डेटा वर्कशीट इंडेक्स आवश्यक है:

```csharp
int defaultWorksheetIndex = 0;
```

## चरण 3: चार्ट डेटा वर्कबुक तक पहुँचें

चार्ट डेटा में हेरफेर करने के लिए, संबंधित कार्यपुस्तिका पुनः प्राप्त करें:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## चरण 4: चार्ट श्रृंखला कॉन्फ़िगर करें और डेटा बिंदु जोड़ें

डिफ़ॉल्ट श्रृंखला साफ़ करें और अपनी श्रृंखला के लिए नए डेटा बिंदु जोड़ें:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// श्रृंखला में डेटा बिंदु जोड़ें
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## चरण 5: डेटा पॉइंट मार्कर पर पिक्चर फिल लागू करें

कस्टम छवियां डेटा मार्करों को दृष्टिगत रूप से आकर्षक बना सकती हैं:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// मार्करों के लिए कस्टम छवियाँ सेट करें
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## चरण 6: मार्कर का आकार अनुकूलित करें

दृश्यता बढ़ाने के लिए मार्करों का आकार संशोधित करें:

```csharp
series.Marker.Size = 20;
```

## चरण 7: अपडेट की गई प्रस्तुति को सहेजें

अनुकूलित प्रस्तुति को अपने इच्छित स्थान पर सहेजें:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## निष्कर्ष

Aspose.Slides for .NET डेवलपर्स को समृद्ध अनुकूलन विकल्पों के साथ पेशेवर चार्ट बनाने के लिए उपकरण प्रदान करता है। चार्ट मार्कर विकल्पों का लाभ उठाकर, आप अपनी प्रस्तुतियों की दृश्य अपील और स्पष्टता को महत्वपूर्ण रूप से बढ़ा सकते हैं। यह चरण-दर-चरण मार्गदर्शिका सुनिश्चित करती है कि जटिल अनुकूलन भी लागू करना आसान है।

## अक्सर पूछे जाने वाले प्रश्न

### क्या मैं मार्कर अनुकूलन के लिए किसी भी छवि प्रारूप का उपयोग कर सकता हूँ?
हां, Aspose.Slides मार्कर अनुकूलन के लिए JPEG, PNG, और BMP सहित विभिन्न छवि प्रारूपों का समर्थन करता है।

### निर्माण के बाद मैं चार्ट का प्रकार कैसे बदल सकता हूँ?
 चार्ट प्रकार बदलने के लिए,`chart.Type` संपत्ति और एक अलग असाइन करें`ChartType`.

### क्या Aspose.Slides for .NET पुराने PowerPoint संस्करणों के साथ संगत है?
हां, यह पुराने पावरपॉइंट प्रारूपों के साथ पश्चगामी संगतता का समर्थन करता है, जिससे बहुमुखी प्रतिभा सुनिश्चित होती है।

### क्या मैं चार्ट डेटा को गतिशील रूप से अपडेट कर सकता हूँ?
 बिल्कुल।`IChartDataWorkbook` चार्ट डेटा को प्रोग्रामेटिक रूप से अद्यतन करने के लिए.

### मुझे और अधिक संसाधन कहां मिल सकते हैं?
 पता लगाएं[Aspose.Slides दस्तावेज़ीकरण](https://reference.aspose.com/slides/net/)या शामिल हों[सामुदायिक मंच](https://forum.aspose.com/) समर्थन के लिए।