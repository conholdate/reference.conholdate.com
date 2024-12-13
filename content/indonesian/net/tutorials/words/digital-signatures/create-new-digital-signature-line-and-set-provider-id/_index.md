---
title: Buat Baris Tanda Tangan Digital Baru dan Tetapkan ID Penyedia
linktitle: Buat Baris Tanda Tangan Digital Baru dan Tetapkan ID Penyedia
second_title: API Pemrosesan Dokumen Aspose.Words
description: Temukan cara menambahkan baris tanda tangan secara terprogram ke dokumen Word Anda menggunakan Aspose.Words untuk .NET. Panduan komprehensif ini mencakup semuanya mulai dari menyiapkan lingkungan pengembangan hingga memasukkan baris tanda tangan dan menandatangani dokumen dengan aman.
type: docs
weight: 10
url: /id/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## Perkenalan

Halo, penggemar teknologi! Pernahkah Anda ingin mengotomatiskan penyertaan baris tanda tangan dalam dokumen Word Anda? Hari ini, kita akan membahas cara melakukannya menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah ini akan memandu Anda membuat baris tanda tangan dan menyetel ID penyedia, sehingga tugas pemrosesan dokumen Anda menjadi lebih efisien dan lancar.

## Prasyarat

Sebelum kita mulai, mari pastikan Anda telah menyiapkan semuanya:

1.  Aspose.Words untuk .NET: Jika Anda belum menginstalnya, unduh[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Gunakan Visual Studio atau pengaturan pengembangan C# apa pun.
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda.
4. Sertifikat PFX: Anda memerlukan sertifikat PFX untuk menandatangani dokumen, yang dapat diperoleh dari otoritas sertifikat tepercaya.

## Mengimpor Ruang Nama yang Diperlukan

Untuk memulai, impor namespace yang diperlukan ke dalam proyek C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Sekarang, mari selami detail pembuatan baris tanda tangan baru dan pengaturan ID penyedia.

## Langkah 1: Buat Dokumen Baru

Pertama, kita perlu membuat dokumen Word baru, yang akan berfungsi sebagai kanvas untuk baris tanda tangan kita:

```csharp
// Tentukan jalur ke direktori dokumen Anda.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Di sini, kita menginisialisasi yang baru`Document` dan sebuah`DocumentBuilder`, yang memungkinkan kita menambahkan elemen dengan mudah.

## Langkah 2: Tentukan Opsi Baris Tanda Tangan

Berikutnya, kita akan menentukan opsi untuk baris tanda tangan kita, termasuk nama penanda tangan, jabatan, email, dan detail relevan lainnya:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Pilihan ini membantu mempersonalisasi baris tanda tangan, menjadikannya jelas dan profesional.

## Langkah 3: Masukkan Baris Tanda Tangan

Setelah opsi kita siap, sekarang kita dapat memasukkan baris tanda tangan ke dalam dokumen:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Itu`InsertSignatureLine` metode menambahkan baris tanda tangan, dan kami menetapkan ID penyedia yang unik padanya.

## Langkah 4: Simpan Dokumen

Setelah memasukkan baris tanda tangan, mari simpan dokumennya:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Ini akan menyimpan dokumen Anda dengan baris tanda tangan yang baru ditambahkan.

## Langkah 5: Siapkan Opsi Penandatanganan

Sekarang, kita akan mengonfigurasi opsi penandatanganan, termasuk ID baris tanda tangan, ID penyedia, komentar, dan waktu penandatanganan:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Pengaturan ini memastikan bahwa dokumen ditandatangani dengan rincian yang benar.

## Langkah 6: Buat Pemegang Sertifikat

Untuk menandatangani dokumen, kita perlu membuat pemegang sertifikat menggunakan sertifikat PFX:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Mengganti`"morzal.pfx"` dengan nama file sertifikat Anda yang sebenarnya dan`"aw"` dengan kata sandi sertifikat Anda.

## Langkah 7: Tandatangani Dokumen

Terakhir, kami akan menandatangani dokumen menggunakan utilitas tanda tangan digital:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Proses ini menandatangani dokumen dan menyimpannya sebagai berkas baru.

## Kesimpulan

Selamat! Anda telah berhasil membuat baris tanda tangan dan menetapkan ID penyedia dalam dokumen Word menggunakan Aspose.Words untuk .NET. Pustaka canggih ini menyederhanakan tugas pemrosesan dokumen, membuat alur kerja Anda lebih efisien. Cobalah dan lihat bagaimana pustaka ini dapat menyempurnakan proyek Anda!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan tampilan baris tanda tangan?
 Tentu saja! Anda dapat menyesuaikan berbagai opsi di`SignatureLineOptions` agar sesuai dengan gaya dan kebutuhan Anda.

### Bagaimana jika saya tidak memiliki sertifikat PFX?
Anda perlu mendapatkannya dari otoritas sertifikat tepercaya, karena penting untuk menandatangani dokumen secara digital.

### Bisakah saya menambahkan beberapa baris tanda tangan ke sebuah dokumen?
Ya, Anda dapat menambahkan beberapa baris tanda tangan dengan mengulangi proses penyisipan dengan opsi yang berbeda.

### Apakah Aspose.Words untuk .NET kompatibel dengan .NET Core?
Ya, Aspose.Words untuk .NET mendukung .NET Core, membuatnya serbaguna untuk berbagai lingkungan pengembangan.

### Seberapa amankah tanda tangan digital?
Tanda tangan digital yang dibuat dengan Aspose.Words sangat aman, asalkan Anda menggunakan sertifikat yang valid dan tepercaya.