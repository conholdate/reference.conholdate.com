---
title: Konversi DOCX ke MHTML dan Kirim Email Menggunakan Aspose.Words untuk .NET
linktitle: Konversi DOCX ke MHTML dan Kirim Email Menggunakan Aspose.Words untuk .NET
second_title: API Pemrosesan Dokumen Aspose.Words
description: Panduan komprehensif ini menyediakan tutorial langkah demi langkah tentang mengonversi dokumen DOCX ke format MHTML dan mengirimkannya melalui email menggunakan pustaka Aspose.Words dan Aspose.Email di .NET.
type: docs
weight: 10
url: /id/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Perkenalan

Dalam lanskap digital saat ini, mengonversi dokumen antarformat dan mengirimkannya melalui email merupakan tugas yang umum. Panduan ini akan memandu Anda mengonversi file DOCX ke format MHTML dan mengirimkannya melalui email menggunakan pustaka Aspose.Words dan Aspose.Email yang canggih untuk .NET. Kami akan menguraikan setiap langkah dengan jelas, memastikan Anda dapat mengikutinya dengan mudah. Mari kita mulai!

## Prasyarat

Sebelum memulai prosesnya, pastikan Anda telah menyiapkan hal berikut:

1.  Aspose.Words untuk .NET: Unduh dan instal pustaka dari[Aspose merilis halaman](https://releases.aspose.com/words/net/).
2.  Aspose.Email untuk .NET: Unduh dan instal pustaka ini dari[Aspose merilis halaman](https://releases.aspose.com/email/net/).
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda.
4. Server SMTP: Anda memerlukan akses ke server SMTP untuk mengirim email.

## Mengimpor Ruang Nama yang Diperlukan

Untuk memanfaatkan Aspose.Words dan Aspose.Email dalam proyek Anda, Anda harus mengimpor namespace yang diperlukan. Tambahkan perintah berikut di bagian atas berkas C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Langkah 1: Muat Dokumen DOCX

 Mulailah dengan memuat dokumen DOCX yang ingin Anda konversi. Gunakan`Document` kelas dari Aspose.Words untuk menyelesaikan hal ini.

```csharp
// Tentukan jalur ke direktori dokumen Anda.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Langkah 2: Simpan Dokumen sebagai MHTML

 Selanjutnya, ubah dokumen yang dimuat ke dalam format MHTML. Ini dilakukan dengan menggunakan`Save` metode dari`Document` kelas.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Atur ulang posisi aliran ke awal untuk pembacaan.
    stream.Position = 0;
}
```

## Langkah 3: Buat Pesan Email

Sekarang, buat pesan email dari aliran MHTML menggunakan Aspose.Email. Anda akan menggunakan`MailMessage` kelas untuk tujuan ini.

```csharp
// Muat aliran MHTML ke dalam pesan email Aspose.Email MIME.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Langkah 4: Kirim Email

 Terakhir, kirim email menggunakan klien SMTP. Konfigurasikan klien SMTP dengan detail server Anda dan gunakan`Send` metode untuk mengirimkan pesan.

```csharp
// Konfigurasikan dan kirim pesan menggunakan Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Kesimpulan

Selamat! Anda telah berhasil mengonversi dokumen DOCX ke MHTML dan mengirimkannya melalui email menggunakan Aspose.Words dan Aspose.Email untuk .NET. Proses ini melibatkan pemuatan dokumen, mengonversinya ke MHTML, membuat pesan email, dan mengirimkannya melalui klien SMTP. Dengan langkah-langkah ini, Anda dapat mengotomatiskan konversi dan pengiriman dokumen melalui email dengan lancar di aplikasi Anda.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan metode ini untuk mengonversi format dokumen lain?
Tentu saja! Aspose.Words mendukung berbagai macam format, yang memungkinkan Anda mengonversi DOC, DOCX, RTF, dan lainnya ke MHTML.

### Bagaimana cara menambahkan lampiran ke email?
 Anda dapat dengan mudah menambahkan lampiran menggunakan`Attachments` milik`MailMessage` kelas.

### Apakah Aspose.Words kompatibel dengan .NET Core?
Ya, Aspose.Words kompatibel dengan .NET Core, membuatnya cocok untuk digunakan dalam aplikasi .NET Core.

### Apakah saya memerlukan lisensi untuk Aspose.Words dan Aspose.Email?
 Ya, kedua perpustakaan memerlukan lisensi. Anda dapat memperoleh lisensi sementara untuk tujuan evaluasi dari[Halaman pembelian Aspose](https://purchase.conholdate.com/temporary-license/).

### Di mana saya dapat menemukan dokumentasi lebih lanjut?
 Untuk dokumentasi terperinci, lihat Aspose.Words[Di Sini](https://reference.aspose.com/words/net/) dan Aspose.Email[Di Sini](https://reference.aspose.com/email/net/).