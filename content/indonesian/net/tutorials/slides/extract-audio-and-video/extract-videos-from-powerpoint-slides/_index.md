---
title: Ekstrak Video dari Slide PowerPoint dengan Aspose.Slides
linktitle: Ekstrak Video dari Slide PowerPoint
second_title: API Pemrosesan PowerPoint Aspose.Slides .NET
description: Temukan cara mudah mengekstrak file video yang disematkan dari presentasi PowerPoint menggunakan Aspose.Slides for .NET. Panduan langkah demi langkah yang komprehensif ini mencakup semuanya, mulai dari menyiapkan lingkungan hingga menyimpan video yang diekstrak.
type: docs
weight: 14
url: /id/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## Perkenalan

Aspose.Slides for .NET adalah pustaka canggih yang memungkinkan pengembang berinteraksi dengan presentasi PowerPoint secara terprogram. Dalam panduan ini, kami akan memandu Anda melalui proses mengekstrak video yang disematkan dalam slide PowerPoint menggunakan Aspose.Slides for .NET. 

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

-  Aspose.Slides untuk .NET: Dapatkan dan instal pustaka dari[Situs web Aspose](https://purchase.aspose.com/buy).
-  Presentasi PowerPoint: Siapkan file PowerPoint (misalnya,`Video.pptx`) dengan video yang ingin Anda ekstrak.

## Ruang Nama yang Diperlukan

Untuk bekerja dengan Aspose.Slides for .NET, Anda perlu mengimpor namespace yang sesuai. Sertakan yang berikut dalam kode Anda:

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## Langkah 1: Tentukan Direktori Dokumen

Pertama, tentukan jalur ke presentasi PowerPoint Anda:

```csharp
string dataDir = "Your Document Directory";
```

 Mengganti`"Your Document Directory"` dengan jalur sebenarnya ke direktori yang berisi berkas PowerPoint Anda.

## Langkah 2: Muat Presentasi

 Memuat presentasi PowerPoint ke dalam`Presentation` obyek:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

 Ini menginisialisasi`Presentation` objek dengan berkas PowerPoint yang Anda tentukan.

## Langkah 3: Ulangi Melalui Slide dan Bentuk

Selanjutnya, ulangi setiap slide dalam presentasi dan periksa bingkai video:

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // Lanjutkan untuk mengekstrak video
        }
    }
}
```

## Langkah 4: Ekstrak Data Video

Setelah Anda menemukan bingkai video, ekstrak propertinya dan data binernya:

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // Simpan bentuk sebagai bingkai video
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// Dapatkan ekstensi file
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## Langkah 5: Simpan Video

Terakhir, tulis data video yang diekstrak ke sebuah file:

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

Kode ini membuat file baru di direktori yang Anda tentukan dan menulis data video ke dalamnya.

## Kesimpulan

Dengan Aspose.Slides untuk .NET, mengekstrak video dari slide PowerPoint merupakan proses yang mudah. Dengan mengikuti panduan ini, Anda dapat mengelola konten multimedia dengan mudah dalam aplikasi .NET, yang memperkaya pengalaman dan fungsionalitas pengguna.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Slides untuk .NET?
Aspose.Slides untuk .NET adalah pustaka yang dirancang untuk bekerja dengan presentasi PowerPoint, yang memungkinkan pengguna untuk membuat, mengedit, dan memanipulasi file presentasi secara terprogram.

### Di mana saya dapat menemukan dokumentasi untuk Aspose.Slides for .NET?
 Anda dapat mengakses dokumentasi lengkapnya[Di Sini](https://reference.aspose.com/slides/net/).

### Apakah Aspose.Slides untuk .NET tersedia untuk uji coba gratis?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[tautan ini](https://releases.aspose.com/).

### Bagaimana cara memperoleh lisensi sementara untuk Aspose.Slides for .NET?
 Permintaan lisensi sementara dapat dilakukan[Di Sini](https://purchase.aspose.com/temporary-license/).

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Slides untuk .NET?
 Dukungan tersedia melalui[Forum Aspose.Slides](https://forum.aspose.com/).