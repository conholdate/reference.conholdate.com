---
title: Membuat Tampilan Panorama Adegan 3D Menggunakan Aspose.3D untuk .NET
linktitle: Membuat Tampilan Panorama Adegan 3D
second_title: Aspose.3D .NET API
description: Pelajari cara membuat tampilan panorama yang menakjubkan dari adegan 3D di aplikasi .NET Anda menggunakan Aspose.3D. Ikuti panduan langkah demi langkah kami untuk membuat tampilan adegan yang imersif.
type: docs
weight: 13
url: /id/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## Perkenalan

Membuat adegan 3D panorama yang imersif merupakan pengubah permainan bagi para pengembang yang ingin meningkatkan aplikasi mereka dengan efek visual yang memukau. Baik Anda bekerja pada mesin permainan, visualisasi arsitektur, atau pengalaman web yang imersif, merender adegan 3D sebagai panorama memungkinkan pengguna untuk merasakan tampilan dinamis dari semua sudut. Aspose.3D untuk .NET adalah alat yang sempurna untuk mengintegrasikan fitur ini dengan lancar ke dalam proyek .NET Anda. Panduan lengkap ini akan memandu Anda melalui proses merender panorama dari adegan 3D menggunakan Aspose.3D untuk .NET.

## Prasyarat

Sebelum memulai proses rendering, pastikan Anda telah menyiapkan hal-hal berikut:

- Aspose.3D untuk .NET: Untuk memulai, Anda perlu menginstal Aspose.3D, yang menyediakan semua alat yang diperlukan untuk menangani aset 3D dan merender.[Unduh Aspose.3D untuk .NET](https://releases.aspose.com/3d/net/) untuk memulai.
- Lingkungan Pengembangan .NET: Diperlukan lingkungan pengembangan .NET yang dikonfigurasikan sepenuhnya. Pastikan Anda memiliki Visual Studio atau IDE lain yang kompatibel.
-  Contoh File Adegan 3D: Anda dapat menggunakan adegan 3D apa pun dalam format seperti`.glb`, `.fbx` , atau`.obj`Untuk tutorial ini, kami akan menggunakan file "VirtualCity.glb" yang sederhana.

Setelah Anda memenuhi prasyarat ini, kita dapat lanjut ke penyiapan tempat kejadian.

## Impor Ruang Nama yang Diperlukan

Untuk bekerja dengan Aspose.3D, kita perlu mengimpor beberapa namespace ke dalam proyek kita. Namespace ini memungkinkan Anda untuk memanipulasi objek 3D, pengaturan kamera, dan opsi rendering secara efisien.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

Ruang nama ini penting untuk memuat pemandangan 3D, mengonfigurasi kamera, pencahayaan, dan mengatur tekstur render yang membentuk tampilan panorama.

## Langkah 1: Muat Adegan 3D ke Aplikasi Anda

 Langkah pertama adalah memuat adegan 3D ke dalam aplikasi Anda. Hal ini dapat dilakukan dengan menggunakan`Scene` kelas yang disediakan oleh Aspose.3D. Ganti`"VirtualCity.glb"` dengan jalur ke berkas adegan 3D Anda.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 Itu`Scene` objek memuat adegan 3D ke dalam memori, memungkinkan Anda berinteraksi dengannya dan menerapkan teknik rendering.

## Langkah 2: Siapkan Kamera dan Lampu

Untuk memastikan bahwa adegan 3D Anda terekam dengan benar, Anda perlu menyiapkan kamera dan pencahayaan yang sesuai. Kamera memungkinkan Anda mengendalikan perspektif adegan, sementara lampu membantu menerangi objek.

```csharp
Camera cam = new Camera(ProjectionType.Perspective)
{
    NearPlane = 0.1,
    FarPlane = 200,
    RotationMode = RotationMode.FixedDirection
};

scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(5, 6, 0);

scene.RootNode.CreateChildNode(new Light() 
{ 
    LightType = LightType.Point 
}).Transform.Translation = new Vector3(-10, 7, -10);

scene.RootNode.CreateChildNode(new Light() 
{ 
    Color = new Vector3(Color.CadetBlue) 
}).Transform.Translation = new Vector3(49, 0, 49);
```

- Pengaturan Kamera: Bidang dekat dan jauh kamera diatur untuk menentukan jarak yang terlihat dalam pemandangan 3D.
- Pengaturan Cahaya: Dua lampu ditambahkan—satu titik cahaya dan satu lagi dengan warna tertentu untuk menambah kedalaman dan realisme pada pemandangan.

## Langkah 3: Siapkan Renderer dan Tentukan Target Render

Setelah adegan, kamera, dan lampu Anda ditetapkan, langkah selanjutnya adalah membuat perender dan menentukan target render. Perender bertanggung jawab untuk menghasilkan gambar 3D, dan target render menentukan tempat penyimpanan hasil akhir.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- Tekstur Render Kubus: Ini digunakan untuk merender peta kubus untuk tampilan panorama. Kami mendefinisikan tekstur 512x512 di sini.
- Tekstur Render Akhir: Ini merupakan tekstur yang akan menahan tampilan panorama equirectangular akhir.

## Langkah 4: Konfigurasikan Viewport dan Render Scene

Setelah membuat tekstur render, kita perlu mengonfigurasi viewport, yang menentukan wilayah pemandangan 3D yang akan ditangkap kamera.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 Kode ini mengatur viewport untuk peta kubus dan merender pemandangan ke dalam`rt` render tekstur.

## Langkah 5: Terapkan Pasca-Pemrosesan untuk Proyeksi Equirectangular

Pada titik ini, kita perlu menerapkan pasca-pemrosesan untuk mengubah peta kubus menjadi tampilan panorama equirectangular. Transformasi ini memastikan bahwa gambar akhir akan menjadi panorama yang tepat.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- Proyeksi Equirectangular: Efek pasca-pemrosesan ini mengambil peta kubus dan mengubahnya menjadi proyeksi panorama equirectangular, memberikan tampilan 360 derajat yang mulus.

## Langkah 6: Simpan Panorama yang Telah Dirender

Setelah rendering dan pasca-pemrosesan selesai, langkah terakhir adalah menyimpan panorama akhir ke berkas gambar, seperti PNG.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

Ini menyimpan gambar panorama ke direktori yang ditentukan, memungkinkan Anda untuk mengintegrasikannya ke dalam aplikasi atau menampilkannya di situs web.

## Kesimpulan

Membuat tampilan panorama dari adegan 3D tidak pernah semudah ini dengan Aspose.3D untuk .NET. Dengan mengikuti langkah-langkah yang diuraikan di atas, Anda dapat dengan mudah memuat adegan 3D, mengonfigurasi kamera dan lampu, membuat adegan, dan menerapkan efek pasca-pemrosesan untuk menghasilkan gambar panorama yang imersif. Aspose.3D untuk .NET memberikan kekuatan dan fleksibilitas untuk menghidupkan visualisasi 3D Anda dan mengintegrasikannya dengan mulus ke dalam aplikasi Anda.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan pemandangan 3D saya sendiri untuk membuat panorama?
Tentu saja. Cukup ganti jalur file adegan contoh dengan lokasi adegan 3D kustom Anda.

### Apakah ada efek pasca-pemrosesan tambahan yang tersedia?
Ya, Aspose.3D menawarkan serangkaian efek pasca-pemrosesan, seperti kedalaman bidang, mekarnya gambar, dan banyak lagi, yang dapat diterapkan untuk menyempurnakan gambar yang Anda render.

### Bagaimana saya dapat mengoptimalkan kinerja rendering?
Performa rendering dapat dioptimalkan dengan menyesuaikan parameter seperti ukuran tekstur render dan resolusi, serta mengubah bidang dekat dan jauh kamera.

### Bisakah saya mengintegrasikan ini ke dalam aplikasi web?
Ya, Aspose.3D untuk .NET dapat diintegrasikan ke dalam aplikasi web .NET Anda untuk merender panorama 3D secara dinamis.

### Apakah ada forum komunitas untuk dukungan Aspose.3D?
 Ya, Anda dapat mengunjungi[Forum Aspose.3D](https://forum.aspose.com/c/3d/18) untuk dukungan dan diskusi komunitas.