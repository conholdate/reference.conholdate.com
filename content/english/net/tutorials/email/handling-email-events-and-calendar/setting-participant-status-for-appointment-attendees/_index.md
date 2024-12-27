---
title: Setting Participant Status for Appointment Attendees with C#
linktitle: Setting Participant Status for Appointment Attendees with C#
second_title: Aspose.Email .NET Email Processing API
description: Learn how to manage appointment attendees' status using C# and Aspose.Email for .NET. Step-by-step guide with source code.
type: docs
weight: 16
url: /net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## Introduction

Aspose.Email for .NET is a robust and feature-rich library designed to streamline email handling in .NET applications. This guide provides a step-by-step walkthrough of creating and managing appointments, adding attendees, and setting participant statuses, ensuring efficient integration into your .NET projects.

## Prerequisites

Before you begin, ensure you have the following:

- A working installation of Visual Studio or a compatible C# IDE.
- The latest version of the Aspose.Email for .NET library.
- Basic knowledge of C# and object-oriented programming.

For library installation, refer to the [download page](https://releases.aspose.com/).

## Import Required Namespaces

To get started, include the necessary namespaces to access the functionalities for managing appointments and email components.

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## Create an Appointment Instance

Appointments in Aspose.Email represent scheduled events such as meetings or tasks. Here's how you create one:

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- Location: Specifies where the appointment will occur.
- StartTime and EndTime: Define the appointment's duration.
- Organizer and Attendees: Define participants and their roles.

## Adding Attendees to Appointments

Aspose.Email allows you to programmatically manage attendees with their email addresses and participation statuses.

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## Managing Participant Statuses

The `ParticipantStatus` property helps determine whether an attendee has accepted, declined, or tentatively accepted an appointment invitation. Use the following enumeration values:

- Accepted
- Declined
- Tentative

Example:

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## Sending Appointments as Meeting Invitations

Once the appointment is prepared, you can send it as an invitation email:

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## Conclusion

Aspose.Email for .NET simplifies appointment management in .NET applications, providing tools for creating, customizing, and managing scheduled events efficiently. With its intuitive API, you can streamline communication workflows and ensure seamless integration.

## FAQ's

### What is Aspose.Email for .NET?

Aspose.Email for .NET is a comprehensive library for handling email messages, appointments, and other related functionalities in .NET applications.

### Can I customize appointment properties?

Yes, properties such as location, start time, and participants can be fully customized.

### Does the library support recurring appointments?

Yes, Aspose.Email for .NET supports recurring appointments using its recurrence pattern API.

### Where can I get support for Aspose.Email for .NET?

You can access detailed documentation and community support at the [support page](https://forum.aspose.com/c/email/11).
