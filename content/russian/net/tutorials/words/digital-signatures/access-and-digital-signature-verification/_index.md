---
title: Проверка доступа и цифровой подписи в документах Word
linktitle: Проверка доступа и цифровой подписи в документах Word
second_title: API обработки документов Aspose.Words
description: Раскройте весь потенциал Aspose.Words для .NET, узнав, как эффективно проверять цифровые подписи в документах Word. Это пошаговое руководство проведет вас через процесс настройки.
type: docs
weight: 10
url: /ru/net/tutorials/words/digital-signatures/access-and-digital-signature-verification/
---
## Введение

Привет, энтузиасты технологий! Вам когда-нибудь приходилось проверять цифровые подписи в документе Word, и вы чувствовали себя подавленными? Не бойтесь! Сегодня мы отправляемся в путешествие по мощным возможностям Aspose.Words для .NET. К концу этого руководства вы будете готовы получить доступ к цифровым подписям и проверять их как профессионал. Давайте погрузимся!

## Предпосылки

Прежде чем начать, убедитесь, что у вас готово следующее:

1. Visual Studio: убедитесь, что она установлена на вашем компьютере для программирования.
2.  Aspose.Words для .NET: Загрузите и установите его с[здесь](https://releases.aspose.com/words/net/) Если вы еще этого не сделали, воспользуйтесь бесплатной пробной версией.[здесь](https://releases.aspose.com/).
3. Документ Word с цифровой подписью: приготовьте документ Word с цифровой подписью для проверки.

## Импорт пространств имен

Во-первых, нам нужно импортировать необходимые пространства имен для использования функций Aspose.Words в вашем проекте. Вот как это сделать:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.DigitalSignatures;
```

Теперь, когда мы рассмотрели основы, давайте разобьем процесс на выполнимые этапы.

## Шаг 1: Настройте свой проект

Создадим новый проект в Visual Studio:

### Создать новый проект

1. Откройте Visual Studio.
2. Нажмите «Создать новый проект».
3. Выберите Консольное приложение (.NET Core) или Консольное приложение (.NET Framework).
4. Нажмите «Далее», назовите свой проект и нажмите «Создать».

### Установить Aspose.Words для .NET

1. В обозревателе решений щелкните правой кнопкой мыши имя вашего проекта и выберите «Управление пакетами NuGet».
2. Найдите Aspose.Words в диспетчере пакетов NuGet.
3. Нажмите «Установить», чтобы добавить его в свой проект.

## Шаг 2: Загрузите документ Word с цифровой подписью

После настройки проекта давайте загрузим документ Word с цифровой подписью.

```csharp
// Укажите путь к каталогу ваших документов.
string dataDir = "YOUR_DOCUMENT_DIRECTORY/";
Document doc = new Document(dataDir + "DigitallySigned.docx");
```

 Не забудьте заменить`"YOUR_DOCUMENT_DIRECTORY"`с фактическим путем к вашему документу. Этот фрагмент кода инициализирует новый`Document` объект и загружает ваш подписанный документ Word.

## Шаг 3: Получите доступ к цифровым подписям

Теперь, когда документ загружен, пришло время получить доступ к цифровым подписям и проверить их.

```csharp
foreach (DigitalSignature signature in doc.DigitalSignatures)
{
    Console.WriteLine("* Signature Found *");
    Console.WriteLine("Is valid: " + signature.IsValid);
    Console.WriteLine("Reason for signing: " + signature.Comments); 
    Console.WriteLine("Time of signing: " + signature.SignTime);
    Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
    Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
    Console.WriteLine();
}
```

Этот цикл проходит по каждой цифровой подписи в документе и выводит ключевые данные:

- Действительна: указывает, действительна ли подпись.
- Причина подписания: Отображает причину подписания.
- Время подписания: показывает, когда документ был подписан.
- Имя субъекта: Извлекает субъекта из сертификата.
- Имя эмитента: извлекает эмитента из сертификата.

## Шаг 4: Запустите свой код

Теперь давайте выполним ваш код и посмотрим на результаты.

1. Нажмите клавишу F5 или кнопку «Пуск» в Visual Studio.
2. Если ваш документ имеет цифровую подпись, данные подписи будут напечатаны в консоли.

## Шаг 5: Обработайте потенциальные ошибки

Крайне важно изящно обрабатывать любые потенциальные ошибки. Вот как добавить базовую обработку ошибок в ваш код:

```csharp
try
{
    // Укажите путь к каталогу ваших документов.
    string dataDir = "YOUR_DOCUMENT_DIRECTORY/";
    Document doc = new Document(dataDir + "DigitallySigned.docx");

    foreach (DigitalSignature signature in doc.DigitalSignatures)
    {
        Console.WriteLine("* Signature Found *");
        Console.WriteLine("Is valid: " + signature.IsValid);
        Console.WriteLine("Reason for signing: " + signature.Comments); 
        Console.WriteLine("Time of signing: " + signature.SignTime);
        Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
        Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
        Console.WriteLine();
    }
}
catch (Exception ex)
{
    Console.WriteLine("An error occurred: " + ex.Message);
}
```

Этот код перехватит любые исключения и выведет сообщение об ошибке, помогая вам более эффективно отлаживать проблемы.

## Заключение

Поздравляем! Вы успешно проверили цифровые подписи в документе Word с помощью Aspose.Words for .NET. Это проще, чем кажется, не так ли? С помощью этих шагов вы сможете уверенно управлять цифровыми подписями в ваших документах Word, гарантируя их подлинность и целостность. Удачного кодирования!

## Часто задаваемые вопросы

### Можно ли использовать Aspose.Words for .NET для добавления цифровых подписей в документ Word?

Конечно! Aspose.Words для .NET предоставляет комплексные функции как для добавления, так и для проверки цифровых подписей.

### Какие типы цифровых подписей может проверять Aspose.Words for .NET?

Aspose.Words for .NET может проверять цифровые подписи в файлах DOCX, использующих сертификаты X.509.

### Совместим ли Aspose.Words для .NET со всеми версиями Microsoft Word?

Да, он поддерживает все версии документов Microsoft Word, включая DOC, DOCX, RTF и другие.

### Как получить временную лицензию на Aspose.Words для .NET?

Вы можете получить временную лицензию[здесь](https://purchase.aspose.com/temporary-license/), что позволяет вам без ограничений изучить все возможности библиотеки.

### Где я могу найти дополнительную документацию по Aspose.Words для .NET?

 Подробную документацию можно найти на сайте[здесь](https://reference.aspose.com/words/net/).