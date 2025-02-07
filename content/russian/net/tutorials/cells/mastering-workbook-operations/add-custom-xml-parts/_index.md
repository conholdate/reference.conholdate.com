---
title: Добавление пользовательских частей XML в книги Excel
linktitle: Добавление пользовательских частей XML в книги Excel
second_title: API обработки Excel Aspose.Cells .NET
description: Изучите всеобъемлющее руководство по интеграции пользовательских частей XML в рабочие книги Excel с Aspose.Cells для .NET. Узнайте, как создать рабочую книгу, добавить пользовательский XML, назначить уникальные идентификаторы и эффективно извлечь эти части.
type: docs
weight: 11
url: /ru/net/tutorials/cells/mastering-workbook-operations/add-custom-xml-parts/
---
## Введение

Когда дело доходит до программного управления файлами Excel, Aspose.Cells for .NET является выдающейся библиотекой. Одной из ее захватывающих функций является возможность интегрировать пользовательские части XML в вашу книгу Excel. Это руководство проведет вас через процесс добавления пользовательских частей XML с уникальными идентификаторами и их извлечения при необходимости. Давайте начнем!

## Предпосылки
Прежде чем приступить к написанию кода, убедитесь, что у вас настроено следующее:
1. Visual Studio: убедитесь, что на вашем компьютере установлена Visual Studio для программирования.
2. Aspose.Cells for .NET: Вам необходимо установить эту библиотеку. Если вы этого еще не сделали, вы можете[скачать здесь](https://releases.aspose.com/cells/net/).
3. .NET Framework: Знакомство с .NET Framework и C# будет полезным.

Как только вы все подготовите, давайте приступим к кодированию!

## Импорт необходимых пакетов
Чтобы использовать Aspose.Cells, добавьте необходимые пространства имен в верхней части кода:
```csharp
using System;
using Aspose.Cells;
```
Это позволяет вам получить доступ ко всем функциям, предоставляемым Aspose.Cells.

## Шаг 1: Создайте пустую рабочую книгу
 Начните с создания экземпляра`Workbook` класс, представляющий вашу книгу Excel:
```csharp
// Создайте пустую рабочую книгу.
Workbook wb = new Workbook();
```
Это инициализирует новую рабочую книгу, в которую вы можете добавлять свои собственные XML-части.

## Шаг 2: Подготовьте данные и схему XML
Далее подготовьте ваши данные XML и схему как массивы байтов. Хотя в этом примере используются данные-заполнители, вам следует заменить их вашим фактическим содержимым XML.
```csharp
// Пример данных в виде байтовых массивов.
byte[] btsData = System.Text.Encoding.UTF8.GetBytes("<root><data>Example</data></root>");
byte[] btsSchema = System.Text.Encoding.UTF8.GetBytes("<root><data></data></root>");
```

## Шаг 3: Добавьте пользовательские XML-части
 Теперь добавьте ваши пользовательские XML-части в рабочую книгу, вызвав метод`Add`метод на`CustomXmlParts` коллекция:
```csharp
// Добавьте пользовательские XML-части в рабочую книгу.
wb.CustomXmlParts.Add(btsData, btsSchema);
wb.CustomXmlParts.Add(btsData, btsSchema);
wb.CustomXmlParts.Add(btsData, btsSchema);
wb.CustomXmlParts.Add(btsData, btsSchema);
```
Этот фрагмент кода добавляет четыре идентичных пользовательских XML-части. Вы можете настроить его в соответствии со своими требованиями.

## Шаг 4: Назначьте уникальные идентификаторы пользовательским частям XML
Присвойте уникальные идентификаторы каждой части XML, чтобы облегчить ее последующий поиск:
```csharp
// Назначьте идентификаторы пользовательским частям XML.
wb.CustomXmlParts[0].ID = "Fruit";
wb.CustomXmlParts[1].ID = "Color";
wb.CustomXmlParts[2].ID = "Sport";
wb.CustomXmlParts[3].ID = "Shape";
```
Эти значимые идентификаторы помогут вам позже идентифицировать соответствующие детали.

## Шаг 5: Укажите идентификаторы поиска для пользовательских частей XML
Чтобы получить определенную часть XML, определите идентификатор, который вы ищете:
```csharp
// Укажите идентификатор пользовательской части XML для поиска.
string srchID = "Fruit"; // При необходимости измените это на другие идентификаторы.
```

## Шаг 6: Поиск пользовательских частей XML по идентификатору
Теперь найдите пользовательскую часть XML, используя указанный идентификатор:
```csharp
// Найдите пользовательскую часть XML по идентификатору поиска.
CustomXmlPart cxp = wb.CustomXmlParts.SelectByID(srchID);
```
 Эта линия использует`SelectByID` для поиска части XML, связанной с указанным идентификатором.

## Шаг 7: Проверьте, найдена ли пользовательская часть XML
Наконец, проверьте, найдена ли часть XML, и выведите соответствующее сообщение:
```csharp
// Вывести на консоль сообщение о найденном или не найденном объекте.
if (cxp == null)
{
    Console.WriteLine("Not Found: CustomXmlPart ID " + srchID);
}
else
{
    Console.WriteLine("Found: CustomXmlPart ID " + srchID);
}
Console.WriteLine("AddCustomXMLPartsAndSelectThemByID executed successfully.");
```
Поздравляем! Вы успешно добавили пользовательские XML-части в свою книгу и реализовали функцию поиска по их идентификаторам.

## Заключение
В этой статье мы рассмотрели, как добавлять пользовательские XML-части в книгу Excel с помощью Aspose.Cells for .NET. Следуя этому пошаговому руководству, вы узнали, как создавать книгу, добавлять пользовательские XML-части, назначать идентификаторы и эффективно извлекать их. Эта функция бесценна для обработки динамических данных в файлах Excel, расширяя возможности ваших приложений.

## Часто задаваемые вопросы

### Что такое Aspose.Cells?
Aspose.Cells — это мощная библиотека .NET, которая позволяет разработчикам создавать, обрабатывать и конвертировать файлы Excel без необходимости установки Microsoft Excel.

### Могу ли я использовать Aspose.Cells бесплатно?
 Да! Вы можете начать с бесплатной пробной версии. Просто[скачать здесь](https://releases.aspose.com/).

### Можно ли добавить несколько пользовательских частей XML в книгу?
Конечно! Вы можете добавлять столько пользовательских частей XML, сколько необходимо, каждая из которых будет иметь уникальный идентификатор для легкого доступа.

### Как мне получить части XML, если я не знаю идентификаторы?
 Если вы не знаете идентификаторы, вы можете просмотреть их`CustomXmlParts` коллекция для просмотра имеющихся деталей и их идентификаторов, что упрощает идентификацию.

### Где я могу найти дополнительные ресурсы или поддержку для Aspose.Cells?
 Вы можете проверить[документация](https://reference.aspose.com/cells/net/) для получения подробной информации или посетите[форум поддержки](https://forum.aspose.com/c/cells/9) для оказания помощи обществу.

---

Эта простая строка инициализирует новую рабочую книгу, в которую мы можем добавлять наши пользовательские XML-части.
## Шаг 2: Подготовьте данные и схему XML
Далее вам нужно подготовить некоторые данные в виде массива байтов. Хотя в нашем примере используются данные-заполнители, в реальном сценарии вы заменили бы эти массивы байтов фактическими данными XML и схемой, которые вы хотите интегрировать в свою рабочую книгу.
```csharp
// Некоторые данные в виде массива байтов.
// Вместо этого используйте правильный XML и схему.
byte[] btsData = new byte[] { 1, 2, 3 };
byte[] btsSchema = new byte[] { 1, 2, 3 };
```
Помните, хотя в этом примере используются простые массивы байтов, обычно здесь используются допустимые XML и схема.
## Шаг 3: Добавьте пользовательские XML-части
 Теперь пришло время добавить ваши пользовательские XML-части в рабочую книгу. Вы можете сделать это, вызвав`Add`метод на`CustomXmlParts` Сборник рабочей тетради.
```csharp
// Создайте четыре пользовательских XML-части.
wb.CustomXmlParts.Add(btsData, btsSchema);
wb.CustomXmlParts.Add(btsData, btsSchema);
wb.CustomXmlParts.Add(btsData, btsSchema);
wb.CustomXmlParts.Add(btsData, btsSchema);
```
Этот фрагмент кода добавляет четыре идентичных пользовательских XML-части в рабочую книгу. Вы можете настроить это в соответствии со своими требованиями.
## Шаг 4: Назначение идентификаторов пользовательским частям XML
Теперь, когда у нас есть добавленные части XML, давайте дадим каждой из них уникальный идентификатор. Этот идентификатор поможет нам позже извлечь части XML.
```csharp
// Назначьте идентификаторы пользовательским частям XML.
wb.CustomXmlParts[0].ID = "Fruit";
wb.CustomXmlParts[1].ID = "Color";
wb.CustomXmlParts[2].ID = "Sport";
wb.CustomXmlParts[3].ID = "Shape";
```
На этом этапе вы назначаете значимые идентификаторы, такие как «Фрукт», «Цвет», «Спорт» и «Форма». Это упрощает идентификацию и работу с соответствующими частями в дальнейшем.
## Шаг 5: Укажите идентификатор поиска для пользовательской XML-части
Если вы хотите получить определенную часть XML, используя ее идентификатор, вам необходимо определить идентификатор, который вы ищете.
```csharp
//Укажите идентификатор пользовательской части XML для поиска.
String srchID = "Fruit";
srchID = "Color";
srchID = "Sport";
```
В реальном приложении вы, скорее всего, захотите указать каждый идентификатор динамически, но в нашем примере мы жестко закодируем несколько.
## Шаг 6: Поиск пользовательской XML-части по идентификатору
Теперь, когда у нас есть идентификаторы поиска, пришло время найти пользовательскую часть XML, соответствующую указанному идентификатору.
```csharp
// Поиск пользовательской части XML по идентификатору поиска.
Aspose.Cells.Markup.CustomXmlPart cxp = wb.CustomXmlParts.SelectByID(srchID);
```
 Эта линия использует`SelectByID` чтобы попытаться найти интересующую нас часть XML.
## Шаг 7: Проверьте, найдена ли пользовательская часть XML
Наконец, нам нужно проверить, была ли найдена XML-часть, и вывести соответствующее сообщение на консоль.
```csharp
// Вывести на консоль сообщение «Найден» или «Не найден».
if (cxp == null)
{
    Console.WriteLine("Not Found: CustomXmlPart ID " + srchID);
}
else
{
    Console.WriteLine("Found: CustomXmlPart ID " + srchID);
}
Console.WriteLine("AddCustomXMLPartsAndSelectThemByID executed successfully.");
```
Вы его раздавили! К этому моменту вы не только добавили пользовательские XML-части в свою рабочую книгу, но и реализовали функциональность для их поиска по идентификаторам.
## Заключение
В этой статье мы рассмотрели, как добавлять пользовательские XML-части в книгу Excel с помощью Aspose.Cells for .NET. Следуя пошаговому руководству, вы смогли создать книгу, добавить пользовательские XML-части, назначить идентификаторы и эффективно их извлечь. Эта функциональность может быть невероятно полезной при работе с динамическими данными, которые необходимо обрабатывать в файлах Excel, делая ваши приложения более умными и способными. 
## Часто задаваемые вопросы
### Что такое Aspose.Cells?  
Aspose.Cells — это надежная библиотека .NET, которая позволяет разработчикам создавать, изменять и конвертировать файлы Excel без необходимости установки Microsoft Excel.
### Могу ли я использовать Aspose.Cells бесплатно?  
 Да! Вы можете начать с бесплатной пробной версии. Просто[скачать здесь](https://releases.aspose.com/).
### Можно ли добавить несколько пользовательских частей XML в книгу?  
Конечно! Вы можете добавить столько пользовательских частей XML, сколько вам нужно, и каждой из них можно присвоить уникальный идентификатор для легкого доступа.
### Как мне получить части XML, если я не знаю идентификаторы?  
 Если вы не знаете идентификаторы, вы можете просмотреть их`CustomXmlParts` коллекция для просмотра имеющихся деталей и их идентификаторов, что упрощает их идентификацию и доступ к ним.
### Где я могу найти дополнительные ресурсы или поддержку для Aspose.Cells?  
 Вы можете проверить[документация](https://reference.aspose.com/cells/net/) для получения подробной информации или посетите[форум поддержки](https://forum.aspose.com/c/cells/9) для помощи обществу.
