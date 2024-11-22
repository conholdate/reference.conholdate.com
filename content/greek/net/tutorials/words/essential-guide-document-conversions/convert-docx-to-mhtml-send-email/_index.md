---
title: Μετατρέψτε το DOCX σε MHTML και στείλτε email χρησιμοποιώντας το Aspose.Words για .NET
linktitle: Μετατρέψτε το DOCX σε MHTML και στείλτε email χρησιμοποιώντας το Aspose.Words για .NET
second_title: Aspose.Words Document Processing API
description: Αυτός ο περιεκτικός οδηγός παρέχει ένα βήμα προς βήμα σεμινάριο σχετικά με τη μετατροπή εγγράφων DOCX σε μορφή MHTML και την αποστολή τους μέσω email χρησιμοποιώντας τις βιβλιοθήκες Aspose.Words και Aspose.Email στο .NET.
type: docs
weight: 10
url: /el/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Εισαγωγή

Στο σημερινό ψηφιακό τοπίο, η μετατροπή εγγράφων μεταξύ μορφών και η αποστολή τους μέσω email είναι μια κοινή εργασία. Αυτός ο οδηγός θα σας καθοδηγήσει στη μετατροπή ενός αρχείου DOCX σε μορφή MHTML και στην αποστολή του μέσω email χρησιμοποιώντας τις πανίσχυρες βιβλιοθήκες Aspose.Words και Aspose.Email για .NET. Θα αναλύσουμε κάθε βήμα με σαφήνεια, διασφαλίζοντας ότι μπορείτε να το ακολουθήσετε με ευκολία. Ας ξεκινήσουμε!

## Προαπαιτούμενα

Πριν ξεκινήσετε τη διαδικασία, βεβαιωθείτε ότι έχετε ρυθμίσει τα ακόλουθα:

1.  Aspose.Words για .NET: Κάντε λήψη και εγκατάσταση της βιβλιοθήκης από το[Σελίδα εκδόσεων Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email για .NET: Κάντε λήψη και εγκατάσταση αυτής της βιβλιοθήκης από το[Σελίδα εκδόσεων Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: Βεβαιωθείτε ότι έχετε εγκαταστήσει το .NET Framework στον υπολογιστή σας.
4. Διακομιστής SMTP: Θα χρειαστείτε πρόσβαση σε διακομιστή SMTP για να στείλετε email.

## Εισαγωγή απαραίτητων χώρων ονομάτων

Για να χρησιμοποιήσετε τα Aspose.Words και Aspose.Email στο έργο σας, πρέπει να εισαγάγετε τους απαιτούμενους χώρους ονομάτων. Προσθέστε τα ακόλουθα χρησιμοποιώντας οδηγίες στην κορυφή του αρχείου C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Βήμα 1: Φορτώστε το έγγραφο DOCX

 Ξεκινήστε φορτώνοντας το έγγραφο DOCX που θέλετε να μετατρέψετε. Χρησιμοποιήστε το`Document` τάξη από το Aspose.Words για να το πετύχετε αυτό.

```csharp
// Καθορίστε τη διαδρομή προς τον κατάλογο εγγράφων σας.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Βήμα 2: Αποθηκεύστε το Έγγραφο ως MHTML

 Στη συνέχεια, μετατρέψτε το φορτωμένο έγγραφο σε μορφή MHTML. Αυτό γίνεται χρησιμοποιώντας το`Save` μέθοδος του`Document`τάξη.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Επαναφέρετε τη θέση ροής στην αρχή για ανάγνωση.
    stream.Position = 0;
}
```

## Βήμα 3: Δημιουργήστε ένα μήνυμα ηλεκτρονικού ταχυδρομείου

Τώρα, δημιουργήστε ένα μήνυμα email από τη ροή MHTML χρησιμοποιώντας το Aspose.Email. Θα αξιοποιήσετε το`MailMessage` τάξη για το σκοπό αυτό.

```csharp
// Φορτώστε τη ροή MHTML σε ένα μήνυμα ηλεκτρονικού ταχυδρομείου Aspose.Email MIME.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Βήμα 4: Στείλτε το email

 Τέλος, στείλτε το email χρησιμοποιώντας έναν πελάτη SMTP. Διαμορφώστε τον πελάτη SMTP με τα στοιχεία του διακομιστή σας και χρησιμοποιήστε το`Send` μέθοδο αποστολής του μηνύματος.

```csharp
// Διαμορφώστε και στείλτε το μήνυμα χρησιμοποιώντας το Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Σύναψη

Συγχαρητήρια! Μετατρέψατε επιτυχώς ένα έγγραφο DOCX σε MHTML και το στείλατε μέσω email χρησιμοποιώντας το Aspose.Words και το Aspose.Email για .NET. Αυτή η διαδικασία περιλαμβάνει τη φόρτωση του εγγράφου, τη μετατροπή του σε MHTML, τη δημιουργία ενός μηνύματος email και την αποστολή του μέσω ενός προγράμματος-πελάτη SMTP. Με αυτά τα βήματα, μπορείτε να αυτοματοποιήσετε τη μετατροπή και την αποστολή με email των εγγράφων απρόσκοπτα στις εφαρμογές σας.

## Συχνές ερωτήσεις

### Μπορώ να χρησιμοποιήσω αυτήν τη μέθοδο για να μετατρέψω άλλες μορφές εγγράφων;
Απολύτως! Το Aspose.Words υποστηρίζει ένα ευρύ φάσμα μορφών, επιτρέποντάς σας να μετατρέψετε DOC, DOCX, RTF και άλλα σε MHTML.

### Πώς μπορώ να προσθέσω συνημμένα στο email;
 Μπορείτε εύκολα να προσθέσετε συνημμένα χρησιμοποιώντας το`Attachments` ιδιοκτησία του`MailMessage`τάξη.

### Είναι το Aspose.Words συμβατό με .NET Core;
Ναι, το Aspose.Words είναι συμβατό με .NET Core, καθιστώντας το κατάλληλο για χρήση σε εφαρμογές .NET Core.

### Χρειάζομαι άδεια για το Aspose.Words και το Aspose.Email;
 Ναι, και οι δύο βιβλιοθήκες απαιτούν άδεια. Μπορείτε να αποκτήσετε μια προσωρινή άδεια για σκοπούς αξιολόγησης από το[Σελίδα αγοράς Aspose](https://purchase.conholdate.com/temporary-license/).

### Πού μπορώ να βρω περισσότερα έγγραφα;
 Για λεπτομερή τεκμηρίωση, ανατρέξτε στο Aspose.Words[εδώ](https://reference.aspose.com/words/net/) και Aspose.Email[εδώ](https://reference.aspose.com/email/net/).