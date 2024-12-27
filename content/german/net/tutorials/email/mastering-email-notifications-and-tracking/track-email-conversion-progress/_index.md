---
title: Verfolgen Sie den Fortschritt der E-Mail-Konvertierung mit Aspose.Email für .NET
linktitle: Verfolgen Sie den Fortschritt der E-Mail-Konvertierung mit Aspose.Email für .NET
second_title: Aspose.Email .NET E-Mail-Verarbeitungs-API
description: Erfahren Sie Schritt für Schritt, wie Sie den Fortschritt der E-Mail-Konvertierung in C# mit Aspose.Email für .NET verfolgen. Steigern Sie die Effizienz Ihres Projekts mit diesem ausführlichen Tutorial.
type: docs
weight: 12
url: /de/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## Einführung

Um E-Mail-Dokumente effizient zu verwalten, muss häufig der Fortschritt ihrer Konvertierung verfolgt werden. Aspose.Email für .NET bietet hierfür robuste Tools, mit denen Entwickler E-Mail-Vorgänge nahtlos abwickeln können. In diesem Tutorial erfahren Sie, wie Sie den Fortschritt der Konvertierung von E-Mail-Dokumenten in C# verfolgen können. Der Prozess wird zur leichteren Verständlichkeit Schritt für Schritt aufgeschlüsselt.  

## Voraussetzungen  

Bevor wir mit dem Tutorial beginnen, stellen wir sicher, dass Sie alles eingerichtet haben:  

1.  Aspose.Email für .NET: Laden Sie herunter und installieren Sie die[Aspose.Email für .NET](https://releases.aspose.com/email/net/) Bibliothek.  
2. Entwicklungsumgebung: Installieren Sie Visual Studio oder eine andere .NET-kompatible IDE.  
3. .NET Framework: Stellen Sie sicher, dass .NET Framework 4.5 oder höher installiert ist.  
4.  Temporäre Lizenz: Erwägen Sie den Erwerb einer[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) um alle Funktionen von Aspose.Email zu erkunden.  
5.  Beispiel einer E-Mail-Datei: Bereiten Sie eine`.eml` Datei (z. B.`test.eml`) als Beispiel verwenden.  

## Pakete importieren  

Um Aspose.Email in Ihrem Projekt zu verwenden, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie oben in Ihrer Datei die folgenden using-Anweisungen hinzu:  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## Schritt 1: Richten Sie Ihr Projekt ein  

Beginnen Sie mit der Erstellung einer neuen C#-Konsolenanwendung in Visual Studio. Diese dient als Grundlage für die Implementierung der Konvertierungsverfolgung für E-Mail-Dokumente.  
  
1. Öffnen Sie Visual Studio und erstellen Sie ein neues Konsolenanwendungsprojekt.  
2. Installieren Sie das Aspose.Email NuGet-Paket:  
```sh
Install-Package Aspose.Email
```  
3.  Fügen Sie den`.eml` Datei in Ihr Projektverzeichnis.  

## Schritt 2: Laden Sie die E-Mail-Datei  

 Laden Sie nun die E-Mail-Datei in ein`MailMessage` Objekt. Dies ist der erste Schritt beim Arbeiten mit E-Mail-Daten.  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`: Gibt das Verzeichnis an, in dem sich Ihre E-Mail-Datei befindet.  
- `MailMessage.Load` : Liest die`.eml` Datei und bereitet sie für weitere Operationen vor.  

## Schritt 3: Initialisieren eines Speicherstreams  

 Erstellen Sie als Nächstes eine`MemoryStream` Widerspruch gegen die vorübergehende Speicherung der konvertierten E-Mail-Daten.  
 
```csharp
MemoryStream ms = new MemoryStream();
```

 A`MemoryStream` wird hier verwendet, um die Ausgabe des Konvertierungsprozesses zu verwalten, ohne die Daten direkt auf der Festplatte zu speichern.  

## Schritt 4: Konvertierungsoptionen definieren  

 Richten Sie die`EmlSaveOptions` mit einem benutzerdefinierten Fortschrittshandler, um den Konvertierungsfortschritt zu verfolgen.  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`: Gibt das Ausgabeformat an.  
- `CustomProgressHandler`: Weist eine benutzerdefinierte Handlerfunktion zur Überwachung des Fortschritts zu.  

## Schritt 5: Speichern Sie die E-Mail im Memory Stream  

Speichern Sie die`MailMessage` Objekt mit den angegebenen Optionen, wodurch die Funktion zur Fortschrittsverfolgung aktiviert wird.  
 
```csharp
msg.Save(ms, opt);
```
 
Dieser Schritt leitet den E-Mail-Konvertierungsprozess ein und sendet Updates an den Fortschrittshandler.  

## Schritt 6: Implementieren des Fortschrittshandlers  

 Definieren Sie die`ShowEmlConversionProgress` Methode, um Fortschrittsaktualisierungen zu verarbeiten und sie in der Konsole anzuzeigen.  
 
```csharp
private static void ShowEmlConversionProgress(ProgressEventHandlerInfo info)
{
    int total;
    int saved;

    switch (info.EventType)
    {
        case ProgressEventType.MimeStructureCreated:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimeStructureCreated - TotalMimePartCount: {total}");
            Console.WriteLine($"MimeStructureCreated - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.MimePartSaved:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimePartSaved - TotalMimePartCount: {total}");
            Console.WriteLine($"MimePartSaved - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.SavedToStream:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"SavedToStream - TotalMimePartCount: {total}");
            Console.WriteLine($"SavedToStream - SavedMimePartCount: {saved}");
            break;
    }
}
```
 
- `ProgressEventHandlerInfo`: Bietet Details zum Konvertierungsprozess.  
-  Switch Cases: Behandeln Sie verschiedene Phasen der Konvertierung:`MimeStructureCreated`, `MimePartSaved` , Und`SavedToStream`.  

### Was ist zu erwarten?  
Während die Konvertierung fortschreitet, werden auf der Konsole detaillierte Aktualisierungen angezeigt, beispielsweise:  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## Abschluss  

Dank Aspose.Email für .NET war es nie einfacher, den Konvertierungsfortschritt von E-Mail-Dokumenten in C# zu verfolgen. In diesem Tutorial haben Sie gelernt, wie Sie eine E-Mail-Datei laden, einen Fortschrittshandler einrichten und die E-Mail-Daten speichern, während Sie den gesamten Prozess überwachen. Diese Funktion stellt sicher, dass Sie während der E-Mail-Dokumentvorgänge informiert bleiben und die Kontrolle behalten.  

## Häufig gestellte Fragen  

###  Kann ich diesen Code für andere Formate verwenden als`.eml`?  
 Ja, ändern Sie die`MailMessageSaveType`um sie an andere Formate wie MSG oder MHTML anzupassen.  

### Wie gehe ich mit großen E-Mail-Dateien um?  
 Erwägen Sie die Verwendung eines`FileStream` anstelle eines`MemoryStream` für eine bessere Leistung bei großen Dateien.  

### Was ist eine vorläufige Lizenz und wie bekomme ich eine?  
 Mit einer temporären Lizenz können Sie den vollen Funktionsumfang der Bibliothek kostenlos testen. Hol es dir[Hier](https://purchase.aspose.com/temporary-license/).  

### Kann ich diesen Code in eine Webanwendung integrieren?  
Ja, der Code ist mit Webanwendungen kompatibel, die ASP.NET oder ähnliche Frameworks verwenden.  

### Wo finde ich zusätzliche Ressourcen?  
 Schauen Sie sich die[Dokumentation](https://reference.aspose.com/email/net/) oder besuchen Sie die[Support-Forum](https://forum.aspose.com/c/email/12/) um Hilfe.  