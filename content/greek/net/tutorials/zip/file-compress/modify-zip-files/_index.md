---
title: Τροποποίηση αρχείων Zip με το Aspose.Zip για .NET
linktitle: Τροποποίηση αρχείων Zip
second_title: Aspose.Zip .NET API για συμπίεση και αρχειοθέτηση αρχείων
description: Μάθετε πώς να εξάγετε, να διαγράφετε και να προσθέτετε καταχωρήσεις σε αρχεία zip μέσω προγραμματισμού, βελτιώνοντας τις δυνατότητες χειρισμού αρχείων σας.
type: docs
weight: 15
url: /el/net/tutorials/zip/file-compress/modify-zip-files/
---
## Εισαγωγή

Τα αρχεία zip είναι ζωτικής σημασίας για την οργάνωση και τη συμπίεση δεδομένων, αλλά πώς μπορείτε να τροποποιήσετε το περιεχόμενό τους μέσω προγραμματισμού; Η λύση βρίσκεται στο Aspose.Zip για .NET, μια ισχυρή βιβλιοθήκη που απλοποιεί τον χειρισμό αρχείων zip με C#. Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε βήμα προς βήμα στην εξαγωγή, τη διαγραφή και την προσθήκη καταχωρήσεων σε αρχεία zip.

## Προαπαιτούμενα

Πριν βουτήξουμε, βεβαιωθείτε ότι έχετε τα εξής:

1.  Aspose.Zip για .NET Library: Εγκαταστήστε τη βιβλιοθήκη στο έργο σας. Μπορείτε να το κατεβάσετε[εδώ](https://releases.aspose.com/zip/net/).
   
2.  Κατάλογος εγγράφων: Ρυθμίστε έναν κατάλογο για να αποθηκεύσετε τα αρχεία zip σας. Αντικαθιστώ`"Your Document Directory"` στον κωδικό με την πραγματική διαδρομή σας.

## Εισαγωγή απαραίτητων χώρων ονομάτων

Ξεκινήστε εισάγοντας τους απαιτούμενους χώρους ονομάτων:

```csharp
using Aspose.Zip;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```

## Βήμα 1: Ανοίξτε το εξωτερικό αρχείο Zip

Ξεκινήστε ανοίγοντας το κύριο αρχείο zip (εξωτερικό zip):

```csharp
string dataDir = "Your Data Directory";
using (Archive outer = new Archive(dataDir + "outer.zip"))
{
    // Προχωρήστε στον εντοπισμό των εσωτερικών εγγραφών φερμουάρ
}
```

## Βήμα 2: Προσδιορίστε τις εσωτερικές καταχωρήσεις φερμουάρ

Στη συνέχεια, εντοπίστε και προετοιμαστείτε να διαγράψετε τυχόν εσωτερικά αρχεία zip:

```csharp
List<ArchiveEntry> entriesToDelete = new List<ArchiveEntry>();
List<string> namesToInsert = new List<string>();
List<MemoryStream> contentToInsert = new List<MemoryStream>();

foreach (ArchiveEntry entry in outer.Entries)
{
    if (entry.Name.EndsWith(".zip", StringComparison.InvariantCultureIgnoreCase))
    {
        entriesToDelete.Add(entry);
        
        using (MemoryStream innerCompressed = new MemoryStream())
        {
            entry.Open().CopyTo(innerCompressed);
            
            // Εξαγωγή εσωτερικών εγγραφών
            using (Archive inner = new Archive(innerCompressed))
            {
                foreach (ArchiveEntry ie in inner.Entries)
                {
                    namesToInsert.Add(ie.Name);
                    MemoryStream content = new MemoryStream();
                    ie.Open().CopyTo(content);
                    contentToInsert.Add(content);
                }
            }
        }
    }
}
```

## Βήμα 3: Διαγράψτε τις καταχωρήσεις εσωτερικού αρχείου

Αφού συγκεντρώσετε τις καταχωρήσεις που χρειάζεστε, διαγράψτε τις εσωτερικές καταχωρήσεις zip:

```csharp
foreach (ArchiveEntry e in entriesToDelete)
{
    outer.DeleteEntry(e);
}
```

## Βήμα 4: Προσθέστε τροποποιημένες καταχωρήσεις στο Outer Zip

Τώρα, μπορείτε να προσθέσετε τις καταχωρήσεις που εξήχθησαν ξανά στο εξωτερικό σας αρχείο zip:

```csharp
for (int i = 0; i < namesToInsert.Count; i++)
{
    outer.CreateEntry(namesToInsert[i], contentToInsert[i]);
}
```

## Βήμα 5: Αποθηκεύστε το τροποποιημένο αρχείο Zip

Τέλος, αποθηκεύστε τις αλλαγές σας σε ένα νέο αρχείο zip:

```csharp
outer.Save(dataDir + "flatten.zip");
```

## Σύναψη

Το Aspose.Zip για .NET παρέχει έναν ισχυρό και απλό τρόπο χειρισμού αρχείων zip μέσω προγραμματισμού. Αυτό το σεμινάριο κάλυψε την εξαγωγή, τη διαγραφή και την προσθήκη καταχωρήσεων σε ένα αρχείο zip, απεικονίζοντας την ευελιξία της βιβλιοθήκης. Εξερευνήστε διαφορετικά σενάρια και βελτιώστε τις δεξιότητές σας χειρισμού αρχείων!

## Συχνές ερωτήσεις

### Μπορώ να χρησιμοποιήσω το Aspose.Zip για .NET με άλλες γλώσσες προγραμματισμού;
Το Aspose.Zip έχει σχεδιαστεί κυρίως για εφαρμογές .NET, αλλά το Aspose προσφέρει παρόμοιες βιβλιοθήκες για διάφορες γλώσσες προγραμματισμού.

### Υπάρχει διαθέσιμη δωρεάν δοκιμή για το Aspose.Zip για .NET;
 Ναι, μια δωρεάν δοκιμή είναι διαθέσιμη για λήψη[εδώ](https://releases.aspose.com/).

### Πώς μπορώ να λάβω υποστήριξη για το Aspose.Zip για .NET;
 Επισκεφθείτε το[Aspose.Zip φόρουμ](https://forum.aspose.com/c/zip/37) για υποστήριξη και συζητήσεις.

### Μπορώ να αγοράσω μια προσωρινή άδεια χρήσης για το Aspose.Zip για .NET;
Ναι, μπορείτε να αποκτήσετε προσωρινή άδεια[εδώ](https://purchase.conholdate.com/temporary-license/).

### Πού μπορώ να βρω την τεκμηρίωση για το Aspose.Zip για .NET;
 Η πλήρης τεκμηρίωση είναι διαθέσιμη[εδώ](https://reference.aspose.com/zip/net/).