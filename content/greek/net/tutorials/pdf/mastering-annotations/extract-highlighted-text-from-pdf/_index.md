---
title: Εξαγωγή επισημασμένου κειμένου από αρχεία PDF χρησιμοποιώντας το Aspose.PDF για .NET
linktitle: Εξαγωγή επισημασμένου κειμένου από αρχεία PDF χρησιμοποιώντας το Aspose.PDF για .NET
second_title: Aspose.PDF για Αναφορά API .NET
description: Ξεκλειδώστε τις δυνατότητες των εγγράφων PDF σας μαθαίνοντας πώς να εξάγετε επισημασμένο κείμενο με το Aspose.PDF για .NET. Αυτός ο περιεκτικός οδηγός σας καθοδηγεί σε κάθε βήμα, από τη ρύθμιση έως την υλοποίηση.
type: docs
weight: 60
url: /el/net/tutorials/pdf/mastering-annotations/extract-highlighted-text-from-pdf/
---
## Εισαγωγή

Όταν εργάζεστε με αρχεία PDF, η εξαγωγή επισημασμένου κειμένου μπορεί να είναι απαραίτητη για την ανάλυση δεδομένων, την αναθεώρηση περιεχομένου ή την οργάνωση σημειώσεων. Εάν χρησιμοποιείτε το Aspose.PDF για .NET, είστε τυχεροί. Αυτό το σεμινάριο παρέχει σαφείς, βήμα προς βήμα οδηγίες για τον τρόπο αποτελεσματικής εξαγωγής επισημασμένου κειμένου από ένα έγγραφο PDF.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα εξής:

-  Aspose.PDF για .NET Library: Κάντε λήψη της βιβλιοθήκης από το[σελίδα έκδοσης](https://releases.aspose.com/pdf/net/).
- Περιβάλλον Ανάπτυξης: Ένα περιβάλλον εργασίας όπως το Visual Studio.
- Βασικές γνώσεις C#: Απαραίτητη η εξοικείωση με την C# και τον αντικειμενοστραφή προγραμματισμό.
-  Aspose License: Ενώ μπορείτε να ξεκινήσετε με μια δωρεάν δοκιμή, α[προσωρινή άδεια](https://purchase.aspose.com/temporary-license/) ή πλήρη άδεια από[εδώ](https://purchase.aspose.com/buy) θα παρέχει απεριόριστη πρόσβαση.

## Εισαγωγή απαραίτητων χώρων ονομάτων

Ξεκινήστε εισάγοντας τους απαιτούμενους χώρους ονομάτων στο έργο σας C#:

```csharp
using Aspose.Pdf.Text;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

Αυτοί οι χώροι ονομάτων παρέχουν πρόσβαση στις κλάσεις και τις μεθόδους που απαιτούνται για το χειρισμό εγγράφων PDF και σχολιασμών.

## Βήμα 1: Ρυθμίστε τον κατάλογο του έργου σας

Καθορίστε τον κατάλογο στον οποίο βρίσκεται το αρχείο PDF:

```csharp
// Διαδρομή στον κατάλογο εγγράφων.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Φροντίστε να αντικαταστήσετε τη διαδρομή με τον πραγματικό κατάλογο του αρχείου PDF σας.

## Βήμα 2: Φορτώστε το έγγραφο PDF

Φορτώστε το έγγραφο PDF με τον ακόλουθο κώδικα:

```csharp
Document doc = new Document(dataDir + "ExtractHighlightedText.pdf");
```

Βεβαιωθείτε ότι το καθορισμένο αρχείο υπάρχει στον δεδομένο κατάλογο.

## Βήμα 3: Πρόσβαση στους σχολιασμούς στη σελίδα

Για να αποκτήσετε πρόσβαση στους σχολιασμούς, πραγματοποιήστε αναζήτηση στους σχολιασμούς στη σελίδα που επιθυμείτε (σε αυτήν την περίπτωση, στην πρώτη σελίδα):

```csharp
foreach (Annotation annotation in doc.Pages[1].Annotations)
{
    if (annotation is TextMarkupAnnotation)
    {
        TextMarkupAnnotation highlightedAnnotation = annotation as TextMarkupAnnotation;
```

 Αυτός ο κώδικας φιλτράρει για`TextMarkupAnnotation` τύπους, που αντιπροσωπεύουν τα κυριότερα σημεία.

## Βήμα 4: Εξαγάγετε το επισημασμένο κείμενο

Τώρα, εξαγάγετε και εμφανίστε το κείμενο από τους επισημασμένους σχολιασμούς:

```csharp
        TextFragmentCollection collection = highlightedAnnotation.GetMarkedTextFragments();
        foreach (TextFragment tf in collection)
        {
            Console.WriteLine(tf.Text);
        }
    }
}
```

Αυτό ανακτά όλα τα επισημασμένα τμήματα κειμένου που σχετίζονται με την επισήμανση και τα εκτυπώνει στην κονσόλα.

## Σύναψη

Η εξαγωγή επισημασμένου κειμένου από ένα PDF χρησιμοποιώντας το Aspose.PDF για .NET είναι απλή και μπορεί να βελτιώσει σημαντικά τη διαδικασία χειρισμού των εγγράφων σας. Ακολουθώντας τα βήματα που περιγράφονται παραπάνω, μπορείτε να συγκεντρώσετε αποτελεσματικά επισημασμένο κείμενο για διάφορες εφαρμογές, όπως προετοιμασία αναφορών ή ανάλυση δεδομένων.

## Συχνές ερωτήσεις

### Μπορώ να εξαγάγω άλλους τύπους σχολιασμών;
 Ναι, απλώς προσαρμόστε το`if` προϋπόθεση να περιλαμβάνει διαφορετικούς τύπους σχολιασμού όπως`TextAnnotation` ή`StampAnnotation`.

### Πώς μπορώ να εξαγάγω επισημασμένο κείμενο από όλες τις σελίδες PDF;
Μπορείτε να κάνετε βρόχο σε όλες τις σελίδες χρησιμοποιώντας:
```csharp
for (int i = 1; i <= doc.Pages.Count; i++)
{
    foreach (Annotation annotation in doc.Pages[i].Annotations) { ... }
}
```

### Είναι απαραίτητη μια άδεια χρήσης για το Aspose.PDF για .NET;
 Μια δωρεάν δοκιμή είναι διαθέσιμη, αλλά σκεφτείτε α[προσωρινή άδεια](https://purchase.aspose.com/temporary-license/) ή πλήρη άδεια για πλήρη πρόσβαση.

### Μπορώ να αποθηκεύσω το εξαγόμενο κείμενο σε ένα αρχείο;
Απολύτως! Μπορείτε να τροποποιήσετε τον κώδικα για να γράψετε το εξαγόμενο κείμενο σε ένα αρχείο κειμένου.

### Το Aspose.PDF υποστηρίζει άλλες πλατφόρμες;
Ναι, το Aspose.PDF υποστηρίζει επίσης Java και άλλες πλατφόρμες, παρέχοντας παρόμοια λειτουργικότητα.