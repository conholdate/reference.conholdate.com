---
title: Αποθήκευση εγγράφων OneNote σε PDF χρησιμοποιώντας το Aspose.Note για .NET
linktitle: Αποθήκευση εγγράφων OneNote σε PDF
second_title: Aspose.Note .NET API
description: Μάθετε πώς να αποθηκεύετε αποτελεσματικά έγγραφα του Microsoft OneNote ως αρχεία PDF χρησιμοποιώντας το Aspose.Note για .NET. Αυτός ο οδηγός σας καθοδηγεί στις απαραίτητες προϋποθέσεις και προσφέρει χρήσιμες συχνές ερωτήσεις.
type: docs
weight: 26
url: /el/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Εισαγωγή

Σε αυτό το σεμινάριο, θα εξερευνήσουμε τον τρόπο αποθήκευσης εγγράφων σε μορφή PDF χρησιμοποιώντας το Aspose.Note για .NET. Το Aspose.Note είναι μια ισχυρή βιβλιοθήκη που επιτρέπει στους προγραμματιστές να εργάζονται με αρχεία Microsoft OneNote μέσω προγραμματισμού. Θα καλύψουμε τις προϋποθέσεις, θα εισαγάγουμε χώρους ονομάτων και θα παρέχουμε οδηγούς βήμα προς βήμα για την αποθήκευση εγγράφων σε PDF σε διάφορες διατάξεις σελίδων.

## Προαπαιτούμενα
1. Visual Studio: Βεβαιωθείτε ότι είναι εγκατεστημένο.
2. Aspose.Note για .NET: Κάντε λήψη και εγκατάσταση της βιβλιοθήκης.
3. Γνώσεις C#: Απαιτείται βασική κατανόηση της γλώσσας.

## Εισαγωγή απαραίτητων χώρων ονομάτων
Πριν συνεχίσετε, εισαγάγετε τους ακόλουθους χώρους ονομάτων στον κώδικά σας:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Βήμα 1: Αποθήκευση σε PDF με τις Ρυθμίσεις σελίδας Letter
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Ενημερώστε αυτήν τη διαδρομή
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Φορτώνει το έγγραφο του OneNote και το αποθηκεύει ως PDF χρησιμοποιώντας ρυθμίσεις σελίδας μεγέθους γράμματος.

## Βήμα 2: Αποθήκευση σε PDF με Ρυθμίσεις σελίδας A4 (Χωρίς όριο ύψους)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Ενημερώστε αυτήν τη διαδρομή
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Παρόμοιο με το Βήμα 1, αλλά χρησιμοποιεί ρυθμίσεις σελίδας Α4 χωρίς περιορισμούς ύψους.

## Σύναψη
Το σεμινάριο δείχνει με επιτυχία πώς να μετατρέψετε αρχεία OneNote σε μορφή PDF χρησιμοποιώντας το Aspose.Note. Χρησιμοποιώντας διαφορετικές ρυθμίσεις σελίδας, οι προγραμματιστές αποκτούν ευελιξία στη διαχείριση εγγράφων.

## Συχνές ερωτήσεις
### Μπορεί το Aspose.Note να χειριστεί πολύπλοκα αρχεία OneNote;
Ναι, χειρίζεται αποτελεσματικά διάφορες δυνατότητες σύνθετων αρχείων OneNote.

### Είναι το Aspose.Note κατάλληλο για εμπορικά έργα;
Ναι, μπορείτε να το χρησιμοποιήσετε για εμπορικές εφαρμογές μετά την αγορά άδειας.

### Το Aspose.Note προσφέρει δωρεάν δοκιμή;
Ναι, μια δωρεάν δοκιμή είναι διαθέσιμη για εξερεύνηση.

### Πού μπορώ να βρω τεκμηρίωση για το Aspose.Note;
Λεπτομερής τεκμηρίωση είναι διαθέσιμη στον ιστότοπο αναφοράς Aspose.

### Χρειάζεστε περαιτέρω βοήθεια;
Για ερωτήσεις και υποστήριξη, ανατρέξτε στο φόρουμ Aspose.Note.
