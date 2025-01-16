---
title: Membuat Bentuk Grup di PowerPoint dengan Aspose.Slides untuk .NET
linktitle: Membuat Bentuk Grup di PowerPoint dengan Aspose.Slides untuk .NET
second_title: API Pemrosesan PowerPoint Aspose.Slides .NET
description: Pelajari cara membuat dan mengelola bentuk grup menggunakan Aspose.Slides untuk .NET. Panduan lengkap ini menyediakan petunjuk langkah demi langkah yang jelas.
type: docs
weight: 11
url: /id/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## Perkenalan

Meningkatkan daya tarik visual dan pengaturan presentasi PowerPoint Anda dapat berdampak signifikan pada keterlibatan audiens Anda. Salah satu metode efektif untuk mencapainya adalah melalui bentuk grup. Dalam tutorial ini, kita akan membahas cara memanfaatkan Aspose.Slides for .NET untuk membuat dan memanipulasi bentuk grup dalam presentasi Anda.

## Prasyarat

Sebelum memulai tutorial, pastikan Anda memiliki hal berikut:

-  Aspose.Slides untuk .NET: Unduh dan instal versi terbaru pustaka Aspose.Slides dari[Situs web Aspose](https://releases.aspose.com/slides/net/).
- Lingkungan Pengembangan: Siapkan IDE yang kompatibel dengan .NET, seperti Visual Studio, untuk mengerjakan proyek Anda.
- Pengetahuan Dasar C#: Biasakan diri Anda dengan konsep dasar C#.


## Impor Ruang Nama yang Diperlukan

Dalam proyek C# Anda, mulailah dengan menyertakan namespace berikut:

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## Langkah 1: Buat Instansiasi Kelas Presentasi

 Buat contoh dari`Presentation`kelas tempat Anda akan mengerjakan slide Anda. Tentukan direktori tempat dokumen Anda disimpan:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // Langkah-langkah untuk membuat dan memanipulasi bentuk akan ada di sini
}
```

## Langkah 2: Akses Slide Pertama

Ambil slide pertama dari presentasi yang baru Anda buat:

```csharp
ISlide slide = pres.Slides[0];
```

## Langkah 3: Akses Koleksi Bentuk

Dapatkan koleksi bentuk pada slide:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## Langkah 4: Tambahkan Bentuk Grup

Sekarang saatnya menambahkan bentuk grup ke slide:

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## Langkah 5: Tambahkan Bentuk di Dalam Grup

Anda dapat mengisi bentuk grup dengan bentuk individual, seperti persegi panjang:

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // Bentuk 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // Bentuk 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // Bentuk 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // Bentuk 4
```

## Langkah 6: Tentukan Bingkai untuk Bentuk Grup

Menetapkan bingkai untuk bentuk grup akan memberikan batasan yang jelas:

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## Langkah 7: Simpan Presentasi

Terakhir, simpan presentasi Anda yang dimodifikasi ke direktori yang ditentukan:

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## Kesimpulan

Selamat! Anda telah berhasil membuat bentuk grup dalam presentasi PowerPoint Anda menggunakan Aspose.Slides for .NET. Dengan mengatur bentuk dengan cara ini, Anda dapat meningkatkan tata letak visual dan kejelasan konten Anda, sehingga presentasi Anda lebih berkesan.

## Pertanyaan yang Sering Diajukan

### Apakah Aspose.Slides kompatibel dengan versi .NET terbaru?

 Ya, Aspose.Slides diperbarui secara berkala untuk kompatibilitas dengan versi .NET terbaru. Periksa[dokumentasi](https://reference.aspose.com/slides/net/) untuk rincian kompatibilitas terkini.

### Bisakah saya mencoba Aspose.Slides sebelum membeli?

 Tentu saja! Anda dapat mengunduh versi uji coba gratis[Di Sini](https://releases.aspose.com/).

### Di mana saya dapat menemukan dukungan untuk kueri terkait Aspose.Slides?

 Kunjungi Aspose.Slides[forum](https://forum.aspose.com/c/slides/11) untuk dukungan dan diskusi komunitas.

### Bagaimana cara mendapatkan lisensi sementara untuk Aspose.Slides?

 Anda dapat meminta lisensi sementara[Di Sini](https://purchase.aspose.com/temporary-license/).

### Di mana saya dapat membeli lisensi lengkap untuk Aspose.Slides?

 Anda dapat membeli lisensi dari[halaman pembelian](https://purchase.aspose.com/buy).