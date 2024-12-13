---
title: Terapkan pengaturan Urutan Halaman di Lembar Kerja
linktitle: Terapkan pengaturan Urutan Halaman di Lembar Kerja
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Pelajari cara mengonfigurasi pengaturan urutan halaman di Excel menggunakan Aspose.Cells untuk .NET. Panduan langkah demi langkah ini menunjukkan cara mencetak di seluruh baris terlebih dahulu dan kemudian di seluruh kolom, memastikan lembar kerja besar Anda tampak rapi di atas kertas.
type: docs
weight: 24
url: /id/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-page-order-settings/
---
## Perkenalan

Saat bekerja dengan lembar kerja Excel yang besar, mengendalikan tata letak cetak sangat penting untuk kejelasan dan pengaturan. Aspose.Cells untuk .NET menawarkan fitur-fitur tangguh yang memungkinkan Anda untuk menyesuaikan pengaturan cetak lembar kerja Anda dengan mudah. Dalam panduan ini, kami akan memandu Anda melalui langkah-langkah untuk mengatur urutan halaman agar dapat dicetak di baris terlebih dahulu dan kemudian di kolom.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Aspose.Cells untuk .NET: Unduh dari[Situs web Aspose](https://releases.aspose.com/cells/net/) dan menginstalnya di proyek Anda.
2. Lingkungan Pengembangan: Gunakan IDE yang kompatibel dengan .NET, seperti Visual Studio.
3. Pengetahuan Dasar C#: Keakraban dengan C# akan membantu Anda memahami cuplikan kode.

 Anda juga bisa mencobanya[Aspose.Cells untuk .NET dengan uji coba gratis](https://releases.aspose.com/) atau dapatkan[lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk akses fitur lengkap.

## Impor Paket yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan untuk mengakses fungsionalitas Aspose.Cells:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

## Langkah 1: Buat Buku Kerja

Pertama, buat contoh buku kerja baru, yang mewakili file Excel Anda.

```csharp
// Buat objek Buku Kerja baru
Workbook workbook = new Workbook();
```

Baris ini menginisialisasi buku kerja Excel kosong, siap untuk kustomisasi.

## Langkah 2: Akses PageSetup dari Lembar Kerja

 Untuk menyesuaikan pengaturan cetak, akses`PageSetup` objek lembar kerja.

```csharp
// Mengakses PageSetup dari lembar kerja pertama
PageSetup pageSetup = workbook.Worksheets[0].PageSetup;
```

 Di sini, kami mengambil`PageSetup` untuk lembar kerja pertama, di mana kita akan mengonfigurasi tata letak cetak.

## Langkah 3: Atur Urutan Halaman ke OverThenDown

Sekarang, mari kita atur urutan halaman. Secara default, Excel akan mencetak setiap kolom terlebih dahulu; kita akan mengubahnya untuk mencetak seluruh baris terlebih dahulu.

```csharp
// Atur urutan cetak ke OverThenDown
pageSetup.Order = PrintOrderType.OverThenDown;
```

Pengaturan ini memastikan bahwa saat dicetak, data mengalir secara horizontal sebelum berpindah ke baris berikutnya, yang sangat berguna untuk kumpulan data yang luas.

## Langkah 4: Simpan Buku Kerja

Terakhir, simpan buku kerja Anda untuk menerapkan perubahan.

```csharp
// Tentukan jalur untuk menyimpan buku kerja
string dataDir = "Your Document Directory/";
// Simpan buku kerja
workbook.Save(dataDir + "SetPageOrder_out.xls");
```

 Mengganti`"Your Document Directory"`dengan jalur file yang Anda inginkan. Anda juga dapat menyimpannya dalam format lain, seperti`.xlsx`, dengan mengubah ekstensi file.

## Kesimpulan

Selamat! Anda telah berhasil mengatur urutan halaman dalam lembar kerja Excel menggunakan Aspose.Cells untuk .NET. Penyesuaian sederhana ini dapat meningkatkan penyajian kumpulan data besar secara signifikan saat dicetak. Aspose.Cells menyediakan banyak pengaturan cetak lain yang dapat disesuaikan, menjadikannya alat yang sangat berharga untuk persiapan laporan dan pengaturan dokumen.

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengubah urutan halaman untuk beberapa lembar kerja sekaligus?

 Ya, Anda dapat mengulang setiap lembar kerja di buku kerja dan menerapkan hal yang sama`PageSetup.Order` pengaturan.

### Apa saja pilihan lain untuk pemesanan cetak yang tersedia?

 Di samping itu`OverThenDown` , kamu bisa menggunakan`DownThenOver`, yang mencetak kolom terlebih dahulu sebelum berpindah antar baris.

### Apakah kode ini memerlukan lisensi?

 Beberapa fitur mungkin terbatas tanpa lisensi. Anda dapat mencoba[Aspose.Cells untuk .NET dengan uji coba gratis](https://releases.aspose.com/).

### Bisakah saya melihat dulu susunan halaman sebelum mencetaknya?

Meskipun Aspose.Cells memungkinkan Anda mengatur konfigurasi cetak, Anda harus membuka file yang disimpan di Excel untuk melihat pratinjau tata letaknya.

### Apakah pengaturan urutan halaman ini kompatibel dengan ekspor PDF?

Ya, pengaturan urutan halaman akan berlaku untuk ekspor PDF dan format lain yang didukung, guna memastikan alur halaman yang konsisten.