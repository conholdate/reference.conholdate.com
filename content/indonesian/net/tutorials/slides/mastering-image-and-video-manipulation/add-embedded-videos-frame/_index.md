---
title: Tambahkan Bingkai Video Tertanam dalam Presentasi .NET
linktitle: Tambahkan Bingkai Video Tertanam dalam Presentasi .NET
second_title: API Pemrosesan PowerPoint Aspose.Slides .NET
description: Manfaatkan potensi presentasi Anda dengan mempelajari cara menyematkan video menggunakan Aspose.Slides for .NET. Tutorial komprehensif ini memandu Anda melalui proses langkah demi langkah untuk mengintegrasikan elemen multimedia.
type: docs
weight: 19
url: /id/net/tutorials/slides/mastering-image-and-video-manipulation/add-embedded-videos-frame/
---
## Perkenalan

Dalam lanskap presentasi yang serba cepat saat ini, mengintegrasikan elemen multimedia dapat meningkatkan keterlibatan dan retensi audiens secara signifikan. Aspose.Slides untuk .NET menawarkan solusi yang tangguh untuk menyematkan bingkai video ke dalam slide Anda. Tutorial ini akan memandu Anda melalui proses ini langkah demi langkah, memastikan pengalaman yang lancar dari awal hingga akhir.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

-  Aspose.Slides untuk Pustaka .NET: Unduh dan instal pustaka dari[halaman rilis](https://releases.aspose.com/slides/net/).
- Konten Media: Berkas video (misalnya, "Wildlife.mp4") yang ingin Anda sematkan dalam presentasi Anda.

## Impor Ruang Nama yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan dalam proyek .NET Anda:

```csharp
using System.IO;
using Aspose.Slides;
using Aspose.Slides.Export;
```

## Langkah 1: Siapkan Direktori Anda

Pastikan proyek Anda menyertakan direktori yang diperlukan untuk file dokumen dan media:

```csharp
string dataDir = "Your Document Directory";
string videoDir = "Your Media Directory";
string resultPath = Path.Combine(dataDir, "VideoFrame_out.pptx");

// Buat direktori jika belum ada
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## Langkah 2: Buat Instansiasi Kelas Presentasi

 Buat contoh dari`Presentation` kelas untuk mewakili file PPTX Anda:

```csharp
using (Presentation pres = new Presentation())
{
    // Dapatkan slide pertama
    ISlide sld = pres.Slides[0];
```

## Langkah 3: Sematkan Video

Sematkan video ke presentasi Anda menggunakan kode berikut:

```csharp
IVideo vid = pres.Videos.AddVideo(new FileStream(Path.Combine(videoDir, "Wildlife.mp4"), FileMode.Open), LoadingStreamBehavior.ReadStreamAndRelease);
```

## Langkah 4: Tambahkan Bingkai Video

Berikutnya, tambahkan bingkai video ke slide:

```csharp
IVideoFrame vf = sld.Shapes.AddVideoFrame(50, 150, 300, 350, vid);
```

## Langkah 5: Konfigurasikan Properti Video

Tetapkan properti video, termasuk mode pemutaran dan volume:

```csharp
vf.EmbeddedVideo = vid;
vf.PlayMode = VideoPlayModePreset.Auto; // Putar video secara otomatis
vf.Volume = AudioVolumeMode.Loud; // Mengatur tingkat volume
```

## Langkah 6: Simpan Presentasi Anda

Terakhir, simpan file PPTX yang dimodifikasi ke disk:

```csharp
pres.Save(resultPath, SaveFormat.Pptx);
```

Anda dapat mengulangi langkah-langkah ini untuk setiap video yang ingin Anda masukkan dalam presentasi Anda.

## Kesimpulan

Selamat! Anda telah berhasil menyematkan bingkai video ke dalam presentasi Anda menggunakan Aspose.Slides for .NET. Fitur dinamis ini dapat membawa presentasi Anda ke tingkat berikutnya, memikat audiens Anda dengan multimedia yang terintegrasi dengan sempurna.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyematkan video di slide presentasi mana pun?

 Ya, Anda dapat memilih slide mana pun dengan menyesuaikan indeks di`pres.Slides[index]`.

### Format video apa yang didukung?

Aspose.Slides mendukung berbagai format video, termasuk MP4, AVI, dan WMV.

### Bisakah saya menyesuaikan ukuran dan posisi bingkai video?

 Tentu saja! Anda dapat mengubah parameter di`AddVideoFrame(x, y, width, height, video)` untuk memenuhi kebutuhan Anda.

### Apakah ada batasan jumlah video yang dapat saya sematkan?

Batasan pada video yang tertanam biasanya bergantung pada kapasitas perangkat lunak presentasi Anda.

### Di mana saya dapat mencari bantuan lebih lanjut atau berbagi pengalaman saya?

 Jangan ragu untuk mengunjungi[Forum Aspose.Slides](https://forum.aspose.com/c/slides/11) untuk dukungan dan diskusi komunitas.