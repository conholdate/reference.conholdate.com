---
title: Отслеживайте ход преобразования электронной почты с помощью Aspose.Email для .NET
linktitle: Отслеживайте ход преобразования электронной почты с помощью Aspose.Email для .NET
second_title: API обработки электронной почты Aspose.Email .NET
description: Узнайте пошагово, как отслеживать прогресс преобразования электронной почты в C# с помощью Aspose.Email для .NET. Повысьте эффективность своего проекта с помощью этого подробного руководства.
type: docs
weight: 12
url: /ru/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## Введение

Эффективное управление документами электронной почты часто подразумевает отслеживание хода их преобразования. Aspose.Email for .NET предоставляет надежные инструменты для достижения этой цели, позволяя разработчикам беспрепятственно обрабатывать операции с электронной почтой. В этом руководстве подробно рассматривается, как можно отслеживать ход преобразования документов электронной почты в C#, с пошаговым разбором процесса для простоты понимания.  

## Предпосылки  

Прежде чем приступить к обучению, давайте убедимся, что у вас все настроено:  

1.  Aspose.Email для .NET: загрузите и установите[Aspose.Email для .NET](https://releases.aspose.com/email/net/) библиотека.  
2. Среда разработки: установите Visual Studio или любую другую совместимую с .NET IDE.  
3. .NET Framework: убедитесь, что установлен .NET Framework 4.5 или более поздней версии.  
4.  Временная лицензия: рассмотрите возможность получения[временная лицензия](https://purchase.aspose.com/temporary-license/) чтобы изучить все возможности Aspose.Email.  
5.  Образец файла электронной почты: подготовьте`.eml` файл (например,`test.eml`) для использования в качестве образца.  

## Импортные пакеты  

Чтобы использовать Aspose.Email в вашем проекте, вам нужно импортировать требуемые пространства имен. Добавьте следующие операторы using в начало вашего файла:  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## Шаг 1: Настройте свой проект  

Начните с создания нового консольного приложения C# в Visual Studio. Это послужит основой для реализации отслеживания преобразования документов электронной почты.  
  
1. Откройте Visual Studio и создайте новый проект консольного приложения.  
2. Установите пакет Aspose.Email NuGet:  
```sh
Install-Package Aspose.Email
```  
3.  Добавьте`.eml` файл в каталог вашего проекта.  

## Шаг 2: Загрузите файл электронной почты  

 Теперь загрузите файл электронной почты в`MailMessage` объект. Это первый шаг в работе с данными электронной почты.  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`: Указывает каталог, в котором находится файл вашей электронной почты.  
- `MailMessage.Load` : Читает`.eml` файл и подготавливает его к дальнейшим операциям.  

## Шаг 3: Инициализация потока памяти  

 Далее создайте`MemoryStream` объект для временного хранения преобразованных данных электронной почты.  
 
```csharp
MemoryStream ms = new MemoryStream();
```

 А`MemoryStream` здесь используется для управления выводом процесса преобразования без сохранения данных непосредственно на диск.  

## Шаг 4: Определите параметры преобразования  

 Настройте`EmlSaveOptions` с настраиваемым обработчиком прогресса для отслеживания хода преобразования.  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`: Указывает формат вывода.  
- `CustomProgressHandler`: Назначает пользовательскую функцию обработчика для отслеживания прогресса.  

## Шаг 5: Сохраните электронное письмо в потоке памяти  

Сохранить`MailMessage` объект с указанными параметрами, включающий функцию отслеживания прогресса.  
 
```csharp
msg.Save(ms, opt);
```
 
Этот шаг инициирует процесс преобразования электронной почты и отправляет обновления обработчику хода выполнения.  

## Шаг 6: Реализация обработчика прогресса  

 Определите`ShowEmlConversionProgress` метод обработки обновлений хода выполнения и отображения их в консоли.  
 
```csharp
private static void ShowEmlConversionProgress(ProgressEventHandlerInfo info)
{
    int total;
    int saved;

    switch (info.EventType)
    {
        case ProgressEventType.MimeStructureCreated:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimeStructureCreated - TotalMimePartCount: {total}");
            Console.WriteLine($"MimeStructureCreated - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.MimePartSaved:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimePartSaved - TotalMimePartCount: {total}");
            Console.WriteLine($"MimePartSaved - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.SavedToStream:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"SavedToStream - TotalMimePartCount: {total}");
            Console.WriteLine($"SavedToStream - SavedMimePartCount: {saved}");
            break;
    }
}
```
 
- `ProgressEventHandlerInfo`: Предоставляет подробную информацию о процессе конвертации.  
-  Случаи переключения: обработка различных этапов преобразования:`MimeStructureCreated`, `MimePartSaved` , и`SavedToStream`.  

### Чего ожидать?  
По мере выполнения преобразования на консоли будут выводиться подробные обновления, например:  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## Заключение  

Отслеживание процесса преобразования документов электронной почты в C# никогда не было таким простым благодаря Aspose.Email для .NET. Следуя этому руководству, вы узнали, как загружать файл электронной почты, настраивать обработчик хода выполнения и сохранять данные электронной почты, отслеживая весь процесс. Эта функция гарантирует, что вы будете в курсе и будете контролировать операции с документами электронной почты.  

## Часто задаваемые вопросы  

###  Могу ли я использовать этот код для форматов, отличных от`.eml`?  
 Да, изменить`MailMessageSaveType`для соответствия другим форматам, таким как MSG или MHTML.  

### Как обрабатывать большие файлы электронной почты?  
 Рассмотрите возможность использования`FileStream` вместо`MemoryStream` для лучшей производительности при работе с большими файлами.  

### Что такое временная лицензия и как ее получить?  
 Временная лицензия позволяет вам бесплатно оценить все возможности библиотеки. Получить[здесь](https://purchase.aspose.com/temporary-license/).  

### Могу ли я интегрировать этот код в веб-приложение?  
Да, код совместим с веб-приложениями, использующими ASP.NET или аналогичные фреймворки.  

### Где я могу найти дополнительные ресурсы?  
 Проверьте[документация](https://reference.aspose.com/email/net/) или посетите[форум поддержки](https://forum.aspose.com/c/email/12/) за помощь.  