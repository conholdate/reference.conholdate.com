---
title: Menguasai Ringkasan Dokumen dengan Model AI
linktitle: Menguasai Ringkasan Dokumen dengan Model AI
second_title: API Pemrosesan Dokumen Aspose.Words
description: Manfaatkan potensi otomatisasi dokumen dengan Aspose.Words untuk .NET. Pelajari cara meringkas dokumen dengan mudah menggunakan model AI tingkat lanjut.
type: docs
weight: 10
url: /id/net/tutorials/words/advanced-ai-document-processing/mastering-document-summarization-ai-model/
---
## Perkenalan

Dalam dunia yang serba cepat saat ini, kebutuhan akan manajemen dokumen yang efisien dan ekstraksi data yang cepat menjadi sangat penting. Bayangkan sebuah solusi otomatis yang meringkas dokumen panjang dalam hitungan detik. Dengan Aspose.Words untuk .NET, kita dapat mengintegrasikan kemampuan peringkasan bertenaga AI langsung ke dalam aplikasi, mengubah dokumen yang panjang menjadi ringkasan ringkas yang menghemat waktu dan meningkatkan produktivitas. Panduan ini mencakup semua langkah yang diperlukan untuk memanfaatkan Aspose.Words untuk .NET dengan model AI seperti GPT OpenAI untuk meringkas dokumen Word secara otomatis dengan kode minimal.

## Prasyarat

Untuk memulai, pastikan Anda memiliki hal-hal berikut:

1. Visual Studio: Diperlukan untuk pengodean dan pengujian. Anda dapat mengunduhnya secara gratis jika belum menginstalnya.
2. .NET Framework atau .NET Core: Aspose.Words untuk .NET mendukung keduanya, jadi pastikan Anda memiliki versi yang kompatibel.
3.  Aspose.Words untuk .NET: Unduh dan instal versi terbaru dari[Aspose merilis halaman](https://releases.aspose.com/words/net/).
4. Kunci API Model AI: Untuk membuat ringkasan, diperlukan akses ke API model AI (misalnya, OpenAI). Daftar di situs penyedia AI untuk mendapatkan kunci API.
5. Pengetahuan Dasar C#: Sedikit pengetahuan tentang pemrograman C# akan membantu Anda mengikutinya secara efektif.

Setelah Anda menyiapkan semuanya, lanjutkan dengan mengimpor paket yang diperlukan dan menginisialisasi proyek.

## Menyiapkan Lingkungan Proyek

Mari kita telusuri langkah-langkah untuk membuat dan mengonfigurasi aplikasi konsol di Visual Studio untuk melakukan ringkasan dokumen.

### Buat Aplikasi Konsol Baru

1. Buka Visual Studio.
2. Pilih “Buat proyek baru.”
3. Pilih “Aplikasi Konsol (.NET Framework)” atau “Aplikasi Konsol (.NET Core)” tergantung pada pengaturan Anda.
4. Beri nama proyek Anda dan pilih lokasi penyimpanan.

### Instal Aspose.Words dan Paket Model AI

Untuk mengaktifkan fungsionalitas Aspose.Words, tambahkan melalui manajer paket NuGet.

1. Klik kanan pada proyek Anda di Solution Explorer, dan pilih Kelola Paket NuGet.
2.  Pencarian untuk`Aspose.Words`dan klik Instal.
3. Jika diperlukan, instal juga paket model AI spesifik untuk integrasi (misalnya, OpenAI).

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Setelah lingkungan diatur, mari beralih ke pengaturan ringkasan dokumen.

Kami akan memandu Anda dalam menyiapkan direktori dokumen, memuat file, mengonfigurasi model AI, dan melakukan peringkasan dokumen tunggal dan multi-dokumen.

## Langkah 1: Tentukan Direktori Dokumen

Tentukan direktori untuk menyimpan dokumen masukan dan menyimpan keluaran yang diringkas.

```csharp
// Tentukan direktori dokumen dan keluaran
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

 Mengganti`YOUR_DOCUMENT_DIRECTORY` Dan`YOUR_ARTIFACTS_DIRECTORY` dengan jalur untuk direktori input dan output.

## Langkah 2: Muat Dokumen untuk Diringkas

Masukkan dokumen Word yang akan diringkas ke dalam program. Berikut cara melakukannya:

```csharp
Document firstDoc = new Document(MyDir + "BigDocument.docx");
Document secondDoc = new Document(MyDir + "AdditionalDocument.docx");
```

 Contoh ini mengasumsikan Anda memiliki dua dokumen yang disimpan sebagai`BigDocument.docx` Dan`AdditionalDocument.docx`Sesuaikan sesuai kebutuhan berdasarkan nama file Anda.

## Langkah 3: Inisialisasi dan Konfigurasikan Model AI

Dengan menggunakan kunci API, kami akan menginisialisasi model AI untuk peringkasan.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

Simpan kunci API dengan aman dalam variabel lingkungan Anda untuk menjaganya tetap terlindungi.

## Langkah 4: Hasilkan Ringkasan untuk Satu Dokumen

Merangkum satu dokumen saja sudah mudah. Tentukan panjang ringkasan yang diinginkan dan simpan hasilnya ke direktori yang Anda tentukan.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "SingleDocumentSummary.docx");
```

 Kode ini merangkum`firstDoc` mendokumentasikan dan menyimpan ringkasan sebagai`SingleDocumentSummary.docx`.

## Langkah 5: Hasilkan Ringkasan untuk Beberapa Dokumen

Untuk meringkas beberapa dokumen sekaligus, muat dokumen tersebut sebagai koleksi dan tentukan opsi ringkasan.

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "MultiDocumentSummary.docx");
```

 Pendekatan ini memungkinkan meringkas dua dokumen secara bersamaan. Output akan disimpan sebagai`MultiDocumentSummary.docx`.

## Kesimpulan

Dengan Aspose.Words untuk .NET dan model yang didukung AI, meringkas dokumen besar menjadi tugas yang mudah. Mengintegrasikan fitur ini ke dalam aplikasi Anda akan menyederhanakan penanganan dokumen, menyediakan ringkasan yang ringkas dan akurat bagi pengguna. Pengaturan ini dapat secara drastis mengurangi waktu yang dihabiskan untuk membaca file yang panjang, baik dalam proyek bisnis, pendidikan, atau pribadi.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka lengkap untuk mengelola dokumen Word. Pustaka ini memungkinkan pengguna membuat, mengedit, mengonversi, dan merender file Word secara terprogram dengan mudah.

### Bagaimana Cara Mendapatkan Kunci API untuk Model AI?
Untuk mengakses layanan model AI, daftarlah dengan penyedia seperti OpenAI atau Google, dan ikuti petunjuk mereka untuk membuat kunci API.

### Bisakah Aspose.Words Merangkum Dokumen Tanpa AI?
Aspose.Words sendiri tidak melakukan peringkasan berbasis AI. Ia memerlukan integrasi dengan model AI eksternal untuk kemampuan peringkasan.

### Apakah Ada Uji Coba Gratis Aspose.Words?
Ya, Aspose menawarkan uji coba gratis, yang dapat diunduh dari situs web mereka.

### Di mana saya dapat menemukan lebih banyak sumber daya untuk Aspose.Words?
 Itu[Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/) menyediakan sumber daya dan contoh yang mendalam.