---
title: Ubah File Zip dengan Aspose.Zip untuk .NET
linktitle: Memodifikasi File Zip
second_title: Aspose.Zip .NET API untuk Kompresi & Pengarsipan File
description: Pelajari cara mengekstrak, menghapus, dan menambahkan entri ke file zip secara terprogram secara efisien, meningkatkan kemampuan manipulasi file Anda.
type: docs
weight: 15
url: /id/net/tutorials/zip/file-compress/modify-zip-files/
---
## Perkenalan

File zip sangat penting untuk pengorganisasian dan kompresi data, tetapi bagaimana Anda memodifikasi kontennya secara terprogram? Solusinya ada di Aspose.Zip untuk .NET, pustaka tangguh yang menyederhanakan manipulasi file zip dengan C#. Dalam tutorial ini, kami akan memandu Anda mengekstrak, menghapus, dan menambahkan entri ke file zip langkah demi langkah.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1.  Aspose.Zip untuk Pustaka .NET: Instal pustaka di proyek Anda. Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/zip/net/).
   
2.  Direktori Dokumen: Siapkan direktori untuk menyimpan file zip Anda. Ganti`"Your Document Directory"` dalam kode dengan jalur Anda yang sebenarnya.

## Impor Ruang Nama yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan:

```csharp
using Aspose.Zip;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```

## Langkah 1: Buka File Zip Luar

Mulailah dengan membuka file zip utama Anda (zip luar):

```csharp
string dataDir = "Your Data Directory";
using (Archive outer = new Archive(dataDir + "outer.zip"))
{
    // Lanjutkan untuk mengidentifikasi entri zip bagian dalam
}
```

## Langkah 2: Identifikasi Entri Zip Dalam

Berikutnya, identifikasi dan persiapkan untuk menghapus file zip internal apa pun:

```csharp
List<ArchiveEntry> entriesToDelete = new List<ArchiveEntry>();
List<string> namesToInsert = new List<string>();
List<MemoryStream> contentToInsert = new List<MemoryStream>();

foreach (ArchiveEntry entry in outer.Entries)
{
    if (entry.Name.EndsWith(".zip", StringComparison.InvariantCultureIgnoreCase))
    {
        entriesToDelete.Add(entry);
        
        using (MemoryStream innerCompressed = new MemoryStream())
        {
            entry.Open().CopyTo(innerCompressed);
            
            // Ekstrak entri internal
            using (Archive inner = new Archive(innerCompressed))
            {
                foreach (ArchiveEntry ie in inner.Entries)
                {
                    namesToInsert.Add(ie.Name);
                    MemoryStream content = new MemoryStream();
                    ie.Open().CopyTo(content);
                    contentToInsert.Add(content);
                }
            }
        }
    }
}
```

## Langkah 3: Hapus Entri Arsip Internal

Setelah Anda mengumpulkan entri yang Anda perlukan, hapus entri zip bagian dalam:

```csharp
foreach (ArchiveEntry e in entriesToDelete)
{
    outer.DeleteEntry(e);
}
```

## Langkah 4: Tambahkan Entri yang Dimodifikasi ke Zip Luar

Sekarang, Anda dapat menambahkan kembali entri yang baru diekstrak ke dalam file zip luar Anda:

```csharp
for (int i = 0; i < namesToInsert.Count; i++)
{
    outer.CreateEntry(namesToInsert[i], contentToInsert[i]);
}
```

## Langkah 5: Simpan File Zip yang Dimodifikasi

Terakhir, simpan perubahan Anda ke file zip baru:

```csharp
outer.Save(dataDir + "flatten.zip");
```

## Kesimpulan

Aspose.Zip untuk .NET menyediakan cara yang ampuh dan mudah untuk memanipulasi file zip secara terprogram. Tutorial ini mencakup cara mengekstrak, menghapus, dan menambahkan entri ke file zip, yang mengilustrasikan fleksibilitas pustaka. Jelajahi berbagai skenario, dan tingkatkan keterampilan manipulasi file Anda!

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan Aspose.Zip untuk .NET dengan bahasa pemrograman lain?
Aspose.Zip terutama dirancang untuk aplikasi .NET, tetapi Aspose menawarkan pustaka serupa untuk berbagai bahasa pemrograman.

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Zip untuk .NET?
 Ya, uji coba gratis tersedia untuk diunduh[Di Sini](https://releases.aspose.com/).

### Bagaimana cara mendapatkan dukungan untuk Aspose.Zip untuk .NET?
 Kunjungi[Forum Aspose.Zip](https://forum.aspose.com/c/zip/37) untuk dukungan dan diskusi.

### Bisakah saya membeli lisensi sementara untuk Aspose.Zip untuk .NET?
Ya, Anda bisa mendapatkan lisensi sementara[Di Sini](https://purchase.conholdate.com/temporary-license/).

### Di mana saya dapat menemukan dokumentasi untuk Aspose.Zip untuk .NET?
 Dokumentasi lengkap tersedia[Di Sini](https://reference.aspose.com/zip/net/).