---
title: Menambahkan Layer ke Geodatabase File Menggunakan Aspose.GIS untuk .NET
linktitle: Tambahkan Lapisan ke Geodatabase File
second_title: API Aspose.GIS .NET
description: Pelajari cara menambahkan layer baru ke File Geodatabase (GDB) menggunakan Aspose.GIS untuk .NET. Panduan komprehensif ini mencakup prasyarat, impor namespace, dan langkah-langkah terperinci untuk membuat dan memvalidasi layer dalam kumpulan data GIS Anda.
type: docs
weight: 16
url: /id/net/tutorials/gis/mastering-layer-management/add-layer-to-file-geo-database/
---
## Perkenalan

Teknologi Sistem Informasi Geografis (SIG) memainkan peran penting dalam analisis dan visualisasi data modern. Aspose.GIS untuk .NET adalah pustaka luar biasa yang memungkinkan pengembang untuk memanipulasi data geografis secara efisien. Panduan terperinci ini membahas cara menambahkan lapisan baru ke kumpulan data File Geodatabase (GDB) menggunakan Aspose.GIS untuk .NET. Ikuti langkah-langkah komprehensif ini untuk mengintegrasikan lapisan dengan lancar dan meningkatkan kemampuan SIG Anda.

## Prasyarat untuk Menambahkan Lapisan ke File GDB

Sebelum kita melanjutkan, pastikan Anda memiliki hal berikut:

1. Pustaka Aspose.GIS untuk .NET  
    Unduh dan instal perpustakaan dari[Aspose.GIS untuk halaman .NET](https://reference.aspose.com/gis/net/).

2. Kumpulan Data Geodatabase File (GDB)  
   Pastikan Anda memiliki kumpulan data GDB untuk operasi tersebut.

3. Lingkungan Pengembangan  
   Instal dan konfigurasikan IDE pilihan Anda dengan dukungan .NET (misalnya, Visual Studio).

4. Lisensi Sementara (Opsional)  
    Untuk evaluasi fitur lengkap, mintalah[lisensi sementara](https://purchase.conholdate.com/temporary-license/).

5. Direktori Data  
   Siapkan direktori untuk mengelola kumpulan data masukan dan keluaran Anda.

## Mengimpor Ruang Nama yang Diperlukan

Sebelum membuat kode, sertakan namespace penting untuk mengakses fungsi Aspose.GIS. Tambahkan cuplikan kode berikut di awal proyek Anda:

```csharp
using Aspose.Gis;
using Aspose.Gis.Geometries;
using Aspose.Gis.SpatialReferencing;
using System;
```

## Langkah 1: Gandakan Dataset GDB

Untuk menjaga integritas kumpulan data asli Anda, buat duplikat. Gunakan kode berikut untuk menyalin kumpulan data ke lokasi baru:

```csharp
string dataDir = "C:\\GISData\\"; // Direktori yang berisi kumpulan data Anda
string originalPath = dataDir + "ExistingDataset.gdb";
string newDatasetPath = dataDir + "ModifiedDataset.gdb";

// Fungsi untuk menduplikasi direktori
RunExamples.CopyDirectory(originalPath, newDatasetPath);
```

## Langkah 2: Buka Dataset dan Periksa Kemampuan Pembuatan

Aspose.GIS memungkinkan pengembang untuk membuka kumpulan data dan memverifikasi apakah lapisan baru dapat ditambahkan. Gunakan cuplikan berikut untuk mengonfirmasi kemampuan pembuatan kumpulan data:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    Console.WriteLine($"Can Create Layers: {dataset.CanCreateLayers}"); // Harus mengembalikan True
}
```

## Langkah 3: Buat Layer Baru di Dataset

Penambahan layer memerlukan pendefinisian sistem referensi spasial dan atributnya. Berikut cara membuat dan mengisi layer dengan data sampel:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    // Buat layer baru dengan sistem referensi spasial WGS 84
    using (var layer = dataset.CreateLayer("NewLayer", SpatialReferenceSystem.Wgs84))
    {
        // Tambahkan skema atribut
        layer.Attributes.Add(new FeatureAttribute("LocationName", AttributeDataType.String));

        // Buat dan tambahkan fitur
        var feature = layer.ConstructFeature();
        feature.SetValue("LocationName", "Sample Point");
        feature.Geometry = new Point(34.0522, -118.2437); // Garis Bujur dan Lintang
        layer.Add(feature);
    }
}
```

## Langkah 4: Buka dan Validasi Layer Baru

Setelah membuat lapisan, validasi isinya untuk memastikan keakuratan. Gunakan cuplikan kode berikut:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    using (var layer = dataset.OpenLayer("NewLayer"))
    {
        Console.WriteLine($"Feature Count: {layer.Count}");
        Console.WriteLine($"Attribute Value: {layer[0].GetValue<string>("LocationName")}");
    }
}
```

## Kesimpulan

Menambahkan lapisan ke kumpulan data File Geodatabase dengan Aspose.GIS untuk .NET merupakan proses yang mudah jika mengikuti langkah-langkah berikut. Dari menduplikasi kumpulan data hingga membuat dan memvalidasi lapisan, pustaka ini menyediakan berbagai alat yang tangguh untuk mengelola data GIS. Dengan menguasai berbagai teknik ini, Anda dapat menyempurnakan alur kerja GIS dan mencapai manipulasi data geografis yang efisien.

## Pertanyaan yang Sering Diajukan

### Untuk apa Aspose.GIS for .NET digunakan?
Aspose.GIS untuk .NET adalah pustaka yang dirancang untuk memproses dan memanipulasi data geografis, mendukung berbagai format file, termasuk Shapefile, GDB, dan banyak lagi.

### Bisakah saya menambahkan beberapa lapisan dalam satu operasi?
Ya, Aspose.GIS memungkinkan pembuatan dan pengelolaan beberapa lapisan dalam satu kumpulan data.

### Sistem referensi spasial apa yang didukung?
Pustaka mendukung berbagai sistem referensi spasial, termasuk WGS 84, NAD 83, dan CRS khusus.

### Di mana saya dapat menemukan dukungan?
 Kunjungi[Forum Aspose.GIS](https://forum.aspose.com/c/gis/33) untuk diskusi dan dukungan komunitas.

### Apakah ada uji coba gratis yang tersedia?
 Ya, sebuah[uji coba gratis](https://releases.aspose.com/) tersedia untuk menguji fitur perpustakaan.