---
title: Penyaringan Tugas DAN Operasi di Aspose.Tasks
linktitle: Penyaringan Tugas DAN Operasi di Aspose.Tasks
second_title: Aspose.Tasks .NET API
description: Pelajari cara memanfaatkan kelas di Aspose.Tasks for .NET untuk memfilter tugas proyek berdasarkan beberapa kondisi. Dengan menggabungkan kriteria seperti tugas ringkasan dan atribut bukan nol.
type: docs
weight: 10
url: /id/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## Perkenalan

Dalam tutorial ini, kita akan menjelajahi cara melakukan penyaringan lanjutan tugas proyek di Aspose.Tasks untuk .NET dengan memanfaatkan`Util.And` kelas. Fitur canggih ini memungkinkan pengembang untuk memfilter tugas berdasarkan beberapa kriteria secara efisien.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Pengetahuan dasar pemrograman C#.
2.  Aspose.Tasks untuk .NET terinstal. Jika Anda belum melakukannya, Anda dapat mengunduhnya dari[tautan ini](https://releases.aspose.com/tasks/net/).
3. Lingkungan pengembangan terpadu (IDE) seperti Visual Studio untuk menulis dan menjalankan kode.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan ke dalam proyek C# Anda. Ini akan memungkinkan Anda untuk mengakses fungsionalitas yang disediakan oleh Aspose.Tasks.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## Langkah 1: Inisialisasi Proyek dan Kumpulkan Tugas

 Pertama, inisialisasikan proyek Aspose.Tasks dan kumpulkan semua tugas di dalamnya. Untuk tujuan demonstrasi, kami akan menganggap ada file proyek bernama`Project2.mpp`.

```csharp
// Jalur ke direktori dokumen
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// Kumpulkan semua tugas anak
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## Langkah 2: Tentukan Kondisi Filter

Pada langkah ini, kita akan menentukan kondisi untuk memfilter tugas. Dalam contoh kita, kita akan membuat dua kondisi: satu untuk memfilter tugas ringkasan dan satu lagi untuk memastikan bahwa tugas tidak kosong.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## Langkah 3: Gabungkan Kondisi dengan Operasi AND

 Langkah selanjutnya adalah menggabungkan kondisi-kondisi ini menggunakan`Util.And` kelas. Hal ini memungkinkan kita untuk membuat kondisi gabungan yang mewajibkan kedua kriteria tersebut.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## Langkah 4: Terapkan Tugas Kondisi dan Filter Gabungan

Sekarang, mari terapkan kondisi gabungan ke tugas-tugas yang dikumpulkan untuk menyaring tugas-tugas spesifik yang memenuhi kedua kondisi tersebut.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## Langkah 5: Keluarkan Tugas yang Difilter

Terakhir, kami akan mengulangi tugas-tugas yang telah kami filter dan menampilkan detail yang relevan. Ini akan membantu kami memahami tugas-tugas yang memenuhi kriteria kami.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## Kesimpulan

 Dalam tutorial ini, kami menunjukkan cara melakukan operasi penyaringan lanjutan di Aspose.Tasks untuk .NET menggunakan`Util.And`kelas. Dengan menggabungkan beberapa kondisi, kita dapat memfilter tugas secara efektif, sehingga meningkatkan kegunaan aplikasi manajemen proyek kita.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Tasks untuk .NET?

Aspose.Tasks untuk .NET adalah API komprehensif yang dirancang bagi pengembang untuk memanipulasi file Microsoft Project secara terprogram dalam aplikasi .NET.

### Bisakah saya menggabungkan lebih dari dua kondisi menggunakan Util.And?

 Ya! Itu`Util.And` kelas memungkinkan Anda menggabungkan beberapa kondisi, mengaktifkan logika penyaringan kompleks yang disesuaikan dengan kebutuhan Anda.

### Apakah ada versi uji coba gratis yang tersedia untuk Aspose.Tasks?

 Ya, Anda dapat mengunduh versi uji coba gratis dari[tautan ini](https://releases.aspose.com/).

### Di mana saya dapat menemukan dokumentasi terperinci untuk Aspose.Tasks?

 Dokumentasi terperinci tersedia[Di Sini](https://reference.aspose.com/tasks/net/).

### Bagaimana saya bisa mencari dukungan untuk Aspose.Tasks?

 Dukungan tersedia melalui forum komunitas Aspose.Tasks, yang dapat diakses[Di Sini](https://forum.aspose.com/c/tasks/15).