---
title: Aspose.Tasks에서의 작업 필터링 및 작업
linktitle: Aspose.Tasks에서의 작업 필터링 및 작업
second_title: Aspose.Tasks .NET API
description: Aspose.Tasks for .NET에서 클래스를 활용하여 여러 조건에 따라 프로젝트 작업을 필터링하는 방법을 알아보세요. 요약 작업 및 null이 아닌 속성과 같은 기준을 결합합니다.
type: docs
weight: 10
url: /ko/net/tutorials/tasks/master-advanced-features/task-filtering-and-operation/
---
## 소개

이 튜토리얼에서는 Aspose.Tasks for .NET에서 프로젝트 작업의 고급 필터링을 수행하는 방법을 살펴보겠습니다.`Util.And` 클래스. 이 강력한 기능을 통해 개발자는 여러 기준에 따라 효율적으로 작업을 필터링할 수 있습니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1. C# 프로그래밍에 대한 기본 지식.
2.  .NET용 Aspose.Tasks가 설치되었습니다. 아직 설치하지 않았다면 다음에서 다운로드할 수 있습니다.[이 링크](https://releases.aspose.com/tasks/net/).
3. 코드를 작성하고 실행하기 위한 Visual Studio와 같은 통합 개발 환경(IDE)이 필요합니다.

## 네임스페이스 가져오기

시작하려면 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다. 이렇게 하면 Aspose.Tasks에서 제공하는 기능에 액세스할 수 있습니다.

```csharp
using Aspose.Tasks;
using System;
using System.Collections.Generic;
using Aspose.Tasks.Util;

```

## 1단계: 프로젝트 초기화 및 작업 수집

 먼저 Aspose.Tasks 프로젝트를 초기화하고 그 안에 있는 모든 작업을 수집합니다. 데모 목적으로 프로젝트 파일이 있다고 가정하겠습니다.`Project2.mpp`.

```csharp
// 문서 디렉토리 경로
string dataDir = "Your Document Directory";
var project = new Project(dataDir + "Project2.mpp");

// 모든 자식 작업 수집
var taskCollector = new ChildTasksCollector();
TaskUtils.Apply(project.RootTask, taskCollector, 0);
```

## 2단계: 필터 조건 정의

이 단계에서는 작업 필터링 조건을 정의합니다. 이 예에서는 두 가지 조건을 만듭니다. 하나는 요약 작업을 필터링하는 조건이고 다른 하나는 작업이 null이 아닌지 확인하는 조건입니다.

```csharp
var summaryCondition = new SummaryCondition();
var notNullCondition = new NotNullCondition();
```

## 3단계: AND 연산을 사용하여 조건 결합

 다음 단계는 이러한 조건을 결합하는 것입니다.`Util.And` 클래스. 이를 통해 두 기준을 모두 요구하는 복합 조건을 만들 수 있습니다.

```csharp
var combinedCondition = new And<Task>(summaryCondition, notNullCondition);
```

## 4단계: 결합된 조건 및 필터 작업 적용

이제 수집된 작업에 결합 조건을 적용하여 두 조건을 모두 충족하는 특정 작업을 필터링해 보겠습니다.

```csharp
List<Task> filteredTasks = Filter(taskCollector.Tasks, combinedCondition);
```

## 5단계: 필터링된 작업 출력

마지막으로, 필터링된 작업을 반복하고 관련 세부 정보를 출력합니다. 이를 통해 기준을 충족하는 작업을 이해하는 데 도움이 됩니다.

```csharp
Console.WriteLine("Filtered Tasks:");
foreach (var task in filteredTasks)
{
    Console.WriteLine(" - Task Name: " + task.Get(Tsk.Name));
}
```

## 결론

 이 튜토리얼에서는 Aspose.Tasks for .NET에서 고급 필터링 작업을 수행하는 방법을 보여주었습니다.`Util.And`클래스. 여러 조건을 결합함으로써, 우리는 효과적으로 작업을 필터링할 수 있고, 이를 통해 프로젝트 관리 애플리케이션의 유용성을 향상시킬 수 있습니다.

## 자주 묻는 질문

### .NET용 Aspose.Tasks란 무엇인가요?

.NET용 Aspose.Tasks는 개발자가 .NET 애플리케이션 내에서 Microsoft Project 파일을 프로그래밍 방식으로 조작할 수 있도록 설계된 포괄적인 API입니다.

### Util.And를 사용하여 두 개 이상의 조건을 결합할 수 있나요?

 네!`Util.And` 클래스를 사용하면 여러 조건을 결합할 수 있으므로 사용자의 요구 사항에 맞춰 복잡한 필터링 논리를 구현할 수 있습니다.

### Aspose.Tasks에 대한 무료 평가판이 있나요?

 네, 무료 평가판을 다운로드할 수 있습니다.[이 링크](https://releases.aspose.com/).

### Aspose.Tasks에 대한 자세한 문서는 어디에서 찾을 수 있나요?

 자세한 문서가 제공됩니다.[여기](https://reference.aspose.com/tasks/net/).

### Aspose.Tasks에 대한 지원을 받으려면 어떻게 해야 하나요?

 지원은 Aspose.Tasks 커뮤니티 포럼을 통해 제공되며,[여기](https://forum.aspose.com/c/tasks/15).