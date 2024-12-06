---
title: Render Gambar Pemodelan 3D dengan Aspose.3D untuk .NET
linktitle: Merender Gambar Model 3D dari Kamera
second_title: Aspose.3D .NET API
description: Pelajari cara membuat dan menyesuaikan model 3D primitif, termasuk kotak dan silinder, dan menyimpannya dalam format FBX dengan mudah. Baik Anda seorang pemula atau pengembang berpengalaman, tutorial langkah demi langkah ini.
type: docs
weight: 11
url: /id/net/tutorials/3d/guide-to-rendering/render-3d-modeling-image/
---
## Perkenalan

Merender model 3D menjadi visual yang memukau merupakan keterampilan penting dalam pengembangan perangkat lunak, terutama saat memanfaatkan pustaka canggih seperti Aspose.3D untuk .NET. Dalam artikel ini, kami akan memandu Anda melalui seluruh proses merender gambar model 3D dari perspektif kamera. Pada akhirnya, Anda akan memiliki pengetahuan untuk membuat rendering 3D yang sangat terperinci, mengubah sudut kamera, dan menerapkan pencahayaan tingkat lanjut untuk hasil visual yang lebih baik.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki prasyarat berikut untuk berhasil merender gambar 3D menggunakan Aspose.3D untuk .NET:

-  Pustaka Aspose.3D untuk .NET: Pertama, unduh pustaka Aspose.3D untuk .NET. Anda dapat menginstalnya menggunakan NuGet atau mengunduhnya langsung dari[Aspose merilis halaman](https://releases.aspose.com/3d/net/).
-  Model 3D: Siapkan model 3D Anda dalam format yang kompatibel, seperti OBJ, FBX, atau 3DS. Untuk tutorial ini, kami akan menggunakan`Aspose3D.obj` mengajukan.
- Lingkungan Pengembangan .NET: Pastikan Anda memiliki lingkungan pengembangan .NET yang berfungsi. Tutorial ini mengasumsikan Anda menggunakan Visual Studio atau IDE serupa.

## Mengimpor Ruang Nama yang Diperlukan

Langkah pertama dalam menyiapkan proyek Anda adalah menyertakan namespace yang diperlukan untuk Aspose.3D. Ini akan memungkinkan kode Anda mengakses fungsionalitas Aspose.3D yang akan membantu Anda memuat model, menyiapkan kamera, pencahayaan, dan merender adegan.

```csharp
using System;
using System.IO;
using System.Collections;
using Aspose.ThreeD;
using Aspose.ThreeD.Animation;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
using Aspose.ThreeD.Utilities;
using System.Drawing;
using System.Drawing.Imaging;
```

## Langkah 1: Muat Adegan 3D

Tindakan pertama dalam alur kerja rendering 3D adalah memuat adegan, yang terdiri dari model, kamera, pencahayaan, dan elemen lain yang diperlukan untuk merender gambar. Berikut cara memuat model 3D ke dalam adegan:

```csharp
Scene scene = new Scene();
var path = "YourModelPath/Aspose3D.obj";  // Tentukan jalur model Anda di sini
scene.Open(path);
```

## Langkah 2: Siapkan Kamera

Pengaturan kamera yang tepat sangat penting untuk menangkap pemandangan dari perspektif yang diinginkan. Pada langkah ini, kita akan membuat Kamera Perspektif, mengatur bidang dekat dan jauhnya untuk kedalaman, dan memposisikan kamera di dalam pemandangan untuk menangkap model dengan benar.

```csharp
Camera cam = new Camera(ProjectionType.Perspective);
cam.NearPlane = 1;
cam.FarPlane = 500;
scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(170, 16, 130);  // Posisikan kamera
cam.LookAt = new Vector3(28, 0, -30);  // Mengatur titik fokus kamera
```

## Langkah 3: Tambahkan Pencahayaan ke Adegan

Pencahayaan memainkan peran penting dalam meningkatkan tampilan model 3D. Aspose.3D memungkinkan Anda menambahkan berbagai jenis lampu seperti lampu sorot, lampu arah, dan lampu sorot untuk menerangi pemandangan. Pada langkah ini, kita akan menambahkan kombinasi lampu-lampu ini untuk membuat model tampak lebih realistis.

```csharp
scene.RootNode.CreateChildNode(new Light()
{
    LightType = LightType.Point,
    ConstantAttenuation = 0.3,
    Color = new Vector3(Color.White)
}).Transform.Translation = new Vector3(30, 10, 10);

scene.RootNode.CreateChildNode(new Light()
{
    LightType = LightType.Directional,
    ConstantAttenuation = 0.3,
    Direction = new Vector3(-0.3, -0.4, 0.3),
    Color = new Vector3(Color.White)
});

scene.RootNode.CreateChildNode(new Light()
{
    LightType = LightType.Spot,
    CastShadows = true,
    LookAt = new Vector3(28, 10, -30),
    Color = new Vector3(Color.White)
}).Transform.Translation = new Vector3(40, 10, 50);
```

## Langkah 4: Tentukan Opsi Render Gambar

Sekarang setelah kita memiliki adegan dengan model, kamera, dan lampu, saatnya menentukan opsi render. Opsi ini memungkinkan Anda untuk menyesuaikan warna latar belakang, mengaktifkan bayangan, dan mengatur direktori tekstur untuk efek yang lebih realistis.

```csharp
ImageRenderOptions opt = new ImageRenderOptions();
opt.BackgroundColor = Color.AliceBlue;  // Mengatur warna latar belakang
opt.AssetDirectories.Add("YourDocumentDirectory" + "textures");  // Mengatur direktori tekstur
opt.EnableShadows = true;  // Aktifkan bayangan untuk kedalaman
```

## Langkah 5: Render Adegan

Setelah semuanya siap, langkah terakhir adalah merender model 3D ke dalam file gambar. Anda dapat menentukan ukuran dan format gambar, dan Aspose.3D akan menangani sisanya.

```csharp
scene.Render(cam, "YourOutputDirectory/Render3DModelImageFromCamera.png", new Size(1024, 1024), ImageFormat.Png, opt);
```

Ini akan menyajikan gambar model 3D pada direktori keluaran yang ditentukan dalam format PNG.

## Kesimpulan

Selamat! Anda kini telah mempelajari cara merender gambar model 3D dari perspektif kamera menggunakan Aspose.3D untuk .NET. Dengan mengikuti langkah-langkah di atas, Anda dapat bereksperimen dengan berbagai model, posisi kamera, dan pengaturan pencahayaan untuk menciptakan visualisasi 3D yang lebih dinamis dan menarik secara visual. Aspose.3D menawarkan fleksibilitas untuk menyesuaikan rendering 3D agar sesuai dengan kebutuhan proyek Anda.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan Aspose.3D untuk .NET dengan alat pemodelan 3D lainnya?

Ya, Aspose.3D mendukung berbagai format model 3D seperti OBJ, FBX, dan 3DS, membuatnya kompatibel dengan alat pemodelan populer seperti Blender, 3ds Max, dan Maya.

### Bagaimana saya dapat memecahkan masalah rendering?

 Untuk pemecahan masalah, periksa[Forum Aspose.3D](https://forum.aspose.com/c/3d/18) untuk solusi atas masalah rendering yang umum. Anda juga dapat merujuk ke dokumentasi untuk panduan terperinci.

### Apakah ada uji coba gratis yang tersedia?

 Ya, Aspose menawarkan[uji coba gratis](https://releases.aspose.com/) bagi Anda untuk menjelajahi semua fitur Aspose.3D dan mengevaluasi kemampuannya sebelum melakukan pembelian.

### Di mana saya dapat menemukan dokumentasi yang lengkap?

 Anda dapat menemukan dokumentasi terperinci untuk Aspose.3D untuk .NET di[halaman dokumentasi](https://reference.aspose.com/3d/net/), yang menyediakan liputan mendalam tentang fitur dan fungsi perpustakaan.

### Bagaimana cara membeli Aspose.3D untuk .NET?

 Untuk membeli Aspose.3D untuk .NET, kunjungi[halaman pembelian](https://purchase.conholdate.com/buy), di mana Anda dapat memilih lisensi yang sesuai dengan kebutuhan Anda.