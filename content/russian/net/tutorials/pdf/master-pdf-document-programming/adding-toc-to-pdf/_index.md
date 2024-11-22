---
title: Добавление оглавления в PDF-документ
linktitle: Добавление оглавления в PDF-документ
second_title: Справочник по API Aspose.PDF для .NET
description: В этом руководстве показано, как добавить оглавление (TOC) в PDF-документ с помощью Aspose.Pdf для .NET.
type: docs
weight: 40
url: /ru/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Введение

Создание оглавления (TOC) в документе PDF может значительно улучшить его навигацию и доступность. В этом руководстве мы покажем, как добавить TOC в файл PDF с помощью Aspose.Pdf для .NET.

## Предпосылки

Перед началом убедитесь, что у вас есть следующее:

1.   Aspose.PDF для .NET: Загрузите и установите последнюю версию с сайта[здесь](https://releases.aspose.com/pdf/net/).
2.  Среда разработки: настройте среду разработки .NET, например Visual Studio.
3.   Лицензия: При необходимости запросите временную лицензию; посетите[Страница лицензирования Aspose.Pdf](https://asposepdf.com/developers) для получения более подробной информации.

Импорт необходимых библиотек

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Шаг 1: Загрузите PDF-документ

Загрузите существующий файл PDF, в который вы хотите добавить оглавление. Укажите путь к каталогу вашего документа.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Шаг 2: Вставьте новую страницу для оглавления

Вставьте новую страницу в начало документа PDF. Эта страница будет служить оглавлением (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Шаг 3: Создайте информационный объект TOC

Создайте объект, который будет представлять информацию TOC. Добавьте заголовок и ссылку на него для лучшей навигации.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Шаг 4: Определите элементы TOC

Определите элементы (или заголовки), которые будут отображаться в TOC. Эти элементы могут помочь читателям перейти к определенным разделам документа.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Шаг 5: Создание заголовков оглавления

Создайте заголовки для первых двух элементов в TOC. Эти заголовки будут ссылаться на соответствующие им страницы.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Шаг 6: Сохраните PDF-файл с оглавлением

Наконец, сохраните обновленный PDF-файл.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Подтверждающее сообщение

Отобразите подтверждающее сообщение, чтобы сообщить пользователю, что процесс завершен.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Заключение

С Aspose.PDF для .NET добавление оглавления в PDF не только просто, но и настраиваемо. Если вам нужно создать простые навигационные ссылки или сложные структуры, этот инструмент вам поможет. Так что в следующий раз, когда вы будете работать с длинным PDF, не забудьте добавить TOC для профессионального штриха.

## Часто задаваемые вопросы

### Могу ли я настроить внешний вид оглавления в Aspose.PDF?

Да, вы можете полностью настроить внешний вид оглавления, включая стиль шрифта, размер и выравнивание.

### Как добавить подзаголовки в оглавление?

 Вы можете добавлять подзаголовки, настраивая`Heading` уровень (например,`Heading(2)`).

### Возможно ли автоматически обновлять оглавление при изменении документа?

Нет, TOC не обновится автоматически. Вам придется создать его заново, если структура документа изменится.

### Могу ли я связать записи TOC с внешними документами?

Да, вы можете использовать гиперссылки для привязки записей оглавления к внешним PDF-файлам или URL-адресам.

### Поддерживает ли Aspose.PDF многоуровневые оглавления?

Да, Aspose.PDF поддерживает многоуровневые оглавления для сложных документов с подразделами.
