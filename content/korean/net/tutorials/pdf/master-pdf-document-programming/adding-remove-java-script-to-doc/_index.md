---
title: PDF 문서에 Javascript 제거 추가
linktitle: PDF 문서에 Javascript 제거 추가
second_title: .NET API 참조를 위한 Aspose.PDF
description: 이 포괄적인 가이드에서는 사용자 정의 동작을 추가하고, 계산이나 검증을 동적으로 수행하고, 다른 소프트웨어 애플리케이션과 통합하는 방법을 보여줍니다.
type: docs
weight: 30
url: /ko/net/tutorials/pdf/master-pdf-document-programming/adding-remove-java-script-to-doc/
---
## 소개

이 포괄적인 가이드에서는 .NET용 Aspose.PDF의 세계를 탐구하고 PDF 문서에 사용자 정의 JavaScript 기능을 추가하는 잠재력을 최대한 활용합니다. 이 강력한 기능을 사용하면 동적 요소를 통합하고, 사용자 경험을 향상시키고, 워크플로를 간소화할 수 있습니다.

## 필수 조건

따라하려면 다음이 필요합니다.

1. 프로젝트에 설치된 .NET용 Aspose.PDF(다운로드)[.NET용 Aspose.PDF 다운로드 페이지](https://releases.aspose.com/pdf/net/))
2. 도서관을 이용할 수 있는 유효한 라이센스
3. AC# IDE 또는 텍스트 편집기

## 패키지 가져오기

시작하려면 필요한 네임스페이스를 프로젝트로 가져옵니다.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
using System.Collections;
```

## 1단계: 새 PDF 문서 초기화

새 PDF 문서를 만들어 캔버스에 추가하세요.

```csharp
Document doc = new Document();
doc.Pages.Add();
```

여기서 JavaScript를 많이 사용한 PDF 구축을 시작할 수 있습니다.

## 2단계: PDF에 JavaScript 추가

 다음을 사용하여 문서에 JavaScript 함수를 삽입하세요.`doc.JavaScript` 컬렉션. 다음은 예입니다.

```csharp
doc.JavaScript["func1"] = "function func1() { console.log('Hello'); }";
doc.JavaScript["func2"] = "function func2() { alert('This is a test'); }";
```

## 3단계: JavaScript로 PDF 저장

업데이트된 문서를 디스크에 저장하세요.

```csharp
doc.Save(dataDir + "AddJavascript.pdf");
```

이제 기존 PDF 내의 JavaScript 코드에 액세스하여 수정할 수 있습니다.

## 4단계: 기존 PDF에서 JavaScript 로드 및 보기

 JavaScript를 포함하는 PDF 파일을 로드하고 다음을 사용하여 키에 액세스합니다.`Keys` 재산:

```csharp
Document doc1 = new Document(dataDir + "AddJavascript.pdf");
IList keys = (System.Collections.IList)doc1.JavaScript.Keys;
```

## 5단계: JavaScript 함수 표시

JavaScript 키를 반복하고 해당 코드를 콘솔에 인쇄합니다.

```csharp
Console.WriteLine("=============================== ");
foreach (string key in keys)
{
    Console.WriteLine(key + " ==> " + doc1.JavaScript[key]);
}
```

이는 현재 어떤 JavaScript 함수가 존재하는지 확인하는 방법을 보여줍니다.

## 6단계: PDF에서 JavaScript 제거

원하는 JavaScript 함수를 해당 이름으로 찾아 제거하세요.

```csharp
doc1.JavaScript.Remove("func1");
Console.WriteLine("Key 'func1' removed ");
```

나머지 함수를 다시 인쇄하여 함수가 성공적으로 삭제되었는지 확인하세요.

## 결론

이 포괄적인 가이드에서는 Aspose.PDF for .NET의 사용자 정의 가능한 JavaScript 기능의 힘을 활용하는 방법을 알아보았습니다. 이 기능을 사용하면 동적 PDF를 만들고, 사용자 경험을 향상시키고, 워크플로를 간소화할 수 있습니다. 이러한 단계를 숙지하고 라이브러리의 기능을 더욱 탐색하면 애플리케이션에서 새로운 가능성을 여는 데 큰 도움이 될 것입니다.

## 자주 묻는 질문

### 하나의 PDF에 여러 개의 JavaScript 기능을 추가할 수 있나요?
 네! 필요에 따라 JavaScript 함수를 추가할 수 있습니다.`doc.JavaScript` 수집.

### 존재하지 않는 JavaScript 함수를 제거하려고 하면 어떻게 되나요?
 해당 기능이 존재하지 않는 경우`Remove` 메서드는 오류를 발생시키지 않지만 아무것도 제거하지도 않습니다. 존재하지 않는 함수를 처리하려면 추가 오류 처리를 추가하거나 코드를 수정하여 무시할 수 있습니다.

### PDF를 여는 즉시 JavaScript를 실행할 수 있나요?
네! JavaScript를 구성하여 문서를 열거나 버튼을 클릭하는 것과 같은 특정 트리거에서 실행되도록 할 수 있습니다.

### PDF에 JavaScript를 추가한 후에 편집할 수 있나요?
네, 기존 PDF를 로드하고, JavaScript에 액세스하고, 코드를 수정한 다음 문서를 다시 저장할 수 있습니다.

### JavaScript를 제거하면 나머지 PDF 콘텐츠에 영향을 미칩니까?
아니요, JavaScript를 제거하면 스크립트에만 영향을 미칩니다. PDF의 내용은 변경되지 않습니다.