---
title: Bidang Formulir Kotak Kombo HTML dengan Jenis Kontrol Pilihan
linktitle: Bidang Formulir Kotak Kombo HTML dengan Jenis Kontrol Pilihan
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyisipkan kolom formulir kotak kombo ke dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah ini mencakup opsi pemuatan HTML, jenis kontrol yang disukai, dan kiat penyesuaian tingkat lanjut untuk otomatisasi dokumen yang lancar.
type: docs
weight: 10
url: /id/net/tutorials/words/use-htmlloadoptions/html-combo-box-form-fields-with-preferred-control-types/
---
## Perkenalan

Dalam dunia dinamis otomatisasi dokumen, mengintegrasikan konten HTML dengan lancar ke dalam dokumen Word merupakan tantangan yang sering terjadi. Dengan menggunakan Aspose.Words untuk .NET, kita dapat memanipulasi HTML dengan presisi dan merendernya ke dalam dokumen Word. Panduan ini membahas cara menggunakan opsi pemuatan HTML untuk mengontrol cara bidang formulir kotak kombo disisipkan, memastikan rendering dan fungsionalitas yang presisi.

## Prasyarat

Sebelum melanjutkan, pastikan Anda telah menyiapkan hal-hal berikut:

-  Aspose.Words untuk Pustaka .NET: Unduh dari[situs web](https://releases.aspose.com/words/net/). 
- Lingkungan Pengembangan: Siapkan Visual Studio atau IDE yang setara.  
- Pengetahuan Pemrograman C#: Pemahaman praktis tentang C#.  
- Dasar-dasar HTML: Keakraban dengan struktur HTML, terutama kontrol formulir.  

## Mengimpor Ruang Nama Penting

Mulailah dengan mengimpor namespace yang diperlukan:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

Ruang nama ini menyediakan alat yang dibutuhkan untuk bekerja dengan dokumen dan memanipulasi konten HTML secara efisien.

## Langkah 1: Tentukan Konten HTML

Siapkan cuplikan HTML yang berisi kolom formulir kotak kombo yang ingin Anda masukkan. Berikut contohnya:

```csharp
const string html = @"
    <html>
        <select name='ComboBox' size='1'>
            <option value='val1'>Option 1</option>
            <option value='val2'>Option 2</option>
        </select>
    </html>";
```

Kode ini menciptakan kotak kombo sederhana dengan dua opsi yang dapat dipilih.

## Langkah 2: Tentukan Direktori Dokumen

Identifikasi dan tentukan jalur direktori tempat dokumen akan disimpan. Penggunaan direktori terpusat menyederhanakan pengelolaan berkas.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

 Mengganti`"YOUR_DOCUMENT_DIRECTORY"` dengan jalur folder sebenarnya pada sistem Anda.

## Langkah 3: Konfigurasikan Opsi Pemuatan HTML

 Itu`HtmlLoadOptions` class di Aspose.Words memungkinkan kita menentukan bagaimana konten HTML harus ditafsirkan. Untuk memastikan kotak kombo ditampilkan sebagai tag dokumen terstruktur:

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions
{
    PreferredControlType = HtmlControlType.StructuredDocumentTag
};
```

Ini memastikan kotak kombo muncul sebagai bidang formulir interaktif dalam dokumen Word.

## Langkah 4: Muat HTML ke dalam Dokumen Word

 Ubah string HTML menjadi aliran byte dan muat ke dalam`Document` objek. Pendekatan ini memastikan penguraian dan rendering HTML yang akurat.

```csharp
Document doc = new Document(
    new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

 Di Sini,`MemoryStream` digunakan untuk menangani konten HTML dalam memori, mengurangi overhead I/O file.

## Langkah 5: Simpan Dokumen Word

Terakhir, simpan dokumen Word ke direktori yang ditentukan dalam format yang Anda inginkan, seperti DOCX:

```csharp
doc.Save(dataDir + "ComboBoxFormField.docx", SaveFormat.Docx);
```

Ini menghasilkan berkas Word yang berisi bidang formulir kotak kombo yang ditampilkan dengan benar.

## Kesimpulan

 Menggabungkan konten HTML, terutama bidang formulir seperti kotak kombo, ke dalam dokumen Word menggunakan Aspose.Words untuk .NET mudah dilakukan saat memanfaatkan`HtmlLoadOptions`Panduan ini membekali Anda dengan pengetahuan untuk mengontrol bagaimana elemen-elemen ini ditampilkan, memastikan dokumen Anda memenuhi persyaratan pengguna dan proyek.

## Pertanyaan yang Sering Diajukan

###  Apa`HtmlControlType` in Aspose.Words for .NET?
`HtmlControlType` menentukan bagaimana kontrol formulir HTML ditampilkan dalam dokumen Word. Pilihannya meliputi`StructuredDocumentTag`, `InlineText`, dan lainnya.

### Bisakah saya menyesuaikan kotak kombo setelah rendering?
Ya, Anda dapat memanipulasi kotak kombo menggunakan API Aspose.Words, seperti menambahkan opsi baru atau mengubah properti.

### Apakah Aspose.Words mendukung elemen HTML tingkat lanjut?
Ya, Aspose.Words menyediakan dukungan yang kuat untuk HTML, termasuk tabel, formulir, multimedia, dan gaya yang kompleks.

### Di mana saya dapat menemukan sumber daya tambahan?
 Kunjungi[Dokumentasi Aspose.Words untuk .NET](https://reference.aspose.com/words/net/) untuk contoh terperinci dan referensi API.

### Apakah uji coba gratis tersedia?
 Ya kamu bisa[unduh uji coba gratis](https://releases.aspose.com/) untuk menjelajahi Aspose.Words untuk .NET.