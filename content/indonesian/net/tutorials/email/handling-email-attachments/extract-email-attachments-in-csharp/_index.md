---
title: Mengekstrak Lampiran Email di C# - Tutorial Aspose.Email
linktitle: Mengekstrak Lampiran Email di C# - Tutorial Aspose.Email
second_title: API Pemrosesan Email Aspose.Email .NET
description: Pelajari cara mengekstrak lampiran email dalam C# menggunakan Aspose.Email untuk .NET. Panduan langkah demi langkah dengan contoh untuk PDF, gambar, dan banyak lagi.
type: docs
weight: 14
url: /id/net/tutorials/email/handling-email-attachments/extract-email-attachments-in-csharp/
---
## Perkenalan

Pernahkah Anda mengunduh lampiran email secara manual, satu per satu? Hal ini tidak hanya memakan waktu tetapi juga rentan terhadap kesalahan. Untungnya, Aspose.Email for .NET menawarkan cara yang ampuh dan efisien untuk mengotomatiskan tugas ini. Baik Anda menangani PDF, gambar, atau jenis file lainnya, Anda dapat mengekstrak lampiran dengan mudah menggunakan C#.

Dalam panduan ini, kami akan memandu Anda melalui tutorial lengkap, mulai dari prasyarat hingga contoh yang berfungsi penuh. Siap menghemat waktu kerja manual selama berjam-jam? Mari kita mulai!

## Prasyarat

Sebelum Anda memulai pengkodean, pastikan Anda memiliki hal berikut:

- Visual Studio terinstal di komputer Anda.
-  Aspose.Email untuk pustaka .NET. Anda dapat[unduh disini](https://releases.aspose.com/email/net/) atau menginstalnya melalui NuGet.
- Akun email yang valid (mendukung IMAP/POP3).
- Pemahaman dasar tentang pemrograman C#.

 Jika Anda baru mengenal Aspose.Email, pertimbangkan untuk meminta[uji coba gratis](https://releases.aspose.com/) atau sebuah[lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk membuka fitur lengkap.

## Paket Impor

Sebelum mulai mengetik kode, pastikan Anda telah mengimpor namespace yang diperlukan. Tambahkan yang berikut di bagian atas file C# Anda:

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Imap;
using Aspose.Email.Clients.Pop3;
```

Mari kita bagi proses ini menjadi beberapa langkah yang mudah dipahami. Ikuti setiap langkah dengan saksama untuk memastikan eksekusi yang lancar.


## Langkah 1: Siapkan Klien IMAP Anda

Langkah pertama adalah menghubungkan ke server email Anda menggunakan protokol IMAP. IMAP memungkinkan kita untuk mengakses dan mengambil pesan email dari server.

```csharp
ImapClient client = new ImapClient("imap.example.com", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
```

-  Mengganti`imap.example.com` dengan alamat server IMAP penyedia email Anda (misalnya,`imap.gmail.com` untuk Gmail).
-  Gunakan email Anda yang sebenarnya`username` Dan`password`.
- `SelectFolder(ImapFolderInfo.InBox)`menentukan bahwa kita ingin bekerja dengan kotak masuk.


## Langkah 2: Ambil Email dari Kotak Masuk

Setelah terhubung, Anda perlu mengambil pesan email dari kotak masuk. Aspose.Email menyediakan metode sederhana untuk mencantumkan semua pesan.

```csharp
ImapMessageInfoCollection messages = client.ListMessages();
```

- `ListMessages()` mengambil metadata untuk semua email di kotak masuk.
-  Itu`ImapMessageInfoCollection` Objek berisi rincian seperti pengirim, subjek, dan ID unik.


## Langkah 3: Ambil Setiap Pesan Email

Untuk mengakses konten dan lampiran, Anda perlu mengambil setiap email menggunakan ID uniknya.


```csharp
foreach (ImapMessageInfo messageInfo in messages)
{
    MailMessage message = client.FetchMessage(messageInfo.UniqueId);
}
```

-  Itu`foreach` loop mengulangi semua pesan.
- `FetchMessage()` mengambil konten email sebenarnya untuk ID pesan tertentu.


## Langkah 4: Ulangi Lampiran

 Sekarang setelah Anda memiliki konten email, saatnya mengekstrak lampiran. Setiap`MailMessage` objek berisi kumpulan lampiran.

```csharp
foreach (Attachment attachment in message.Attachments)
{
    Console.WriteLine($"Attachment Name: {attachment.Name}");
}
```

-  Itu`Attachments` properti mencantumkan semua lampiran dalam email.
-  Menggunakan`attachment.Name` untuk mendapatkan nama berkas.


## Langkah 5: Simpan Lampiran ke Disk

Terakhir, simpan lampiran ke komputer lokal Anda. Anda dapat memfilter berkas berdasarkan jenis, ukuran, atau kriteria lainnya.

```csharp
foreach (Attachment attachment in message.Attachments)
{
    string filePath = Path.Combine("C:\\Attachments", attachment.Name);
    using (var stream = new FileStream(filePath, FileMode.Create))
    {
        attachment.Save(stream);
    }
}
```

-  Mengganti`"C:\\Attachments"`dengan jalur folder yang Anda inginkan.
-  Itu`attachment.Save()` metode menulis berkas ke disk.


## Langkah 6: Memproses Lampiran berdasarkan Jenis

Jika Anda perlu menangani lampiran secara berbeda berdasarkan jenisnya (misalnya, PDF vs. JPEG), Aspose.Email mempermudahnya.

```csharp
if (attachment.ContentType.MediaType == "application/pdf")
{
    Console.WriteLine("Processing PDF...");
}
else if (attachment.ContentType.MediaType == "image/jpeg")
{
    Console.WriteLine("Processing JPEG...");
}
```

- `ContentType.MediaType` mengidentifikasi tipe file (misalnya,`application/pdf` untuk PDF,`image/jpeg` untuk gambar).
- Tambahkan logika khusus untuk berbagai jenis file sesuai kebutuhan.


## Kesimpulan

Nah, itu dia! Mengekstrak lampiran dari email bukan lagi tugas yang membosankan. Dengan Aspose.Email untuk .NET, Anda dapat mengotomatiskan proses ini hanya dalam beberapa baris kode. Dari menyiapkan klien IMAP hingga menyimpan lampiran secara lokal, panduan ini telah mencakup semua yang Anda butuhkan untuk memulai. 

 Jadi, mengapa menunggu?[Unduh Aspose.Email](https://releases.aspose.com/email/net/) dan mulailah menyederhanakan alur kerja email Anda hari ini!


## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan kode ini dengan Gmail atau Outlook?
 Ya! Ganti`imap.example.com` dengan Gmail (`imap.gmail.com`) atau Outlook (`outlook.office365.com`) Alamat server IMAP.

### Apakah Aspose.Email gratis untuk digunakan?
 Aspose.Email memerlukan lisensi untuk fitur lengkap. Anda dapat meminta lisensi[uji coba gratis](https://releases.aspose.com/) atau sebuah[lisensi sementara](https://purchase.aspose.com/temporary-license/).

### Bagaimana saya dapat menangani keamanan kata sandi?
Pertimbangkan untuk menggunakan variabel lingkungan atau penyimpanan kredensial yang aman alih-alih menggunakan kata sandi hardcoding.

### Bisakah saya mengekstrak lampiran dari item yang terkirim?
 Ya, cukup gunakan saja`SelectFolder(ImapFolderInfo.Sent)` alih-alih kotak masuk.

### Apakah Aspose.Email mendukung POP3?
Tentu saja! Selain IMAP, ia juga mendukung POP3 dan SMTP.