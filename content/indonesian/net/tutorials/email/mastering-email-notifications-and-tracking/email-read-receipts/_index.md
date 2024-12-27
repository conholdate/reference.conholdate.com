---
title: Tanda Terima Baca Email dengan Aspose.Email untuk .NET
linktitle: Tanda Terima Baca Email dengan Aspose.Email untuk .NET
second_title: API Pemrosesan Email Aspose.Email .NET
description: Pelajari cara meminta tanda terima email yang telah dibaca menggunakan Aspose.Email untuk .NET. Panduan langkah demi langkah bagi pengembang untuk menerapkan pelacakan pembacaan di C#.
type: docs
weight: 11
url: /id/net/tutorials/email/mastering-email-notifications-and-tracking/email-read-receipts/
---
## Perkenalan

Pernahkah Anda mengirim email dan berharap dapat mengetahui kapan penerima membukanya? Masukkan tanda terima email telah dibaca—fitur yang memungkinkan Anda melacak apakah pesan Anda telah dibaca. Dalam tutorial ini, kami akan memandu Anda tentang cara meminta tanda terima email telah dibaca menggunakan Aspose.Email untuk .NET. Jika Anda seorang pengembang, ini adalah kesempatan Anda untuk menyederhanakan komunikasi email hanya dengan beberapa baris kode!

Kami akan menguraikan setiap langkah, mulai dari menyiapkan lingkungan Anda hingga mengirim email dengan pelacakan yang diaktifkan. Di akhir tutorial ini, Anda akan menjadi ahli dalam menerapkan fitur ini!

## Prasyarat

Sebelum menyelami kodenya, pastikan Anda telah menyiapkan hal berikut:

1.  Pustaka Aspose.Email untuk .NET terinstal.[Unduh di sini](https://releases.aspose.com/email/net/).
2. Server SMTP yang valid dengan kredensial (host, nama pengguna, kata sandi).
3. Visual Studio atau IDE apa pun yang kompatibel.
4. .NET Framework terpasang.
5.  A[lisensi sementara](https://purchase.aspose.com/temporary-license/) jika Anda menggunakan versi uji coba.

## Paket Impor

Untuk memulai, Anda perlu menyertakan namespace yang diperlukan dalam proyek Anda. Namespace ini menyediakan kelas dan metode yang diperlukan untuk mengirim email dan meminta tanda terima baca.

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Smtp;
using Aspose.Email.Mime;
```

## Langkah 1: Buat Pesan Email

 Langkah pertama adalah membuat instance dari`MailMessage` kelas, yang mewakili email yang ingin Anda kirim.

```csharp
MailMessage message = new MailMessage();
```

 Itu`MailMessage` objek adalah kanvas kosong tempat Anda akan mengatur properti seperti pengirim, penerima, subjek, isi, dan tajuk. Anggap saja seperti sedang menyusun email di klien favorit Anda.

## Langkah 2: Tetapkan Rincian Pengirim dan Penerima

Tentukan alamat email pengirim, alamat email penerima, dan properti utama lainnya seperti subjek dan isi.

```csharp
message.From = "sender@sender.com";
message.To.Add("receiver@receiver.com");
message.Subject = "Requesting Read Receipt";
message.HtmlBody = "<html><body>This is the HTML body</body></html>";
```

Di sini, kami menetapkan alamat email pengirim dan penerima. Kami juga menentukan subjek dan isi email, menggunakan HTML agar terlihat lebih menarik.

## Langkah 3: Aktifkan Pengiriman dan Tanda Terima Baca

Tambahkan header untuk meminta pengiriman dan tanda terima baca. Header ini memberi tahu server email penerima untuk memberi tahu Anda saat email terkirim atau dibuka.

```csharp
message.DeliveryNotificationOptions = DeliveryNotificationOptions.OnSuccess;
message.Headers.Add("Return-Receipt-To", "sender@sender.com");
message.Headers.Add("Disposition-Notification-To", "sender@sender.com");
```

- DeliveryNotificationOptions: Meminta konfirmasi saat email berhasil terkirim.
- Return-Receipt-To: Meminta tanda terima saat email dibaca.
- Disposition-Notification-To: Header spesifik yang digunakan untuk tanda terima telah dibaca.

## Langkah 4: Konfigurasikan Klien SMTP

 Buat contoh dari`SmtpClient` kelas dan konfigurasikan dengan detail server SMTP Anda.

```csharp
SmtpClient client = new SmtpClient
{
    Host = "smtp.server.com",
    Username = "Username",
    Password = "Password",
    Port = 25
};
```

 Itu`SmtpClient` menangani pengiriman email Anda. Ganti`"smtp.server.com"`, `"Username"` , Dan`"Password"` dengan rincian server SMTP Anda.

## Langkah 5: Kirim Email

 Gunakan`Send` metode dari`SmtpClient` untuk mengirim email Anda. Tangani pengecualian untuk memastikan eksekusi yang lancar.

```csharp
try
{
    client.Send(message);
    Console.WriteLine("Message sent");
}
catch (Exception ex)
{
    System.Diagnostics.Trace.WriteLine(ex.ToString());
}
```

- client.Send(pesan): Mengirim email yang telah disiapkan.
- Penanganan Pengecualian: Mencatat masalah apa pun, seperti rincian server yang salah atau masalah konektivitas.

## Kesimpulan

Selesai! Anda telah berhasil menerapkan sistem untuk meminta tanda terima email telah dibaca menggunakan Aspose.Email untuk .NET. Fitur ini mengubah permainan untuk memastikan email penting mendapatkan perhatian yang layak. Baik Anda mengirim email transaksional atau pembaruan bisnis penting, pelacakan tanda terima email telah dibaca memberikan lapisan akuntabilitas tambahan.

## Pertanyaan yang Sering Diajukan

### Apa itu tanda terima telah dibaca dalam email?
Laporan telah dibaca adalah pemberitahuan yang Anda terima saat penerima membuka email Anda. Pemberitahuan ini memberikan konfirmasi bahwa pesan Anda telah dibaca.

### Bisakah saya meminta tanda terima telah dibaca untuk semua email?
Tidak semua klien email mendukung tanda terima telah dibaca, dan penerima dapat memilih untuk menolak mengirimkannya.

### Apakah Aspose.Email untuk .NET gratis?
 Anda dapat menggunakan[versi uji coba gratis](https://releases.aspose.com/) atau membeli lisensi dari[Situs web Aspose](https://purchase.aspose.com/buy).

### Seberapa amankah Aspose.Email untuk mengirim email?
Aspose.Email menyediakan fitur keamanan yang tangguh, termasuk enkripsi SSL/TLS untuk komunikasi email yang aman.

### Bisakah saya menyesuaikan header email lebih lanjut?
Ya, Aspose.Email memungkinkan Anda menambahkan header khusus untuk persyaratan tertentu. Lihat[dokumentasi](https://reference.aspose.com/email/net/) untuk rinciannya.