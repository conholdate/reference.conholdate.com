---
title: Menetapkan Status Peserta untuk Peserta Janji Temu dengan C#
linktitle: Menetapkan Status Peserta untuk Peserta Janji Temu dengan C#
second_title: API Pemrosesan Email Aspose.Email .NET
description: Pelajari cara mengelola status peserta janji temu menggunakan C# dan Aspose.Email untuk .NET. Panduan langkah demi langkah dengan kode sumber.
type: docs
weight: 16
url: /id/net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## Perkenalan

Aspose.Email untuk .NET adalah pustaka yang tangguh dan kaya fitur yang dirancang untuk menyederhanakan penanganan email dalam aplikasi .NET. Panduan ini menyediakan panduan langkah demi langkah untuk membuat dan mengelola janji temu, menambahkan peserta, dan menetapkan status peserta, guna memastikan integrasi yang efisien ke dalam proyek .NET Anda.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

- Instalasi Visual Studio yang berfungsi atau IDE C# yang kompatibel.
- Versi terbaru pustaka Aspose.Email untuk .NET.
- Pengetahuan dasar tentang C# dan pemrograman berorientasi objek.

 Untuk instalasi perpustakaan, lihat[halaman unduhan](https://releases.aspose.com/).

## Mengimpor Ruang Nama yang Diperlukan

Untuk memulai, sertakan namespace yang diperlukan untuk mengakses fungsionalitas dalam mengelola janji temu dan komponen email.

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## Buat Contoh Janji Temu

Janji temu di Aspose.Email merupakan acara terjadwal seperti rapat atau tugas. Berikut cara membuatnya:

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- Lokasi: Menentukan di mana janji temu akan berlangsung.
- StartTime dan EndTime: Tentukan durasi janji temu.
- Penyelenggara dan Peserta: Tentukan peserta dan peran mereka.

## Menambahkan Peserta ke Janji Temu

Aspose.Email memungkinkan Anda mengelola peserta secara terprogram dengan alamat email dan status partisipasi mereka.

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## Mengelola Status Peserta

 Itu`ParticipantStatus` properti membantu menentukan apakah peserta telah menerima, menolak, atau menerima sementara undangan janji temu. Gunakan nilai enumerasi berikut:

- Diterima
- Ditolak
- Bisa berubah

Contoh:

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## Mengirim Janji Temu sebagai Undangan Rapat

Setelah janji temu disiapkan, Anda dapat mengirimkannya sebagai email undangan:

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## Kesimpulan

Aspose.Email untuk .NET menyederhanakan manajemen janji temu dalam aplikasi .NET, menyediakan alat untuk membuat, menyesuaikan, dan mengelola acara terjadwal secara efisien. Dengan API intuitifnya, Anda dapat menyederhanakan alur kerja komunikasi dan memastikan integrasi yang lancar.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Email untuk .NET?

Aspose.Email untuk .NET adalah pustaka komprehensif untuk menangani pesan email, janji temu, dan fungsi terkait lainnya dalam aplikasi .NET.

### Bisakah saya menyesuaikan properti janji temu?

Ya, properti seperti lokasi, waktu mulai, dan peserta dapat disesuaikan sepenuhnya.

### Apakah perpustakaan mendukung janji temu berulang?

Ya, Aspose.Email untuk .NET mendukung janji temu berulang menggunakan API pola pengulangannya.

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Email untuk .NET?

 Anda dapat mengakses dokumentasi terperinci dan dukungan komunitas di[halaman dukungan](https://forum.aspose.com/c/email/11).