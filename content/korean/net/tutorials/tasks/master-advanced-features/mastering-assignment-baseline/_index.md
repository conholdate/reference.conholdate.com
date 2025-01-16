---
title: Aspose.Tasks for .NET을 사용하여 할당 기준선 마스터링
linktitle: Aspose.Tasks에서 할당 기준선 관리
second_title: Aspose.Tasks .NET API
description: Aspose.Tasks for .NET을 사용하여 할당 기준선을 효율적으로 관리하는 방법을 알아보세요. 이 단계별 가이드는 프로젝트 로딩, 기준선 설정, 데이터 검색, 기준선 비교 등을 다루어 프로젝트 관리 워크플로를 최적화합니다.
type: docs
weight: 14
url: /ko/net/tutorials/tasks/master-advanced-features/mastering-assignment-baseline/
---
## 소개

효율적인 프로젝트 관리의 핵심은 할당 기준선을 정확하게 추적하고 관리하는 것입니다. Aspose.Tasks for .NET을 사용하면 더 나은 프로젝트 통찰력을 위해 할당 기준선 처리를 간소화하는 강력한 툴킷을 얻을 수 있습니다. 이 문서에서는 할당 기준선을 관리하고 프로젝트가 제대로 진행되도록 하는 프로세스를 안내합니다.

## 필수 조건

구현에 들어가기 전에 다음 사항이 있는지 확인하세요.

- 프로그래밍 전문성: C#에 대한 기본적인 지식이 있어야 합니다.
- 개발 환경: Visual Studio 설치 및 구성.
-  .NET 라이브러리용 Aspose.Tasks: 여기에서 다운로드하세요.[Aspose.Tasks 릴리스](https://releases.aspose.com/tasks/net/).
- 프로젝트 파일: MPP 형식의 프로젝트 파일에 액세스합니다.

## 필요한 네임스페이스 가져오기

Aspose.Tasks의 기능을 사용하려면 프로젝트 파일에 다음 네임스페이스를 포함하세요.

```csharp
using Aspose.Tasks;
using System;
```

## 1단계: 프로젝트 로드 및 기준선 설정

프로젝트를 로드하고 기준선을 설정하는 것은 할당 기준선을 관리하는 데 기본이 됩니다. 다음 코드는 프로젝트를 로드하고 기준선을 설정하는 방법을 보여줍니다.

```csharp
string dataDir = "Your Document Directory";
Project project = new Project(dataDir + "ProjectSample.mpp");

// 프로젝트 기준선 설정
project.SetBaseline(BaselineType.Baseline);
Console.WriteLine("Baseline has been set successfully.");
```

## 2단계: 과제 기준 데이터 검색

각 리소스 할당에 대한 자세한 기준선 정보를 추출할 수 있습니다. 방법은 다음과 같습니다.

```csharp
foreach (var assignment in project.ResourceAssignments)
{
    foreach (var baseline in assignment.Baselines)
    {
        Console.WriteLine("Baseline Start: " + baseline.Start);
        Console.WriteLine("Baseline Finish: " + baseline.Finish);
        Console.WriteLine("Baseline Cost: " + baseline.Cost);
        Console.WriteLine("Baseline Work: " + baseline.Work);
    }
}
```

## 3단계: 할당 간 기준선 비교

Aspose.Tasks를 사용하면 프로그래밍 방식으로 기준선을 비교하여 리소스 할당 간의 차이점을 평가할 수 있습니다.

```csharp
var assignment1 = project.ResourceAssignments.GetByUid(1);
var assignment2 = project.ResourceAssignments.GetByUid(2);

var baseline1 = assignment1.Baselines.First();
var baseline2 = assignment2.Baselines.First();

bool areEqual = baseline1.Equals(baseline2);
Console.WriteLine("Are the baselines equal? " + areEqual);
```

## 4단계: 기준선 세부 정보를 프로그래밍 방식으로 수정

변화하는 프로젝트 요구 사항을 충족하기 위해 기준 데이터를 프로그래밍 방식으로 수정할 수 있습니다.

```csharp
var assignment = project.ResourceAssignments.GetByUid(3);
var baseline = assignment.Baselines.First();

baseline.Cost += 1000;  // 기준 비용 조정
baseline.Work = baseline.Work.Add(TimeSpan.FromHours(10));  // 근무시간 추가

Console.WriteLine("Modified Baseline Cost: " + baseline.Cost);
Console.WriteLine("Modified Baseline Work: " + baseline.Work);
```

## 결론

할당 기준선을 효과적으로 관리하는 것은 프로젝트 일정과 예산에 대한 통제를 유지하는 데 필수적입니다. Aspose.Tasks for .NET은 기준선을 정밀하게 처리하는 데 필요한 도구를 제공하여 데이터 기반 의사 결정을 가능하게 합니다.

## 자주 묻는 질문

### Aspose.Tasks가 단일 프로젝트에 대해 여러 개의 기준선을 처리할 수 있나요?  
네, Aspose.Tasks는 여러 기준선을 지원하여 다양한 프로젝트 버전을 추적하는 데 유연성을 제공합니다.

### Aspose.Tasks는 MPP가 아닌 프로젝트 파일과 호환됩니까?  
물론입니다. Aspose.Tasks는 XML, MPX 등의 형식을 지원합니다.

### 기준선 업데이트를 자동화할 수 있나요?  
네, API를 사용하면 프로그래밍 방식으로 동적이고 자동화된 기준선 수정이 가능합니다.

### Aspose.Tasks는 시간별 기준선 데이터를 제공합니까?  
네, 세부적인 시간대별 기준선 데이터를 검색하여 분석할 수 있습니다.

### 지원과 문서는 어디에서 볼 수 있나요?  
 방문하다[Aspose.Tasks 문서](https://reference.aspose.com/words/net/)또는 가입하세요[Aspose 지원 포럼](https://forum.aspose.com/c/words/8) 도움이 필요하면. 