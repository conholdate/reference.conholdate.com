---
title: Membuat Pemodelan 3D Primitif
linktitle: Membuat Pemodelan 3D Primitif
second_title: Aspose.3D .NET API
description: Pelajari cara membuat dan menyesuaikan model 3D primitif, termasuk kotak dan silinder, dan menyimpannya dalam format FBX dengan mudah.
type: docs
weight: 10
url: /id/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## Perkenalan

Selamat datang di dunia pemodelan 3D yang mendalam menggunakan Aspose.3D untuk .NET! Dalam tutorial komprehensif ini, kami akan memandu Anda melalui proses pembuatan model 3D primitif langkah demi langkah. Baik Anda pengembang berpengalaman atau pemula yang ingin belajar, panduan ini akan memberdayakan Anda untuk membuat elemen 3D yang memukau secara visual untuk proyek Anda.

## Prasyarat

Sebelum terjun ke pemodelan 3D, pastikan Anda memiliki prasyarat berikut:

-  Aspose.3D untuk .NET: Unduh dan instal pustaka Aspose.3D untuk .NET dari[halaman unduhan](https://releases.aspose.com/3d/net/).
  
- Lingkungan Pengembangan .NET: Siapkan lingkungan yang kompatibel dengan Aspose.3D, seperti Visual Studio.

Setelah semuanya siap, mari kita mulai petualangan pemodelan 3D kita!

## Mengimpor Ruang Nama yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan untuk mengakses fungsionalitas Aspose.3D:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Ruang nama ini akan menyediakan Anda alat yang diperlukan untuk memanipulasi model 3D dan menyimpan kreasi Anda.

## Langkah 1: Inisialisasi Objek Adegan

Buat objek pemandangan baru yang berfungsi sebagai kanvas untuk model 3D Anda:

```csharp
// Inisialisasi objek Adegan
Scene scene = new Scene();
```

Adegan ini akan berisi bentuk primitif yang akan Anda buat.

## Langkah 2: Buat Model Kotak

Selanjutnya, mari tambahkan model kotak ke adegan Anda:

```csharp
// Buat model Kotak
scene.RootNode.CreateChildNode("box", new Box());
```

Anda dapat menyesuaikan dimensi dan properti kotak agar sesuai dengan visi kreatif Anda.

## Langkah 3: Buat Model Silinder

Sekarang, tingkatkan pemandangan Anda dengan menambahkan silinder:

```csharp
// Membuat model Silinder
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Sama halnya dengan kotak, Anda bebas menyesuaikan parameter silinder untuk mendapatkan tampilan yang Anda inginkan.

## Langkah 4: Simpan Adegan dalam Format FBX

Untuk menyimpan model 3D Anda, simpan dalam format FBX:

```csharp
// Simpan gambar dalam format FBX
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Pastikan untuk memilih direktori keluaran dan nama file yang sesuai untuk model Anda.

## Langkah 5: Menampilkan Pesan Sukses

Terakhir, rayakan keberhasilan Anda dengan menampilkan pesan:

```csharp
// Menampilkan pesan sukses
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

Adegan 3D Anda yang terdiri dari model primitif sekarang sudah lengkap dan tersimpan!

## Kesimpulan

 Selamat telah membuat model 3D yang menakjubkan menggunakan Aspose.3D untuk .NET! Tutorial ini membahas dasar-dasar pemodelan primitif, tetapi kemungkinannya tidak terbatas. Jelajahi lebih lanjut tentang fitur dan teknik lanjutan di[dokumentasi](https://reference.aspose.com/3d/net/).

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan Aspose.3D untuk .NET dengan bahasa pemrograman selain .NET?

Aspose.3D terutama mendukung .NET, tetapi ada versi yang tersedia untuk Java dan platform lainnya.

### Apakah uji coba gratis tersedia?

 Ya, Anda dapat mencoba kemampuan Aspose.3D dengan[uji coba gratis](https://releases.aspose.com/).

### Di mana saya dapat menemukan dukungan untuk Aspose.3D untuk .NET?

Untuk dukungan komunitas, kunjungi[Forum Aspose.3D](https://forum.aspose.com/c/3d/18).

### Bagaimana saya bisa memperoleh lisensi sementara?

 Anda dapat meminta lisensi sementara[Di Sini](https://purchase.conholdate.com/temporary-license/).

### Apakah ada tutorial tambahan yang tersedia?

 Ya! Jelajahi lebih banyak tutorial dan contoh di[dokumentasi](https://reference.aspose.com/3d/net/).