---
title: Προστασία γραμμών στο φύλλο εργασίας χρησιμοποιώντας το Aspose.Cells
linktitle: Προστασία γραμμών στο φύλλο εργασίας χρησιμοποιώντας το Aspose.Cells
second_title: Aspose.Cells .NET Excel Processing API
description: Μάθετε πώς να ασφαλίζετε ευαίσθητες πληροφορίες στα φύλλα εργασίας του Excel προστατεύοντας συγκεκριμένες σειρές χρησιμοποιώντας το Aspose.Cells για .NET. Αυτό το ολοκληρωμένο σεμινάριο καλύπτει τα πάντα, από τη ρύθμιση του περιβάλλοντος σας.
type: docs
weight: 18
url: /el/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## Εισαγωγή

Η εργασία με αρχεία Excel μέσω προγραμματισμού συχνά απαιτεί όχι μόνο χειρισμό δεδομένων αλλά και προστασία δεδομένων. Η προστασία συγκεκριμένων σειρών σε ένα φύλλο εργασίας μπορεί να είναι ζωτικής σημασίας για τη διαφύλαξη ευαίσθητων πληροφοριών ή την αποτροπή τυχαίων επεξεργασιών. Σε αυτό το σεμινάριο, θα διερευνήσουμε πώς να προστατεύσουμε σειρές σε ένα φύλλο εργασίας του Excel χρησιμοποιώντας το Aspose.Cells για .NET. Θα σας καθοδηγήσουμε στα απαραίτητα βήματα, από τη ρύθμιση του περιβάλλοντος σας έως την εφαρμογή λειτουργιών προστασίας σειρών με απλό τρόπο.

## Προαπαιτούμενα
Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα εξής:

1.  Aspose.Cells για .NET: Κάντε λήψη και εγκαταστήστε το από το[Σελίδα λήψης Aspose Cells](https://releases.aspose.com/cells/net/).
2. Visual Studio ή οποιοδήποτε .NET IDE: Χρειάζεστε ένα περιβάλλον ανάπτυξης. Συνιστάται το Visual Studio, αλλά αρκεί οποιοδήποτε IDE συμβατό με .NET.
3. Βασικές γνώσεις C#: Η εξοικείωση με τον προγραμματισμό C# θα σας βοηθήσει να ακολουθήσετε και να τροποποιήσετε το παράδειγμα κώδικα όπως απαιτείται.
4.  Aspose.Cells API Documentation: Ελέγξτε το[Aspose.Cells για τεκμηρίωση .NET](https://reference.aspose.com/cells/net/) για μια επισκόπηση της δομής και των μεθόδων της τάξης.

Αφού έχετε έτοιμα τα προαπαιτούμενα, μπορούμε να προχωρήσουμε στην υλοποίηση.

## Εισαγωγή απαραίτητων πακέτων
Ξεκινήστε εισάγοντας τα απαιτούμενα πακέτα στο έργο σας C#. Αυτές οι βιβλιοθήκες είναι απαραίτητες για την αλληλεπίδραση με αρχεία Excel.

```csharp
using System.IO;
using Aspose.Cells;
```

## Βήμα 1: Δημιουργήστε ένα νέο βιβλίο εργασίας και ένα νέο φύλλο εργασίας
Πριν εφαρμόσετε οποιεσδήποτε ρυθμίσεις προστασίας, δημιουργήστε ένα νέο βιβλίο εργασίας και επιλέξτε το φύλλο εργασίας με το οποίο θέλετε να εργαστείτε.

```csharp
// Καθορίστε τη διαδρομή προς τον κατάλογο εγγράφων.
string dataDir = "Your Document Directory";
// Δημιουργήστε τον κατάλογο εάν δεν υπάρχει.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

// Δημιουργήστε ένα νέο βιβλίο εργασίας και επιλέξτε το πρώτο φύλλο εργασίας.
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## Βήμα 2: Ορισμός Style και StyleFlag Objects
Καθορίστε τα αντικείμενα σημαίας στυλ και στυλ, τα οποία θα σας επιτρέψουν να τροποποιήσετε τις ιδιότητες των κελιών, όπως το κλείδωμα ή το ξεκλείδωμα τους.

```csharp
// Καθορίστε τα αντικείμενα σημαίας στυλ και στυλ.
Style style;
StyleFlag flag;
```

## Βήμα 3: Ξεκλειδώστε όλες τις στήλες στο φύλλο εργασίας
Από προεπιλογή, όλα τα κελιά σε ένα φύλλο εργασίας του Excel είναι κλειδωμένα. Για να προστατεύσετε μόνο συγκεκριμένες σειρές, ξεκλειδώστε πρώτα όλες τις στήλες.

```csharp
// Κάντε βρόχο σε όλες τις στήλες και ξεκλειδώστε τις.
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## Βήμα 4: Κλείδωμα συγκεκριμένων σειρών
Τώρα, κλειδώστε τις σειρές που θέλετε να προστατέψετε. Σε αυτό το παράδειγμα, θα κλειδώσουμε την πρώτη σειρά.

```csharp
// Κλειδώστε την πρώτη σειρά.
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

Μπορείτε να επαναλάβετε αυτό το βήμα για τυχόν πρόσθετες σειρές που θέλετε να κλειδώσετε.

## Βήμα 5: Προστατέψτε το Φύλλο
Με τις απαραίτητες σειρές κλειδωμένες, ήρθε η ώρα να προστατέψετε το φύλλο εργασίας. Αυτό θα αποτρέψει τροποποιήσεις στις κλειδωμένες σειρές εκτός εάν αφαιρεθεί η προστασία.

```csharp
// Προστατέψτε το φύλλο.
sheet.Protect(ProtectionType.All);
```

## Βήμα 6: Αποθηκεύστε το βιβλίο εργασίας
Τέλος, αποθηκεύστε το βιβλίο εργασίας με τις εφαρμοσμένες αλλαγές. Μπορείτε να επιλέξετε από διάφορες μορφές, όπως Excel 97-2003 ή νεότερες εκδόσεις.

```csharp
// Αποθηκεύστε το αρχείο Excel.
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## Σύναψη
Συγχαρητήρια! Μάθατε με επιτυχία πώς να προστατεύετε σειρές σε ένα φύλλο εργασίας του Excel χρησιμοποιώντας το Aspose.Cells για .NET. Ακολουθώντας αυτά τα βήματα, μπορείτε να ξεκλειδώσετε ή να κλειδώσετε σειρές ή στήλες όπως απαιτείται και να εφαρμόσετε προστασία για να διατηρήσετε την ακεραιότητα των δεδομένων σας.

## Συχνές ερωτήσεις
### Πώς μπορώ να προστατεύσω πολλές σειρές ταυτόχρονα;
Μπορείτε να κάνετε βρόχο ανάμεσα σε πολλαπλούς δείκτες σειρών και να εφαρμόσετε το στυλ κλειδώματος σε καθένα ξεχωριστά.

### Μπορώ να ορίσω κωδικό πρόσβασης για προστασία φύλλου;
 Ναι, μπορείτε να περάσετε έναν κωδικό πρόσβασης στο`sheet.Protect()` μέθοδος επιβολής προστασίας με κωδικό πρόσβασης.

### Μπορώ να ξεκλειδώσω συγκεκριμένα κελιά αντί για ολόκληρες στήλες;
Ναι, μπορείτε να ξεκλειδώσετε μεμονωμένα κελιά τροποποιώντας τις ιδιότητες στυλ τους αντί να ξεκλειδώνετε ολόκληρες στήλες.

### Τι θα συμβεί αν προσπαθήσω να επεξεργαστώ μια προστατευμένη σειρά;
Όταν μια σειρά προστατεύεται, το Excel θα αποτρέψει τυχόν αλλαγές στα κλειδωμένα κελιά, εκτός εάν το φύλλο δεν είναι προστατευμένο.

### Μπορώ να προστατεύσω συγκεκριμένα εύρη εντός μιας σειράς;
 Ναί! Μπορείτε να κλειδώσετε μεμονωμένες περιοχές σε μια σειρά, ρυθμίζοντας το`IsLocked` ιδιότητα για συγκεκριμένα κελιά εντός αυτού του εύρους.