---
title: Menguasai Ringkasan Dokumen Model AI Google
linktitle: Menguasai Ringkasan Dokumen Model AI Google
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari langkah demi langkah cara meringkas dokumen Word dengan Aspose.Words dan Google AI dalam .NET. Ikuti panduan ini untuk menyederhanakan ekstraksi konten, wawasan dokumen, dan otomatisasi.
type: docs
weight: 10
url: /id/net/tutorials/words/advanced-ai-document-processing/mastering-document-summarization-google-ai-model/
---
## Perkenalan

Memperlancar informasi dari dokumen besar tidak pernah semudah ini. Panduan ini membahas cara memanfaatkan Aspose.Words untuk .NET dan model AI Google untuk meringkas dokumen Word secara akurat dan efisien. Apakah Anda perlu membuat ringkasan singkat untuk laporan, mengekstrak wawasan utama dari penelitian, atau memproses beberapa dokumen, tutorial komprehensif ini akan memandu Anda melalui setiap langkah.

## Prasyarat

Untuk memulai, pastikan Anda memiliki hal berikut:

1. Kemampuan dalam C# dan .NET: Pemahaman dasar tentang C# dan .NET akan membantu Anda memahami kode dan konsep secara lebih efektif.
2.  Aspose.Words untuk .NET: Pustaka canggih ini menyediakan alat untuk membuat, mengedit, dan mengelola dokumen Word dalam aplikasi .NET. Unduh[Di Sini](https://releases.aspose.com/words/net/).
3. Kunci API untuk Google AI: Kunci API diperlukan untuk mengautentikasi permintaan ke model AI Google. Simpan kunci ini dengan aman di variabel lingkungan Anda.
4. Lingkungan Pengembangan: IDE yang kompatibel dengan .NET, seperti Visual Studio, diperlukan untuk membangun dan menjalankan aplikasi.
5. Contoh Dokumen Word: Pastikan Anda telah menyiapkan contoh dokumen Word (misalnya, "Dokumen besar.docx", "Dokumen.docx") untuk menguji fungsionalitas ringkasan.

## Impor Ruang Nama yang Diperlukan

Mulailah dengan mengimpor namespace yang diperlukan untuk mengintegrasikan Aspose.Words dengan Google AI.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.AI;
```

Dengan paket-paket ini, Anda siap untuk mulai meringkas dokumen.

## Langkah 1: Siapkan Jalur Direktori

Mulailah dengan menentukan jalur file untuk dokumen masukan Anda dan tempat Anda ingin menyimpan dokumen ringkasan.

```csharp
// Direktori untuk dokumen sumber
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Direktori untuk menyimpan artefak keluaran
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

 Mengganti`"YOUR_DOCUMENT_DIRECTORY"` Dan`"YOUR_ARTIFACTS_DIRECTORY"` dengan jalur aktual pada sistem Anda. Direktori ini akan berfungsi sebagai referensi untuk memuat dan menyimpan dokumen.

## Langkah 2: Muat Dokumen Word

 Selanjutnya, muat dokumen yang ingin Anda rangkum menggunakan`Document` kelas dari Aspose.Words.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

 Pastikan nama file sesuai dengan dokumen di direktori yang Anda tentukan.`Document` kelas memungkinkan Anda memuat dokumen Word ke dalam memori untuk diproses.

## Langkah 3: Ambil Kunci API Google Anda

Untuk mengakses model AI Google, ambil kunci API dengan aman dari variabel lingkungan Anda.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Dengan menyimpan kunci API Anda sebagai variabel lingkungan, Anda mengurangi risiko terungkapnya informasi sensitif dalam kode Anda.

## Langkah 4: Siapkan Instansi Model AI

Konfigurasikan model AI dengan membuat contoh menggunakan model GPT-4 Mini. Model ini menyediakan kemampuan meringkas dokumen secara efisien.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

 Mengacu kepada[Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/) untuk rincian tambahan tentang pemilihan dan konfigurasi model.

## Langkah 5: Ringkaslah Satu Dokumen

 Untuk membuat ringkasan dari satu dokumen, gunakan`Summarize` metode yang disediakan oleh contoh model. Tentukan panjang ringkasan yang diinginkan, dalam hal ini, ringkasan singkat.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

Kode ini membuat versi ringkasan dari`firstDoc` dan menyimpannya di direktori artifak. Sesuaikan panjang ringkasan sesuai kebutuhan Anda, baik pendek, sedang, atau panjang.

## Langkah 6: Merangkum Beberapa Dokumen Secara Bersamaan

 Untuk skenario di mana Anda ingin meringkas beberapa dokumen sekaligus, berikan array dokumen ke`Summarize` metode.

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

 Pendekatan ini menghasilkan ringkasan komprehensif yang mengintegrasikan konten dari keduanya`firstDoc` Dan`secondDoc`, memberikan gambaran yang lebih luas dalam satu dokumen ringkasan.

## Kesimpulan

Dengan tutorial ini, Anda akan mampu meringkas dokumen secara efektif menggunakan Aspose.Words untuk model .NET dan Google AI. Mulai dari menentukan direktori dokumen dan memuat file hingga mengambil kunci API dan menyiapkan instans model, setiap langkah memastikan Anda dapat menangani teks dalam jumlah besar secara efisien dan membuat ringkasan singkat hanya dalam beberapa baris kode.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?

Aspose.Words untuk .NET adalah pustaka serbaguna untuk membuat, mengedit, dan mengonversi dokumen Word dalam aplikasi .NET, yang menawarkan kemampuan otomatisasi dokumen tingkat lanjut.

### Bagaimana cara memperoleh kunci Google API untuk peringkasan AI?

Untuk menggunakan layanan AI Google, daftar di Google Cloud, aktifkan layanan API yang relevan, dan amankan kunci API Anda.

### Bisakah saya meringkas beberapa dokumen sekaligus?

Ya, Aspose.Words memungkinkan Anda meneruskan beberapa dokumen ke model AI, menghasilkan ringkasan komprehensif dari berbagai sumber.

### Bagaimana cara mengontrol panjang ringkasan?

 Gunakan`SummaryLength` pilihan dalam`SummarizeOptions` kelas untuk menetapkan panjang ringkasan yang diinginkan sebagai pendek, sedang, atau panjang.

### Di mana saya dapat menemukan sumber daya tambahan untuk Aspose.Words?

 Untuk contoh dan detail teknis lebih lanjut, lihat[Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/).