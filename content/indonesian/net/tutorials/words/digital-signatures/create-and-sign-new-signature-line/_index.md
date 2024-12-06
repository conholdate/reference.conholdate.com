---
title: Buat dan Tandatangani Baris Tanda Tangan Baru
linktitle: Buat dan Tandatangani Baris Tanda Tangan Baru
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menambahkan tanda tangan digital ke dokumen Word Anda dengan mudah menggunakan Aspose.Words untuk .NET. Tutorial komprehensif ini mencakup semuanya mulai dari menyiapkan lingkungan Anda dan memasukkan baris tanda tangan hingga menyimpan dan memverifikasi dokumen yang telah Anda tandatangani.
type: docs
weight: 10
url: /id/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## Perkenalan

Ingin menambahkan tanda tangan digital ke dokumen Word? Dengan Aspose.Words untuk .NET, semuanya lebih mudah dari yang Anda kira! Tutorial ini akan memandu Anda melalui langkah-langkah menyiapkan lingkungan, menambahkan baris tanda tangan, dan menandatangani dokumen secara digital. Mari kita mulai!

## Prasyarat

Sebelum menyelami kode, pastikan Anda memiliki hal berikut:

1.  Aspose.Words untuk .NET -[Unduh di sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan .NET - Visual Studio ideal untuk tugas ini.
3. Dokumen untuk Ditandatangani - Anda dapat membuat dokumen Word baru atau menggunakan dokumen Word yang sudah ada.
4.  File Sertifikat - A`.pfx` file diperlukan untuk tanda tangan digital.
5. Gambar Baris Tanda Tangan (Opsional) - Anda dapat menyertakan berkas gambar untuk tanda tangan.

## Mengimpor Ruang Nama yang Diperlukan

Untuk menggunakan fungsionalitas Aspose.Words, Anda perlu mengimpor namespace berikut:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Langkah 1: Menyiapkan Direktori Dokumen

Mulailah dengan menentukan jalur ke direktori dokumen Anda. Di sinilah Anda akan menyimpan dan mengambil dokumen Anda.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Tentukan jalur direktori dokumen Anda
```

## Langkah 2: Membuat Dokumen Baru

Selanjutnya, mari buat dokumen Word baru. Dokumen ini akan berfungsi sebagai kanvas untuk baris tanda tangan Anda.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 3: Memasukkan Baris Tanda Tangan

 Sekarang, gunakan`DocumentBuilder` kelas untuk menyisipkan baris tanda tangan ke dalam dokumen Anda:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Langkah 4: Menyimpan Dokumen

Setelah Anda memasukkan baris tanda tangan, simpan dokumen tersebut. Ini adalah langkah penting sebelum menandatangani.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Langkah 5: Mengonfigurasi Opsi Penandatanganan

Siapkan opsi untuk proses penandatanganan. Ini termasuk menentukan ID baris tanda tangan dan gambar opsional untuk ditampilkan bersama tanda tangan.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // Jalur menuju gambar Anda
};
```

## Langkah 6: Memuat Sertifikat

Muat file sertifikat yang diperlukan untuk menandatangani dokumen:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Sesuaikan nama file dan kata sandi
```

## Langkah 7: Menandatangani Dokumen

 Terakhir, tandatangani dokumen menggunakan`DigitalSignatureUtil` kelas. Simpan dokumen yang ditandatangani dengan nama baru untuk referensi di masa mendatang.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Kesimpulan

Selamat! Anda telah berhasil membuat dokumen Word, menambahkan baris tanda tangan, dan menandatanganinya secara digital menggunakan Aspose.Words untuk .NET. Alat canggih ini menyederhanakan otomatisasi dokumen, memastikan kontrak dan dokumen formal Anda ditandatangani dan diautentikasi dengan aman.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan format gambar lain untuk baris tanda tangan?

Ya, Anda dapat menggunakan berbagai format gambar, termasuk PNG, JPG, dan BMP.

###  Apakah perlu menggunakan`.pfx` file for the certificate?

 Ya, sebuah`.pfx` file adalah format standar untuk menyimpan sertifikat dan kunci pribadi untuk tanda tangan digital.

### Bisakah saya menambahkan beberapa baris tanda tangan dalam satu dokumen?

Tentu saja! Anda dapat menyisipkan beberapa baris tanda tangan dengan mengulangi langkah penyisipan sesuai kebutuhan.

### Bagaimana jika saya tidak memiliki sertifikat digital?

Anda perlu memperoleh sertifikat digital dari otoritas sertifikat tepercaya atau membuatnya menggunakan alat seperti OpenSSL.

### Bagaimana cara memverifikasi tanda tangan digital dalam dokumen?

Anda dapat memverifikasi tanda tangan digital dengan membuka dokumen yang ditandatangani di Word dan memeriksa detail tanda tangan untuk mengonfirmasi keaslian dan integritasnya.