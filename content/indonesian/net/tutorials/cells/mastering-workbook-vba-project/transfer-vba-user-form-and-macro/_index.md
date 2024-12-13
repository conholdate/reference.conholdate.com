---
title: Mentransfer Formulir Pengguna VBA dan Makro Antar Buku Kerja Excel
linktitle: Mentransfer Formulir Pengguna VBA dan Makro Antar Buku Kerja Excel
second_title: API Pemrosesan Excel Aspose.Cells .NET
description: Manfaatkan kekuatan otomatisasi Excel dengan panduan lengkap tentang cara mentransfer Formulir Pengguna VBA dan makro antar buku kerja menggunakan Aspose.Cells untuk .NET. Sempurna untuk pengembang pemula dan berpengalaman.
type: docs
weight: 11
url: /id/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Perkenalan

Selamat datang di panduan utama untuk meningkatkan pengalaman Excel Anda menggunakan makro VBA dan formulir pengguna! Dalam tutorial ini, kita akan menjelajahi cara mentransfer Desainer UserForm Makro VBA dari satu buku kerja ke buku kerja lain menggunakan pustaka Aspose.Cells for .NET yang canggih. Apakah Anda seorang pengembang berpengalaman atau baru memulai, panduan langkah demi langkah ini akan membekali Anda dengan pengetahuan untuk menangani file Excel secara terprogram. Siap untuk mencobanya? Mari kita mulai!

## Prasyarat
Sebelum kita masuk ke pengkodean, mari pastikan Anda memiliki semua yang dibutuhkan:

1. Lingkungan Pengembangan C#: Lingkungan kerja untuk pengembangan C#, dengan Visual Studio sangat direkomendasikan.
2.  Pustaka Aspose.Cells untuk .NET: Pastikan untuk mengintegrasikan pustaka Aspose.Cells ke dalam proyek Anda. Anda dapat dengan mudah[unduh disini](https://releases.aspose.com/cells/net/).
3. Pengetahuan Dasar tentang VBA dan Makro Excel: Keakraban dengan VBA dan cara kerja makro Excel akan meningkatkan pemahaman Anda tentang tutorial ini.
4. File Excel dengan Formulir Pengguna: Buat atau dapatkan buku kerja Excel yang berisi Formulir Pengguna (sebaiknya dengan makro yang diaktifkan, seperti`.xlsm` (berkas).

## Mengimpor Paket yang Diperlukan
Untuk memanfaatkan fungsionalitas yang disediakan oleh Aspose.Cells, sertakan namespace berikut di bagian atas file C# Anda:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Ruang nama ini akan memberi Anda akses ke berbagai alat hebat yang tertanam dalam pustaka Aspose.Cells.

## Langkah 1: Tentukan Direktori Sumber dan Output Anda
Pertama, tentukan lokasi file Anda:

```csharp
// Tentukan direktori sumber dan keluaran
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Ganti jalur placeholder dengan direktori sebenarnya tempat file Anda disimpan.

## Langkah 2: Buat Buku Kerja Target Kosong
Berikutnya, buat buku kerja baru tempat Anda akan menyalin formulir pengguna dan makro:

```csharp
// Buat buku kerja target kosong
Workbook target = new Workbook();
```

Ini menginisialisasi buku kerja kosong, yang berfungsi sebagai kanvas untuk transfer data yang akan datang.

## Langkah 3: Muat Buku Kerja Template Anda
Muat buku kerja yang berisi formulir pengguna dan makro Anda:

```csharp
// Muat file Excel yang berisi Formulir Pengguna VBA-Macro Designer
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Menyesuaikan`"sampleDesignerForm.xlsm"` ke nama berkas Anda sebenarnya.

## Langkah 4: Salin Lembar Kerja ke Buku Kerja Target
Sekarang, mari salin lembar kerja dari templat ke buku kerja target:

```csharp
// Salin semua lembar kerja templat ke buku kerja target
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Tambahkan pesan di sel A2 lembar kerja target
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Kode ini berulang melalui setiap lembar kerja dalam templat dan menyalinnya ke buku kerja target, memastikan semua data Anda ditransfer dengan lancar.

## Langkah 5: Salin Makro VBA dari Template
Berikutnya, kita akan menyalin makro VBA, termasuk modul UserForm Designer, ke buku kerja baru:

```csharp
// Salin UserForm Desainer VBA-Macro dari Template ke Target
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Salin kode modul ThisWorkbook
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Salin kode dan data modul lainnya
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Dapatkan penyimpanan desainer formulir pengguna
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Tambahkan penyimpanan desainer ke Proyek Vba target
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Kode ini memastikan bahwa tidak hanya kode tetapi juga desain formulir pengguna disalin, sehingga menjaga fungsionalitas makro Anda.

## Langkah 6: Simpan Buku Kerja Target
Setelah menyelesaikan proses penyalinan, simpan buku kerja baru Anda:

```csharp
// Simpan buku kerja target
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Ubah nama berkas keluaran sesuai kebutuhan. Langkah ini membuat buku kerja kustom Anda yang berisi makro dan formulir pengguna.

## Langkah 7: Konfirmasikan Keberhasilan
Terakhir, cetak pesan sukses ke konsol:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Kalimat sederhana ini meyakinkan Anda bahwa proses Anda berjalan lancar—konfirmasi penting atas kerja keras Anda!

## Kesimpulan
Selamat! Anda telah berhasil mempelajari cara menyalin VBA Macro User Form Designer dari satu buku kerja ke buku kerja lain menggunakan Aspose.Cells for .NET. Meskipun mungkin tampak menakutkan pada awalnya, latihan akan membuat Anda mahir dalam manipulasi buku kerja. Ingat, pengodean adalah tentang eksperimen, jadi jangan ragu untuk menjelajahi berbagai fungsi dalam file Excel Anda. Jika Anda memiliki pertanyaan atau memerlukan bantuan, forum dan dokumentasi Aspose adalah sumber daya yang sangat baik untuk mendapatkan dukungan.

## Pertanyaan yang Sering Diajukan

### Versi Excel apa yang didukung Aspose.Cells?
Aspose.Cells mendukung berbagai format Excel, termasuk XLSX, XLSM, CSV, dan banyak lagi.

### Bisakah saya menggunakan Aspose.Cells secara gratis?
 Ya! Anda dapat memulai dengan uji coba gratis untuk mengevaluasi pustaka:[Uji Coba Gratis](https://releases.aspose.com/).

### Apakah saya memerlukan Visual Studio untuk menjalankan kode ini?
Meskipun Visual Studio direkomendasikan karena fiturnya yang mudah digunakan, IDE C# apa pun yang mendukung pengembangan .NET sudah cukup.

### Di mana saya dapat menemukan lebih banyak contoh dan dokumentasi?
 Anda dapat menjelajahi[Dokumentasi Aspose.Cells](https://reference.aspose.com/cells/net/) untuk contoh lebih lanjut dan penjelasan lebih mendalam.

### Bagaimana cara mengatasi masalah saat menggunakan Aspose.Cells?
 Anda harus mengunjungi[Forum Dukungan Aspose](https://forum.aspose.com/c/cells/9) untuk bantuan dari komunitas dan staf dukungan Aspose.