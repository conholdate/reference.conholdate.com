---
title: Menambahkan Tanda Tangan Digital Baru ke File Excel yang Ditandatangani
linktitle: Menambahkan Tanda Tangan Digital Baru ke File Excel yang Ditandatangani
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara menambahkan tanda tangan digital baru ke berkas Excel yang sudah ditandatangani menggunakan Aspose.Cells untuk .NET. Panduan lengkap ini mencakup semua prasyarat, petunjuk langkah demi langkah, dan contoh kode.
type: docs
weight: 12
url: /id/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## Perkenalan

Dalam lanskap digital saat ini, memastikan keaslian dan integritas dokumen lebih penting dari sebelumnya. Tanda tangan digital menyediakan cara yang andal untuk memverifikasi bahwa dokumen belum diubah dan berasal dari sumber yang sah. Jika Anda bekerja dengan file Excel dalam .NET dan perlu menambahkan tanda tangan digital baru ke file yang sudah ditandatangani, panduan ini cocok untuk Anda! Kami akan memandu Anda melalui proses penambahan tanda tangan digital ke file Excel yang sudah ditandatangani menggunakan Aspose.Cells untuk .NET.

## Prasyarat

Sebelum kita mulai implementasinya, pastikan Anda memiliki hal berikut:

1.  Aspose.Cells untuk .NET: Unduh dan instal Aspose.Cells dari[halaman rilis](https://releases.aspose.com/cells/net/).
2. .NET Framework: Pastikan komputer Anda telah menginstal .NET Framework dan Anda memahami konsep dasar pemrograman .NET.
3. Sertifikat Digital: Dapatkan sertifikat digital yang valid dalam format .pfx. Untuk pengujian, Anda dapat membuat sertifikat yang ditandatangani sendiri.
4. Lingkungan Pengembangan: Gunakan IDE seperti Visual Studio untuk menulis dan mengeksekusi kode C# Anda.
5. Contoh Berkas Excel: Miliki berkas Excel yang sudah ditandatangani secara digital, yang akan menjadi target untuk menambahkan tanda tangan baru.

Jika prasyarat ini terpenuhi, mari masuk ke kodenya!

## Impor Paket yang Diperlukan

Di bagian atas file C# Anda, sertakan namespace berikut untuk mengakses kelas dan metode yang diperlukan:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Langkah 1: Tentukan Direktori Anda

Tentukan direktori untuk file sumber Anda dan tempat menyimpan file keluaran:

```csharp
// Direktori sumber
string sourceDir = "Your Document Directory"; // Ganti dengan direktori Anda yang sebenarnya
// Direktori keluaran
string outputDir = "Your Document Directory"; // Ganti dengan direktori Anda yang sebenarnya
```

## Langkah 2: Muat Buku Kerja yang Sudah Ditandatangani

Muat buku kerja Excel yang sudah ditandatangani:

```csharp
// Muat buku kerja yang sudah ditandatangani secara digital
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## Langkah 3: Buat Koleksi Tanda Tangan Digital

Buat koleksi untuk mengelola tanda tangan digital Anda:

```csharp
//Buat koleksi tanda tangan digital
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## Langkah 4: Muat Sertifikat Anda

Muat sertifikat digital Anda, yang akan digunakan untuk membuat tanda tangan baru:

```csharp
// File sertifikat dan kata sandinya
string certFileName = sourceDir + "AsposeDemo.pfx"; // File sertifikat Anda
string password = "aspose"; // Kata sandi sertifikat Anda

// Buat sertifikat baru
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## Langkah 5: Buat Tanda Tangan Digital Baru

Sekarang, buat tanda tangan digital baru dan tambahkan ke koleksi Anda:

```csharp
// Buat tanda tangan digital baru dan tambahkan ke koleksi
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## Langkah 6: Tambahkan Koleksi Tanda Tangan ke Buku Kerja

Tambahkan koleksi tanda tangan digital ke buku kerja:

```csharp
// Tambahkan koleksi tanda tangan digital ke buku kerja
workbook.AddDigitalSignature(dsCollection);
```

## Langkah 7: Simpan Buku Kerja

Simpan buku kerja dengan tanda tangan digital baru yang disertakan:

```csharp
// Simpan buku kerja
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## Langkah 8: Konfirmasikan Keberhasilan

Berikan umpan balik setelah eksekusi berhasil:

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## Kesimpulan

Selamat! Anda telah berhasil menambahkan tanda tangan digital baru ke berkas Excel yang sudah ditandatangani menggunakan Aspose.Cells for .NET. Proses ini meningkatkan keamanan dokumen Anda dan memastikan keaslian serta integritasnya.

## Pertanyaan yang Sering Diajukan

### Apa itu tanda tangan digital?

Tanda tangan digital adalah skema matematika yang memverifikasi keaslian dan integritas pesan atau dokumen digital, memastikannya tidak diubah dan mengonfirmasi identitas penanda tangan.

### Apakah saya memerlukan sertifikat khusus untuk membuat tanda tangan digital?

Ya, sertifikat digital yang diterbitkan oleh otoritas sertifikat (CA) tepercaya diperlukan untuk membuat tanda tangan digital yang valid.

### Dapatkah saya menggunakan sertifikat yang ditandatangani sendiri untuk pengujian?

Tentu saja! Anda dapat menggunakan sertifikat yang ditandatangani sendiri untuk tujuan pengembangan dan pengujian, tetapi untuk produksi, sebaiknya gunakan sertifikat dari CA tepercaya.

### Apa yang terjadi jika saya mencoba menambahkan tanda tangan ke dokumen yang tidak ditandatangani?

Jika Anda mencoba menambahkan tanda tangan digital ke dokumen yang belum ditandatangani, prosesnya akan berfungsi tanpa masalah, tetapi tanda tangan asli tidak akan ada.

### Di mana saya dapat menemukan informasi lebih lanjut tentang Aspose.Cells?

 Untuk panduan terperinci dan referensi API, periksa[Dokumentasi Aspose.Cells](https://reference.aspose.com/cells/net/).