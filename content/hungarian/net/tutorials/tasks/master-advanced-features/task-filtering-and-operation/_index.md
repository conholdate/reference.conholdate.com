---
title: Feladatszűrés ÉS Működés az Aspose.Tasks-ban
linktitle: Feladatszűrés ÉS Működés az Aspose.Tasks-ban
second_title: Aspose.Tasks .NET API
description: Ismerje meg, hogyan használhatja ki az Aspose.Tasks for .NET osztályát a projektfeladatok több feltétel alapján történő szűrésére. Olyan feltételek kombinálásával, mint az összefoglaló feladatok és a nem null attribútumok.
type: docs
weight: 10
url: /hu/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## Bevezetés

Ebben az oktatóanyagban megvizsgáljuk, hogyan hajthatjuk végre a projektfeladatok speciális szűrését az Aspose.Tasks for .NET-ben a`Util.And` osztály. Ez a hatékony funkció lehetővé teszi a fejlesztők számára, hogy több kritérium alapján hatékonyan szűrjék a feladatokat.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1. C# programozási alapismeretek.
2.  Aspose.Tasks for .NET telepítve. Ha még nem tette meg, letöltheti innen[ezt a linket](https://releases.aspose.com/tasks/net/).
3. Integrált fejlesztői környezet (IDE), például a Visual Studio a kód írásához és futtatásához.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket a C# projektbe. Ez lehetővé teszi az Aspose.Tasks által biztosított funkciók elérését.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## 1. lépés: Inicializálja a projektet és gyűjtse össze a feladatokat

 Először inicializáljon egy Aspose.Tasks projektet, és gyűjtse össze benne az összes feladatot. Demonstrációs célból feltételezzük, hogy van egy nevű projektfájl`Project2.mpp`.

```csharp
// A dokumentumok könyvtár elérési útja
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// Gyűjtsd össze az összes gyermekfeladatot
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## 2. lépés: Adja meg a szűrési feltételeket

Ebben a lépésben meghatározzuk a szűrési feladatok feltételeit. Példánkban két feltételt fogunk létrehozni: az egyiket az összefoglaló feladatok szűrésére, a másikat pedig annak biztosítására, hogy a feladatok ne legyenek nullák.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## 3. lépés: A feltételek kombinálása az ÉS művelettel

 A következő lépés ezeknek a feltételeknek a kombinálása a`Util.And` osztály. Ez lehetővé teszi olyan összetett feltétel létrehozását, amely mindkét feltételt kötelezővé teszi.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## 4. lépés: Alkalmazza a Kombinált feltétel és szűrési feladatokat

Most alkalmazzuk a kombinált feltételt az összegyűjtött feladatokra, hogy kiszűrjük azokat a konkrét feladatokat, amelyek mindkét feltételnek megfelelnek.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## 5. lépés: Adja ki a szűrt feladatokat

Végül ismételjük a szűrt feladatainkat, és megjelenítjük a releváns részleteket. Ez segít megérteni a kritériumainknak megfelelő feladatokat.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## Következtetés

 Ebben az oktatóanyagban bemutattuk, hogyan hajthatunk végre speciális szűrési műveleteket az Aspose.Tasks for .NET-ben a`Util.And`osztály. Több feltétel kombinálásával hatékonyan szűrhetjük a feladatokat, ezzel is növelve projektmenedzsment alkalmazásaink hasznosságát.

## GYIK

### Mi az Aspose.Tasks a .NET számára?

Az Aspose.Tasks for .NET egy átfogó API, amelyet a fejlesztők számára fejlesztettek ki, hogy programozottan kezeljék a Microsoft Project fájlokat .NET-alkalmazásokon belül.

### Kombinálhatok kettőnél több feltételt az Util.And használatával?

 Igen! A`Util.And` osztály lehetővé teszi több feltétel kombinálását, lehetővé téve az Ön igényeire szabott komplex szűrési logikát.

### Elérhető az Aspose.Tasks ingyenes próbaverziója?

 Igen, letölthet egy ingyenes próbaverziót a webhelyről[ezt a linket](https://releases.aspose.com/).

### Hol találom az Aspose.Tasks részletes dokumentációját?

 A részletes dokumentáció elérhető[itt](https://reference.aspose.com/tasks/net/).

### Hogyan kérhetek támogatást az Aspose.Tasks-hoz?

 A támogatás az Aspose.Tasks közösségi fórumon keresztül érhető el, amely elérhető[itt](https://forum.aspose.com/c/tasks/15).