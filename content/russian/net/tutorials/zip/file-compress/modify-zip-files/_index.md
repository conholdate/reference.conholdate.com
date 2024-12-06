---
title: Изменение ZIP-файлов с помощью Aspose.Zip для .NET
linktitle: Изменить ZIP-файлы
second_title: API Aspose.Zip .NET для сжатия и архивации файлов
description: Узнайте, как эффективно извлекать, удалять и добавлять записи в zip-файлы программным способом, расширяя возможности манипулирования файлами.
type: docs
weight: 15
url: /ru/net/tutorials/zip/file-compress/modify-zip-files/
---
## Введение

Zip-файлы жизненно важны для организации и сжатия данных, но как изменить их содержимое программно? Решение заключается в Aspose.Zip для .NET, надежной библиотеке, которая упрощает манипуляции с zip-файлами с помощью C#. В этом руководстве мы шаг за шагом проведем вас через извлечение, удаление и добавление записей в zip-файлы.

## Предпосылки

Прежде чем приступить к работе, убедитесь, что у вас есть следующее:

1.  Aspose.Zip for .NET Library: Установите библиотеку в свой проект. Вы можете скачать ее[здесь](https://releases.aspose.com/zip/net/).
   
2.  Каталог документов: Настройте каталог для хранения ваших zip-файлов. Заменить`"Your Document Directory"` в коде с вашим реальным путем.

## Импорт необходимых пространств имен

Начните с импорта необходимых пространств имен:

```csharp
using Aspose.Zip;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```

## Шаг 1: Откройте внешний ZIP-файл

Начните с открытия основного zip-файла (внешнего zip-файла):

```csharp
string dataDir = "Your Data Directory";
using (Archive outer = new Archive(dataDir + "outer.zip"))
{
    // Продолжайте определять внутренние почтовые индексы.
}
```

## Шаг 2: Определите внутренние почтовые индексы

Далее определите и подготовьтесь к удалению всех внутренних zip-файлов:

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
            
            // Извлечь внутренние записи
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

## Шаг 3: Удалить записи внутреннего архива

Собрав необходимые записи, удалите внутренние записи zip-архива:

```csharp
foreach (ArchiveEntry e in entriesToDelete)
{
    outer.DeleteEntry(e);
}
```

## Шаг 4: Добавьте измененные записи во внешний почтовый индекс

Теперь вы можете добавить вновь извлеченные записи обратно во внешний zip-файл:

```csharp
for (int i = 0; i < namesToInsert.Count; i++)
{
    outer.CreateEntry(namesToInsert[i], contentToInsert[i]);
}
```

## Шаг 5: Сохраните измененный ZIP-файл

Наконец, сохраните изменения в новом zip-файле:

```csharp
outer.Save(dataDir + "flatten.zip");
```

## Заключение

Aspose.Zip для .NET предоставляет мощный и простой способ программной обработки zip-файлов. В этом руководстве рассматривается извлечение, удаление и добавление записей в zip-файл, что демонстрирует универсальность библиотеки. Исследуйте различные сценарии и улучшите свои навыки обработки файлов!

## Часто задаваемые вопросы

### Могу ли я использовать Aspose.Zip для .NET с другими языками программирования?
Aspose.Zip в первую очередь предназначен для приложений .NET, но Aspose предлагает аналогичные библиотеки для различных языков программирования.

### Существует ли бесплатная пробная версия Aspose.Zip для .NET?
 Да, бесплатная пробная версия доступна для загрузки.[здесь](https://releases.aspose.com/).

### Как получить поддержку Aspose.Zip для .NET?
 Посетите[Форум Aspose.Zip](https://forum.aspose.com/c/zip/37) за поддержку и обсуждения.

### Могу ли я приобрести временную лицензию на Aspose.Zip для .NET?
Да, вы можете получить временную лицензию.[здесь](https://purchase.conholdate.com/temporary-license/).

### Где я могу найти документацию по Aspose.Zip для .NET?
 Полная документация доступна[здесь](https://reference.aspose.com/zip/net/).