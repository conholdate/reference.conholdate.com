---
title: Nastavení statusu účastníka pro účastníky schůzky s C#
linktitle: Nastavení statusu účastníka pro účastníky schůzky s C#
second_title: Aspose.Email .NET Email Processing API
description: Naučte se spravovat stav účastníků schůzky pomocí C# a Aspose.Email pro .NET. Průvodce krok za krokem se zdrojovým kódem.
type: docs
weight: 16
url: /cs/net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## Zavedení

Aspose.Email for .NET je robustní a na funkce bohatá knihovna navržená pro zefektivnění práce s e-maily v aplikacích .NET. Tato příručka poskytuje podrobný návod k vytváření a správě schůzek, přidávání účastníků a nastavování statusů účastníků, což zajišťuje efektivní integraci do vašich projektů .NET.

## Předpoklady

Než začnete, ujistěte se, že máte následující:

- Funkční instalace sady Visual Studio nebo kompatibilního vývojového prostředí C#.
- Nejnovější verze knihovny Aspose.Email for .NET.
- Základní znalost C# a objektově orientovaného programování.

 Pro instalaci knihovny viz[stránka ke stažení](https://releases.aspose.com/).

## Importujte požadované jmenné prostory

Chcete-li začít, zahrňte potřebné jmenné prostory pro přístup k funkcím pro správu schůzek a e-mailových komponent.

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## Vytvořte instanci schůzky

Schůzky v Aspose.Email představují plánované události, jako jsou schůzky nebo úkoly. Postup vytvoření:

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- Místo: Určuje, kde se schůzka uskuteční.
- StartTime a EndTime: Definujte dobu trvání schůzky.
- Organizátor a účastníci: Definujte účastníky a jejich role.

## Přidávání účastníků do schůzek

Aspose.Email vám umožňuje programově spravovat účastníky s jejich e-mailovými adresami a stavy účasti.

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## Správa statusů účastníků

 The`ParticipantStatus` vlastnost pomáhá určit, zda účastník přijal, odmítl nebo předběžně přijal pozvání na schůzku. Použijte následující hodnoty výčtu:

- Přijato
- Odmítnuto
- Orientační

Příklad:

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## Odesílání schůzek jako pozvánek na schůzku

Jakmile je schůzka připravena, můžete ji odeslat jako e-mail s pozvánkou:

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## Závěr

Aspose.Email for .NET zjednodušuje správu schůzek v aplikacích .NET a poskytuje nástroje pro efektivní vytváření, přizpůsobení a správu plánovaných událostí. Díky intuitivnímu rozhraní API můžete zefektivnit komunikační pracovní postupy a zajistit bezproblémovou integraci.

## FAQ

### Co je Aspose.Email pro .NET?

Aspose.Email for .NET je komplexní knihovna pro zpracování e-mailových zpráv, schůzek a dalších souvisejících funkcí v aplikacích .NET.

### Mohu přizpůsobit vlastnosti schůzky?

Ano, vlastnosti jako umístění, čas zahájení a účastníci lze plně přizpůsobit.

### Podporuje knihovna opakované schůzky?

Ano, Aspose.Email for .NET podporuje opakované schůzky pomocí svého API vzoru opakování.

### Kde mohu získat podporu pro Aspose.Email pro .NET?

 Můžete získat přístup k podrobné dokumentaci a podpoře komunity na adrese[stránka podpory](https://forum.aspose.com/c/email/11).