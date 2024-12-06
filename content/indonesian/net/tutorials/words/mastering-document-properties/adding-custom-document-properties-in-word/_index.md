---
title: Menambahkan Properti Dokumen Kustom di Word
linktitle: Menambahkan Properti Dokumen Kustom di Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyempurnakan dokumen Word Anda dengan properti dokumen kustom menggunakan Aspose.Words untuk .NET. Panduan lengkap ini akan memandu Anda melalui prosesnya.
type: docs
weight: 10
url: /id/net/tutorials/words/mastering-document-properties/adding-custom-document-properties-in-word/
---
## Perkenalan

Selamat datang! Jika Anda menjelajahi Aspose.Words untuk .NET dan ingin mempelajari cara menambahkan properti dokumen kustom ke file Word Anda, Anda berada di tempat yang tepat. Properti kustom sangat berharga untuk menyimpan metadata tambahan yang tidak tercakup oleh properti bawaan. Apakah Anda perlu melacak otorisasi dokumen, nomor revisi, atau tanggal tertentu, properti kustom dapat membantu. Dalam tutorial ini, kami akan memandu Anda melalui langkah-langkah untuk menambahkan properti ini dengan mudah menggunakan Aspose.Words untuk .NET. Mari kita mulai!

## Prasyarat

Sebelum menyelami kode, pastikan Anda memiliki hal berikut:

1.  Pustaka Aspose.Words untuk .NET: Unduh[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: IDE seperti Visual Studio.
3. Pengetahuan Dasar C#: Keakraban dengan C# dan .NET akan sangat membantu.
4.  Contoh Dokumen: Siapkan contoh dokumen Word bernama`Properties.docx` untuk modifikasi.

## Mengimpor Ruang Nama

Untuk mengakses fungsionalitas Aspose.Words, Anda perlu mengimpor namespace yang diperlukan di awal kode Anda:

```csharp
using System;
using Aspose.Words;
```

## Langkah 1: Menyiapkan Jalur Dokumen

 Selanjutnya, mari kita tentukan jalur ke dokumen Word Anda. Langkah ini penting untuk menemukan dan membuka`Properties.docx` mengajukan.

```csharp
// Tentukan jalur ke direktori dokumen Anda.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

 Pastikan untuk mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke dokumen Anda.

## Langkah 2: Mengakses Properti Dokumen Kustom

Sekarang, mari mengakses properti dokumen kustom dari dokumen Word, tempat metadata kustom Anda akan berada.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

Baris ini memberi Anda akses ke koleksi properti khusus yang akan Anda kerjakan.

## Langkah 3: Memeriksa Properti yang Ada

Sebelum menambahkan properti baru, sebaiknya periksa apakah properti tersebut sudah ada untuk menghindari duplikasi.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

Kode ini memeriksa apakah properti "Authorized" sudah ada. Jika ada, metode akan keluar lebih awal, mencegah duplikasi.

## Langkah 4: Menambahkan Properti Boolean

Mari tambahkan properti boolean khusus untuk menunjukkan apakah dokumen tersebut sah.

```csharp
customDocumentProperties.Add("Authorized", true);
```

 Baris ini menambahkan properti bernama "Diotorisasi" dan menetapkan nilainya menjadi`true`.

## Langkah 5: Menambahkan Properti String

Berikutnya, kami akan menentukan siapa yang mengesahkan dokumen tersebut dengan menambahkan properti string.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

Jangan ragu untuk mengganti "John Smith" dengan nama apa pun yang Anda inginkan.

## Langkah 6: Menambahkan Properti Tanggal

Untuk melacak kapan dokumen tersebut diotorisasi, mari tambahkan properti tanggal.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

 Baris ini menambahkan properti yang disebut "Tanggal Resmi" dan menetapkan tanggal hari ini menggunakan`DateTime.Today`.

## Langkah 7: Menambahkan Nomor Revisi

Untuk kontrol versi, kita dapat menambahkan properti untuk melacak nomor revisi dokumen.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

Di sini, kami menambahkan properti "Revisi Resmi" yang menyimpan nomor revisi dokumen saat ini.

## Langkah 8: Menambahkan Properti Numerik

Terakhir, mari tambahkan properti numerik untuk menyimpan jumlah yang sah, seperti angka anggaran.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

 Baris ini menambahkan properti bernama "Jumlah Resmi" dengan nilai`123.45`Anda dapat menyesuaikan angka ini sesuai kebutuhan.

## Kesimpulan

Selamat! Anda telah berhasil menambahkan properti dokumen kustom ke dokumen Word menggunakan Aspose.Words for .NET. Properti ini merupakan cara yang ampuh untuk menyimpan metadata yang disesuaikan dengan kebutuhan Anda, baik untuk melacak detail otorisasi, nomor revisi, atau jumlah tertentu.

## Pertanyaan yang Sering Diajukan

### Apa itu properti dokumen kustom?
Properti dokumen kustom adalah metadata yang dapat Anda tambahkan ke dokumen Word untuk menyimpan informasi tambahan yang tidak tercakup oleh properti bawaan.

### Bisakah saya menambahkan properti selain string dan angka?
Ya, Anda dapat menambahkan berbagai jenis properti, termasuk nilai boolean, tanggal, dan bahkan objek kustom.

### Bagaimana cara mengakses properti ini dalam dokumen Word?
Anda dapat mengakses properti kustom secara terprogram menggunakan Aspose.Words atau melihatnya langsung di Word melalui properti dokumen.

### Apakah mungkin untuk mengedit atau menghapus properti khusus?
Tentu saja! Anda dapat dengan mudah mengedit atau menghapus properti kustom menggunakan metode yang disediakan oleh Aspose.Words.

### Bisakah properti khusus digunakan untuk memfilter dokumen?
Ya! Properti kustom sangat bagus untuk mengkategorikan dan memfilter dokumen berdasarkan metadata tertentu.