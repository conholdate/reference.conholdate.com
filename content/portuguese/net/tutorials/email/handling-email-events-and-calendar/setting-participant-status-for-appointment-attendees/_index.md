---
title: Definindo o status do participante para participantes do compromisso com C#
linktitle: Definindo o status do participante para participantes do compromisso com C#
second_title: API de processamento de e-mail Aspose.Email .NET
description: Aprenda a gerenciar o status dos participantes do compromisso usando C# e Aspose.Email para .NET. Guia passo a passo com código-fonte.
type: docs
weight: 16
url: /pt/net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## Introdução

Aspose.Email for .NET é uma biblioteca robusta e rica em recursos, projetada para simplificar o manuseio de e-mails em aplicativos .NET. Este guia fornece um passo a passo para criar e gerenciar compromissos, adicionar participantes e definir status de participantes, garantindo integração eficiente em seus projetos .NET.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

- Uma instalação funcional do Visual Studio ou um IDE C# compatível.
- A versão mais recente da biblioteca Aspose.Email para .NET.
- Conhecimento básico de C# e programação orientada a objetos.

 Para instalação da biblioteca, consulte o[página de download](https://releases.aspose.com/).

## Importar namespaces necessários

Para começar, inclua os namespaces necessários para acessar as funcionalidades de gerenciamento de compromissos e componentes de e-mail.

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## Criar uma instância de compromisso

Compromissos no Aspose.Email representam eventos agendados, como reuniões ou tarefas. Veja como criar um:

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- Localização: especifica onde o compromisso ocorrerá.
- StartTime e EndTime: definem a duração do compromisso.
- Organizador e participantes: defina os participantes e suas funções.

## Adicionar participantes aos compromissos

O Aspose.Email permite que você gerencie programaticamente os participantes com seus endereços de e-mail e status de participação.

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## Gerenciando status de participantes

 O`ParticipantStatus` property ajuda a determinar se um participante aceitou, recusou ou aceitou provisoriamente um convite para compromisso. Use os seguintes valores de enumeração:

- Aceito
- Recusado
- Tentativa

Exemplo:

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## Enviando compromissos como convites para reuniões

Depois que o compromisso estiver preparado, você pode enviá-lo como um e-mail de convite:

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## Conclusão

O Aspose.Email para .NET simplifica o gerenciamento de compromissos em aplicativos .NET, fornecendo ferramentas para criar, personalizar e gerenciar eventos agendados de forma eficiente. Com sua API intuitiva, você pode simplificar os fluxos de trabalho de comunicação e garantir integração perfeita.

## Perguntas frequentes

### O que é Aspose.Email para .NET?

Aspose.Email para .NET é uma biblioteca abrangente para manipular mensagens de e-mail, compromissos e outras funcionalidades relacionadas em aplicativos .NET.

### Posso personalizar as propriedades do compromisso?

Sim, propriedades como localização, hora de início e participantes podem ser totalmente personalizadas.

### A biblioteca aceita agendamentos recorrentes?

Sim, o Aspose.Email para .NET oferece suporte a compromissos recorrentes usando sua API de padrão de recorrência.

### Onde posso obter suporte para o Aspose.Email para .NET?

 Você pode acessar documentação detalhada e suporte da comunidade em[página de suporte](https://forum.aspose.com/c/email/11).