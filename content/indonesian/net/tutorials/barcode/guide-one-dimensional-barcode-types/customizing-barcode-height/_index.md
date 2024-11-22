---
title: Menyesuaikan Tinggi Barcode dengan Aspose.BarCode di .NET
linktitle: Menyesuaikan Tinggi Kode Batang
second_title: Aspose.BarCode .NET API
description: Pelajari cara menyesuaikan tinggi kode batang satu dimensi secara efisien di aplikasi .NET Anda menggunakan Aspose.BarCode. Tutorial komprehensif ini menyediakan contoh-contoh yang jelas.
type: docs
weight: 13
url: /id/net/tutorials/barcode/guide-one-dimensional-barcode-types/customizing-barcode-height/
---
## Perkenalan

Saat membangun aplikasi .NET yang memerlukan pembuatan kode batang—seperti untuk manajemen inventaris atau ritel—memiliki kendali yang tepat atas properti kode batang dapat menjadi hal yang penting. Aspose.BarCode untuk .NET adalah perangkat tangguh yang memungkinkan Anda menyesuaikan kode batang dengan mudah, termasuk kemampuan untuk menyesuaikan tingginya. Dalam panduan ini, kami akan memberi Anda proses langkah demi langkah untuk mengubah tinggi kode batang satu dimensi menggunakan Aspose.BarCode.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki prasyarat berikut:

- Lingkungan pengembangan dengan .NET Framework atau .NET Core.
-  Pustaka Aspose.BarCode untuk .NET, yang dapat diunduh[Di Sini](https://releases.aspose.com/barcode/net/).
- Editor kode pilihan Anda untuk menulis dan menjalankan kode Anda.

## Memulai

Kita akan mulai dengan mengimpor namespace yang diperlukan untuk bekerja dengan Aspose.BarCode.

### Mengimpor Ruang Nama

Tambahkan perintah berikut ke berkas kode Anda:

```csharp
using Aspose.BarCode.Generation;
```

## Langkah 1: Tentukan Jalur Direktori Anda

Tetapkan jalur direktori tempat Anda ingin menyimpan gambar kode batang yang dihasilkan. Pastikan untuk mengganti "Jalur Direktori Anda" dengan jalur sebenarnya di sistem Anda:

```csharp
string path = @"C:\YourDirectoryPath\"; // Pastikan Anda menyertakan garis miring terbalik di akhir
```

## Langkah 2: Buat Generator Kode Batang

 Buat contoh dari`BarcodeGenerator` kelas. Di sini, kita akan menggunakan`Code128` jenis kode batang dan atur nilainya menjadi "ASPOSE":

```csharp
BarcodeGenerator barcodeGen = new BarcodeGenerator(EncodeTypes.Code128, "ASPOSE");
```

## Langkah 3: Sesuaikan Tinggi Kode Batang

 Langkah ini melibatkan modifikasi tinggi kode batang menggunakan`BarHeight` properti. Kami akan menunjukkan cara membuat dua gambar kode batang dengan tinggi yang berbeda—40 piksel dan 80 piksel.

```csharp
// Sesuaikan tinggi menjadi 40 piksel
barcodeGen.Parameters.Barcode.BarHeight.Pixels = 40;
barcodeGen.Save($"{path}BarHeight40Code128.png", BarCodeImageFormat.Png);

// Sesuaikan tinggi menjadi 80 piksel
barcodeGen.Parameters.Barcode.BarHeight.Pixels = 80;
barcodeGen.Save($"{path}BarHeight80Code128.png", BarCodeImageFormat.Png);
```

## Kesimpulan

Dalam tutorial ini, Anda mempelajari cara menyesuaikan tinggi kode batang satu dimensi menggunakan Aspose.BarCode for .NET. Dengan kemampuan untuk menyesuaikan berbagai properti kode batang, Anda dapat membuat gambar kode batang yang disesuaikan untuk memenuhi persyaratan aplikasi spesifik Anda.

## Pertanyaan yang Sering Diajukan

### Jenis kode batang apa yang didukung Aspose.BarCode untuk .NET?
 Aspose.BarCode mendukung berbagai jenis kode batang, termasuk Code128, QR Code, DataMatrix, dan masih banyak lagi. Anda dapat menemukan daftar lengkapnya di[dokumentasi](https://reference.aspose.com/barcode/net/).

### Bisakah saya juga menyesuaikan lebar kode batang?
Tentu saja! Anda dapat mengubah lebar kode batang satu dimensi dengan menggunakan pendekatan yang sama untuk menyesuaikan tinggi.

### Apakah ada uji coba gratis untuk Aspose.BarCode untuk .NET?
 Ya! Uji coba gratis tersedia bagi Anda untuk menjelajahi Aspose.BarCode untuk .NET. Unduh[Di Sini](https://releases.aspose.com/barcode/net/).

### Bisakah saya membuat kode batang dalam berbagai format gambar?
Aspose.BarCode untuk .NET mendukung berbagai format gambar, seperti PNG, JPEG, dan TIFF, memungkinkan Anda memilih salah satu yang sesuai dengan kebutuhan Anda.

### Di mana saya dapat menemukan dokumentasi terperinci?
 Untuk informasi mendalam tentang cara menggunakan Aspose.BarCode di proyek Anda, lihat[dokumentasi](https://reference.aspose.com/barcode/net/).