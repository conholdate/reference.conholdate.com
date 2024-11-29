---
title: Μετατροπή DGN σε PDF στο Aspose.CAD για .NET
linktitle: Μετατροπή DGN σε PDF στο Aspose.CAD για .NET
second_title: Aspose.CAD .NET - Μορφή αρχείου CAD και BIM
description: Μάθετε πώς να μετατρέπετε εύκολα αρχεία DGN σε PDF χρησιμοποιώντας την ισχυρή βιβλιοθήκη Aspose.CAD για .NET. Αυτός ο οδηγός βήμα προς βήμα έχει σχεδιαστεί για προγραμματιστές όλων των επιπέδων.
type: docs
weight: 12
url: /el/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Εισαγωγή

Η πλοήγηση στον κόσμο των αρχείων CAD μπορεί να είναι δύσκολη, αλλά με το Aspose.CAD για .NET, οι προγραμματιστές μπορούν εύκολα να χειριστούν και να μετατρέψουν διάφορες μορφές CAD. Μια κοινή ανάγκη είναι η μετατροπή αρχείων DGN σε PDF, τα οποία θα εξερευνήσουμε βήμα προς βήμα σε αυτό το σεμινάριο.

## Προαπαιτούμενα

Για να ακολουθήσετε, βεβαιωθείτε ότι έχετε τα εξής:

- Βασική επάρκεια στη C# και στο πλαίσιο .NET.
-  Εγκαταστάθηκε το Aspose.CAD για τη βιβλιοθήκη .NET. Μπορείτε να το κατεβάσετε[εδώ](https://releases.aspose.com/cad/net/).
- Ένα δείγμα αρχείου DGN (π.χ. Nikon_D90_Camera.dgn). 

## Βήμα 1: Εισαγάγετε τους απαιτούμενους χώρους ονομάτων

Ξεκινήστε εισάγοντας τους σχετικούς χώρους ονομάτων στο έργο σας C#:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Βήμα 2: Φορτώστε το αρχείο DGN

Καθορίστε τον κατάλογο για το αρχείο DGN και φορτώστε τον χρησιμοποιώντας τον ακόλουθο κώδικα:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Η πρόσθετη επεξεργασία θα γίνει εδώ...
}
```

## Βήμα 3: Διαμορφώστε τις επιλογές Rasterization

Στη συνέχεια, ρυθμίστε τις επιλογές ραστεροποίησης για να ορίσετε πώς θα αποδίδεται το DGN σας στο PDF:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Προσαρμόστε το πλάτος όπως χρειάζεται
    PageHeight = 300, // Ρυθμίστε το ύψος όπως χρειάζεται
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Βήμα 4: Δημιουργία επιλογών PDF

Καθορίστε τις επιλογές PDF, ενσωματώνοντας τις ρυθμίσεις ραστεροποίησης που διαμορφώθηκαν νωρίτερα:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Βήμα 5: Αποθηκεύστε το DGN ως PDF

Τέλος, αποθηκεύστε το αρχείο DGN ως PDF χρησιμοποιώντας τις επιλογές που έχετε διαμορφώσει:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Σύναψη

Συγχαρητήρια! Μετατρέψατε με επιτυχία ένα αρχείο DGN σε PDF χρησιμοποιώντας το Aspose.CAD για .NET. Αυτός ο απλός οδηγός σας καθοδήγησε στη φόρτωση του αρχείου DGN, στη ρύθμιση των επιλογών ραστεροποίησης και στην αποθήκευση της εξόδου ως PDF.

## Συχνές ερωτήσεις

### Χρειάζομαι προηγούμενη γνώση CAD για να χρησιμοποιήσω το Aspose.CAD;  
Απολύτως! Το Aspose.CAD έχει σχεδιαστεί για να απλοποιεί πολύπλοκες εργασίες CAD, καθιστώντας το προσβάσιμο για όλους τους προγραμματιστές, ανεξάρτητα από τις γνώσεις τους στο CAD.

### Πού μπορώ να βρω περισσότερους πόρους και τεκμηρίωση για το Aspose.CAD;  
 Μπορείτε να εξερευνήσετε αναλυτικούς οδηγούς και παραδείγματα στο[Τεκμηρίωση Aspose.CAD](https://reference.aspose.com/cad/net/).

### Υπάρχει διαθέσιμη δωρεάν δοκιμή για το Aspose.CAD;  
 Ναι, μπορείτε να αποκτήσετε δωρεάν δοκιμή[εδώ](https://releases.aspose.com/).

### Πώς μπορώ να πάρω μια προσωρινή άδεια για το Aspose.CAD;  
 Μπορείτε να ζητήσετε προσωρινές άδειες[εδώ](https://purchase.conholdate.com/temporary-license/).

### Χρειάζεστε βοήθεια ή έχετε ερωτήσεις;  
 Συμμετάσχετε στη συζήτηση στο[Φόρουμ Aspose.CAD](https://forum.aspose.com/c/cad/19) για κοινοτική υποστήριξη και έρευνες.