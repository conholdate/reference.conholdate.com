---
title: Aspose.Tasks for .NET을 사용하여 MS Project 파일을 PDF로 변환
linktitle: Aspose.Tasks에 대한 PDF 저장 옵션
second_title: Aspose.Tasks .NET API
description: Aspose.Tasks for .NET을 사용하여 Microsoft Project(.mpp) 파일을 PDF로 변환하는 방법을 알아보세요. 이 단계별 가이드를 따라 PDF 출력을 사용자 지정하고, 특정 페이지를 선택하고, 일괄 변환을 자동화하세요.
type: docs
weight: 13
url: /ko/net/tutorials/tasks/guide-to-saving-options/convert-ms-project-files-to-pdf/
---
## 소개

효율적인 프로젝트 파일 관리가 간소화된 워크플로와 프로젝트 성공에 중요한 역할을 합니다. Aspose.Tasks for .NET을 사용하면 개발자는 Microsoft Project 파일을 정밀하고 유연하게 PDF 형식으로 변환할 수 있습니다. 이 가이드에서는 Microsoft Project(.mpp) 파일을 사용자 정의 가능한 옵션과 함께 PDF로 저장하는 단계별 프로세스를 안내합니다.

## .NET용 Aspose.Tasks 사용을 위한 전제 조건

계속하기 전에 다음 전제 조건이 충족되는지 확인하세요.

1. .NET 설치를 위한 Aspose.Tasks  
    라이브러리를 다운로드하고 설치하세요[웹사이트](https://releases.aspose.com/tasks/net/).

2. 개발 환경  
   C# 프로그래밍 언어와 구성된 .NET 개발 환경에 대한 실무 지식이 있습니다.

3. Microsoft Project 파일 입력  
   유효한`.mpp` 변환 가능한 파일이 있습니다.

## 필수 네임스페이스 가져오기

코딩하기 전에 Aspose.Tasks 기능에 액세스하는 데 필요한 네임스페이스를 포함시킵니다. 

```csharp
using Aspose.Tasks;
using Aspose.Tasks.Saving;
using Aspose.Tasks.Visualization;
using System.Collections.Generic;
```

## 1단계: Microsoft Project 파일 로드

 시작하려면 다음을 로드하세요.`.mpp` 파일로 저장하다`Project` 객체. 바꾸기`"Your_Project_File_Path.mpp"` 입력 파일의 경로를 포함합니다.

```csharp
var project = new Project("Your_Project_File_Path.mpp");
```

## 2단계: PDF 저장 옵션 구성

출력 PDF를 사용자 정의하기 위한 옵션을 설정합니다. Aspose.Tasks for .NET은 페이지 렌더링, 레이아웃 및 기타 측면을 제어하는 유연성을 제공합니다.

```csharp
var options = new PdfSaveOptions
{
    RenderToSinglePage = false, // 모든 콘텐츠를 단일 페이지에 렌더링할지 여부
    Pages = new List<int>()     // PDF에 포함할 페이지
};
```

## 3단계: 페이지 수 결정

 사용하세요`PageCount` 프로젝트가 몇 페이지에 걸쳐 있는지 식별하는 속성입니다. 이는 특정 페이지를 포함할지 아니면 모두 내보낼지 결정하는 데 도움이 됩니다.

```csharp
Console.WriteLine("Total Pages: " + options.PageCount);
```

## 4단계: 내보낼 특정 페이지 선택(선택 사항)

 PDF에 포함될 정확한 페이지를 지정하려면 다음을 채우십시오.`Pages` 속성. 예를 들어, 페이지 1과 4를 내보내려면:

```csharp
options.Pages.Add(1);
options.Pages.Add(4);
```

## 5단계: 프로젝트 파일을 PDF로 저장

마지막으로 저장하세요`.mpp` 호출하여 PDF로 파일화`Save` 방법. 출력 파일 경로를 지정하고 구성된 옵션을 전달합니다.

```csharp
project.Save("Output_PDF_File_Path.pdf", options);
```

## 결론

Aspose.Tasks for .NET을 사용하여 Microsoft Project 파일을 PDF로 변환하면 매끄럽고 사용자 정의 가능한 경험이 보장됩니다. 특정 페이지 선택에서 일괄 내보내기 자동화에 이르기까지 이 도구는 개발자가 프로젝트 파일을 효과적으로 처리할 수 있도록 지원합니다.

## 자주 묻는 질문

### 내보낸 PDF의 모양을 사용자 정의할 수 있나요?
네, Aspose.Tasks를 사용하면 사용자의 특정 요구 사항에 맞게 글꼴, 색상 및 페이지 레이아웃을 사용자 정의할 수 있습니다.

###  변환이 가능할까요?`.mpp` files from older versions of Microsoft Project?
 Aspose.Tasks 지원`.mpp` Microsoft Project 2003 이상의 파일입니다.

### 모든 프로젝트 데이터를 단일 PDF 페이지에 렌더링하려면 어떻게 해야 하나요?
 설정하다`RenderToSinglePage` 의 속성`PdfSaveOptions` 반대하다`true`.

```csharp
options.RenderToSinglePage = true;
```

### 프로젝트 데이터를 다른 파일 형식으로 내보낼 수 있나요?
네, Aspose.Tasks는 Excel, HTML, PNG, JPEG와 같은 이미지 형식을 포함한 다양한 형식으로 내보내기를 지원합니다.

### Aspose.Tasks for .NET에 대한 무료 평가판이 있나요?
 네, 다운로드할 수 있습니다[무료 체험판은 여기를 클릭하세요](https://releases.aspose.com/).