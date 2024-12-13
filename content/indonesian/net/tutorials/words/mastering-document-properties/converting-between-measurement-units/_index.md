---
title: Konversi Antar Satuan Pengukuran
linktitle: Konversi Antar Satuan Pengukuran
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengelola margin, header, dan footer secara efektif dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan terperinci ini memandu Anda mengonversi satuan pengukuran.
type: docs
weight: 10
url: /id/net/tutorials/words/mastering-document-properties/converting-between-measurement-units/
---
## Perkenalan

Halo, para pengembang! Jika Anda bekerja dengan dokumen Word menggunakan Aspose.Words for .NET, Anda mungkin sering perlu mengatur margin, header, atau footer dalam berbagai satuan ukuran. Mengonversi antara satuan seperti inci dan poin dapat menjadi tantangan jika Anda tidak familier dengan fungsi pustaka tersebut. Dalam tutorial ini, kami akan memandu Anda melalui proses mengonversi satuan ukuran dan menyesuaikan tata letak dokumen Anda dengan mudah. Mari kita mulai!

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

1.  Pustaka Aspose.Words untuk .NET: Unduh[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Gunakan Visual Studio atau IDE lain yang kompatibel dengan .NET.
3. Pengetahuan Dasar C#: Keakraban dengan C# akan membantu Anda mengikutinya dengan lancar.
4.  Lisensi Aspose: Opsional, tetapi direkomendasikan untuk fungsionalitas penuh. Dapatkan lisensi sementara[Di Sini](https://purchase.aspose.com/temporary-license/).

## Mengimpor Ruang Nama

Untuk memulai, impor namespace yang diperlukan untuk mengakses kelas dan metode Aspose.Words:

```csharp
using Aspose.Words;
using Aspose.Words.Layout;
```

## Langkah 1: Buat Dokumen Baru

Mulailah dengan membuat dokumen baru menggunakan Aspose.Words. Ini akan menginisialisasi ruang kerja Anda untuk pembuatan konten.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Akses Pengaturan Halaman

 Selanjutnya, akses`PageSetup`objek untuk mengonfigurasi margin, header, dan footer:

```csharp
PageSetup pageSetup = builder.PageSetup;
```

Ini memungkinkan Anda untuk memanipulasi berbagai properti pengaturan halaman, termasuk margin dan jarak.

## Langkah 3: Ubah Inci ke Poin

 Aspose.Words menggunakan poin sebagai ukuran default. Untuk mengatur margin dalam inci, gunakan`ConvertUtil.InchToPoint` metode untuk konversi:

```csharp
pageSetup.TopMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.BottomMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.LeftMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.RightMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.HeaderDistance = ConvertUtil.InchToPoint(0.2);
pageSetup.FooterDistance = ConvertUtil.InchToPoint(0.2);
```

- Margin Atas dan Bawah: Atur masing-masing menjadi 1 inci.
- Margin Kiri dan Kanan: Masing-masing diatur ke 1,5 inci.
- Jarak Header dan Footer: Atur masing-masing menjadi 0,2 inci.

## Langkah 4: Simpan Dokumen

Setelah Anda mengonfigurasi dokumen Anda, simpan untuk menerapkan semua perubahan:

```csharp
doc.Save("ConvertedDocument.docx");
```

Ini menyimpan dokumen Anda dengan margin dan jarak yang ditentukan dalam poin.

## Kesimpulan

Selamat! Anda telah berhasil mengonversi dan mengatur margin dan jarak dalam dokumen Word menggunakan Aspose.Words untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat dengan mudah menangani konversi unit, yang akan meningkatkan proses kustomisasi dokumen Anda. Jelajahi berbagai pengaturan dan fungsionalitas ekstensif yang ditawarkan Aspose.Words.

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengonversi satuan lain seperti sentimeter ke poin menggunakan Aspose.Words?
 Ya, Aspose.Words menyediakan metode seperti`ConvertUtil.CmToPoint` untuk mengonversi sentimeter ke poin.

### Apakah lisensi diperlukan untuk menggunakan Aspose.Words untuk .NET?
Meskipun Anda dapat menggunakan Aspose.Words tanpa lisensi, beberapa fitur lanjutan mungkin dibatasi. Memperoleh lisensi memastikan fungsionalitas penuh.

### Bagaimana cara menginstal Aspose.Words untuk .NET?
 Unduh dari[situs web](https://releases.aspose.com/words/net/) dan ikuti petunjuk instalasi yang disediakan.

### Dapatkah saya menetapkan unit yang berbeda untuk bagian yang berbeda dalam suatu dokumen?
 Tentu saja! Anda dapat menyesuaikan margin dan pengaturan untuk bagian yang berbeda menggunakan`Section`kelas.

### Fitur apa lagi yang ditawarkan Aspose.Words?
 Aspose.Words mendukung berbagai fitur, termasuk konversi dokumen, gabungan surat, dan opsi pemformatan yang luas. Periksa[dokumentasi](https://reference.aspose.com/words/net/) untuk lebih jelasnya.
