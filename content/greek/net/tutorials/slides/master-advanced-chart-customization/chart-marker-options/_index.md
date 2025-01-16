---
title: Επιλογές δείκτη γραφήματος στο σημείο δεδομένων στο Aspose.Slides .NET
linktitle: Επιλογές δείκτη γραφήματος στο σημείο δεδομένων στο Aspose.Slides .NET
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Μάθετε πώς να βελτιώσετε τα γραφήματα του PowerPoint με προσαρμοσμένες επιλογές δεικτών χρησιμοποιώντας το Aspose.Slides για .NET. Αυτός ο οδηγός βήμα προς βήμα καλύπτει προαπαιτούμενα, δημιουργία γραφήματος, μορφοποίηση σημείων δεδομένων και πολλά άλλα.
type: docs
weight: 11
url: /el/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Εισαγωγή

Η ενσωμάτωση οπτικών βοηθημάτων στις παρουσιάσεις είναι απαραίτητη για την αποτελεσματική επικοινωνία. Το Aspose.Slides for .NET παρέχει ισχυρά εργαλεία για τη δημιουργία και την προσαρμογή γραφημάτων, επιτρέποντας στους προγραμματιστές να βελτιώσουν τις παρουσιάσεις δεδομένων τους. Ένα από τα χαρακτηριστικά που ξεχωρίζουν είναι η δυνατότητα χρήσης επιλογών δεικτών γραφήματος σε σημεία δεδομένων, επιτρέποντας την ακριβή προσαρμογή για γραφήματα με επαγγελματική εμφάνιση. Αυτό το άρθρο θα σας καθοδηγήσει σε κάθε βήμα που χρειάζεται για να το πετύχετε.

## Προαπαιτούμενα

Πριν προχωρήσετε, βεβαιωθείτε για τα ακόλουθα:

-  Aspose.Slides for .NET Installed: Κάντε λήψη του από[εδώ](https://releases.aspose.com/slides/net/).
- Βασική εγκατάσταση: Ένα αρχείο παρουσίασης, όπως "Test.pptx", στον κατάλογο εργασίας σας.
- Περιβάλλον ανάπτυξης: Visual Studio ή αντίστοιχο, διαμορφωμένο για .NET.

## Εισαγωγή απαιτούμενων χώρων ονομάτων

Προσθέστε τους απαραίτητους χώρους ονομάτων στο έργο σας για απρόσκοπτη ανάπτυξη:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Βήμα 1: Δημιουργήστε ένα γράφημα στην παρουσίασή σας

Ξεκινήστε δημιουργώντας ένα προεπιλεγμένο γράφημα στην πρώτη διαφάνεια της παρουσίασής σας:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Αυτό προσθέτει α`LineWithMarkers` γράφημα στη διαφάνειά σας με καθορισμένες διαστάσεις.

## Βήμα 2: Ανακτήστε το Ευρετήριο φύλλου εργασίας δεδομένων γραφήματος

Το προεπιλεγμένο ευρετήριο φύλλου εργασίας δεδομένων γραφήματος είναι απαραίτητο για περαιτέρω προσαρμογή:

```csharp
int defaultWorksheetIndex = 0;
```

## Βήμα 3: Πρόσβαση στο Βιβλίο εργασίας δεδομένων γραφήματος

Για να χειριστείτε δεδομένα γραφήματος, ανακτήστε το σχετικό βιβλίο εργασίας:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Βήμα 4: Διαμόρφωση σειράς γραφημάτων και προσθήκη σημείων δεδομένων

Διαγράψτε τις προεπιλεγμένες σειρές και προσθέστε νέα σημεία δεδομένων για τη σειρά σας:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Προσθέστε σημεία δεδομένων στη σειρά
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Βήμα 5: Εφαρμόστε γεμίσματα εικόνας σε δείκτες σημείων δεδομένων

Οι προσαρμοσμένες εικόνες μπορούν να κάνουν τους δείκτες δεδομένων οπτικά ελκυστικούς:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Ορίστε προσαρμοσμένες εικόνες για δείκτες
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Βήμα 6: Προσαρμόστε το μέγεθος δείκτη

Τροποποιήστε το μέγεθος των δεικτών για να βελτιώσετε την ορατότητα:

```csharp
series.Marker.Size = 20;
```

## Βήμα 7: Αποθηκεύστε την ενημερωμένη παρουσίαση

Αποθηκεύστε την προσαρμοσμένη παρουσίαση στην επιθυμητή τοποθεσία:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Σύναψη

Το Aspose.Slides for .NET εξοπλίζει τους προγραμματιστές με εργαλεία για τη δημιουργία επαγγελματικών γραφημάτων με πλούσιες επιλογές προσαρμογής. Αξιοποιώντας τις επιλογές δεικτών γραφήματος, μπορείτε να βελτιώσετε σημαντικά την οπτική ελκυστικότητα και τη σαφήνεια των παρουσιάσεών σας. Αυτός ο οδηγός βήμα προς βήμα διασφαλίζει ότι ακόμη και πολύπλοκες προσαρμογές είναι απλές στην εφαρμογή.

## Συχνές ερωτήσεις

### Μπορώ να χρησιμοποιήσω οποιαδήποτε μορφή εικόνας για προσαρμογή δείκτη;
Ναι, το Aspose.Slides υποστηρίζει διάφορες μορφές εικόνας, συμπεριλαμβανομένων των JPEG, PNG και BMP, για προσαρμογή δείκτη.

### Πώς μπορώ να αλλάξω τον τύπο γραφήματος μετά τη δημιουργία;
 Για να αλλάξετε τον τύπο γραφήματος, μεταβείτε στο`chart.Type` ιδιοκτησίας και να εκχωρήσετε διαφορετική`ChartType`.

### Είναι το Aspose.Slides για .NET συμβατό με παλαιότερες εκδόσεις PowerPoint;
Ναι, υποστηρίζει συμβατότητα προς τα πίσω με παλαιότερες μορφές PowerPoint, εξασφαλίζοντας ευελιξία.

### Μπορώ να ενημερώσω δυναμικά τα δεδομένα γραφήματος;
 Απολύτως. Χρησιμοποιήστε το`IChartDataWorkbook` για να ενημερώσετε μέσω προγραμματισμού δεδομένα γραφήματος.

### Πού μπορώ να βρω περισσότερους πόρους;
 Εξερευνήστε το[Τεκμηρίωση Aspose.Slides](https://reference.aspose.com/slides/net/)ή εγγραφείτε στο[κοινοτικά φόρουμ](https://forum.aspose.com/) για υποστήριξη.