---
title: Φιλτράρισμα εργασιών ΚΑΙ Λειτουργία στο Aspose.Tasks
linktitle: Φιλτράρισμα εργασιών ΚΑΙ Λειτουργία στο Aspose.Tasks
second_title: Aspose.Tasks .NET API
description: Μάθετε πώς να αξιοποιείτε την κλάση στο Aspose.Tasks για .NET για να φιλτράρετε εργασίες έργου με βάση πολλαπλές συνθήκες. Συνδυάζοντας κριτήρια όπως εργασίες σύνοψης και μη μηδενικά χαρακτηριστικά.
type: docs
weight: 10
url: /el/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## Εισαγωγή

Σε αυτό το σεμινάριο, θα διερευνήσουμε πώς να εκτελείτε προηγμένο φιλτράρισμα εργασιών έργου στο Aspose.Tasks για .NET χρησιμοποιώντας το`Util.And` τάξη. Αυτή η ισχυρή δυνατότητα επιτρέπει στους προγραμματιστές να φιλτράρουν αποτελεσματικά τις εργασίες βάσει πολλαπλών κριτηρίων.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:

1. Βασικές γνώσεις προγραμματισμού C#.
2.  Εγκαταστάθηκε Aspose.Tasks για .NET. Εάν δεν το έχετε κάνει ακόμα, μπορείτε να το κατεβάσετε από[αυτόν τον σύνδεσμο](https://releases.aspose.com/tasks/net/).
3. Ένα ολοκληρωμένο περιβάλλον ανάπτυξης (IDE) όπως το Visual Studio για τη σύνταξη και εκτέλεση του κώδικα.

## Εισαγωγή χώρων ονομάτων

Για να ξεκινήσετε, πρέπει να εισαγάγετε τους απαιτούμενους χώρους ονομάτων στο έργο C#. Αυτό θα σας επιτρέψει να έχετε πρόσβαση στις λειτουργίες που παρέχονται από το Aspose.Tasks.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## Βήμα 1: Αρχικοποιήστε το έργο και συλλέξτε εργασίες

 Αρχικά, αρχικοποιήστε ένα έργο Aspose.Tasks και συγκεντρώστε όλες τις εργασίες μέσα σε αυτό. Για λόγους επίδειξης, θα υποθέσουμε ότι υπάρχει ένα αρχείο έργου με το όνομα`Project2.mpp`.

```csharp
// Διαδρομή στον κατάλογο εγγράφων
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// Συλλέξτε όλες τις παιδικές εργασίες
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## Βήμα 2: Καθορίστε τις συνθήκες φίλτρου

Σε αυτό το βήμα, θα ορίσουμε τις συνθήκες για το φιλτράρισμα των εργασιών. Στο παράδειγμά μας, θα δημιουργήσουμε δύο συνθήκες: μία για να φιλτράρουμε τις εργασίες σύνοψης και μία άλλη για να διασφαλίσουμε ότι οι εργασίες δεν είναι μηδενικές.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## Βήμα 3: Συνδυάστε τις συνθήκες με τη λειτουργία AND

 Το επόμενο βήμα είναι να συνδυάσετε αυτές τις συνθήκες χρησιμοποιώντας το`Util.And` τάξη. Αυτό μας επιτρέπει να δημιουργήσουμε μια σύνθετη συνθήκη που επιβάλλει και τα δύο κριτήρια.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## Βήμα 4: Εφαρμογή των εργασιών συνδυασμένης συνθήκης και φίλτρου

Τώρα, ας εφαρμόσουμε τη συνδυασμένη συνθήκη στις συλλεγμένες εργασίες για να φιλτράρουμε τις συγκεκριμένες εργασίες που πληρούν και τις δύο συνθήκες.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## Βήμα 5: Εξαγωγή των φιλτραρισμένων εργασιών

Τέλος, θα επαναλάβουμε τις φιλτραρισμένες εργασίες μας και θα εξάγουμε σχετικές λεπτομέρειες. Αυτό θα μας βοηθήσει να κατανοήσουμε τις εργασίες που πληρούν τα κριτήριά μας.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## Σύναψη

 Σε αυτό το σεμινάριο, δείξαμε πώς να εκτελείτε προηγμένες λειτουργίες φιλτραρίσματος στο Aspose.Tasks για .NET χρησιμοποιώντας το`Util.And`τάξη. Συνδυάζοντας πολλαπλές συνθήκες, μπορούμε να φιλτράρουμε αποτελεσματικά τις εργασίες, ενισχύοντας έτσι τη χρησιμότητα των εφαρμογών διαχείρισης έργων μας.

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Tasks για .NET;

Το Aspose.Tasks for .NET είναι ένα ολοκληρωμένο API σχεδιασμένο για προγραμματιστές να χειρίζονται αρχεία Microsoft Project μέσω προγραμματισμού εντός εφαρμογών .NET.

### Μπορώ να συνδυάσω περισσότερες από δύο συνθήκες χρησιμοποιώντας το Util.And;

 Ναί! Ο`Util.And` class σάς επιτρέπει να συνδυάσετε πολλαπλές συνθήκες, επιτρέποντας πολύπλοκη λογική φιλτραρίσματος προσαρμοσμένη στις ανάγκες σας.

### Υπάρχει διαθέσιμη δωρεάν δοκιμαστική έκδοση για το Aspose.Tasks;

 Ναι, μπορείτε να κάνετε λήψη μιας δωρεάν δοκιμαστικής έκδοσης από[αυτόν τον σύνδεσμο](https://releases.aspose.com/).

### Πού μπορώ να βρω αναλυτική τεκμηρίωση για το Aspose.Tasks;

 Λεπτομερής τεκμηρίωση είναι διαθέσιμη[εδώ](https://reference.aspose.com/tasks/net/).

### Πώς μπορώ να αναζητήσω υποστήριξη για το Aspose.Tasks;

 Η υποστήριξη είναι διαθέσιμη μέσω του φόρουμ κοινότητας Aspose.Tasks, στο οποίο μπορείτε να έχετε πρόσβαση[εδώ](https://forum.aspose.com/c/tasks/15).