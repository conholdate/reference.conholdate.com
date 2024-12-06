---
title: Word에서 사용자 정의 문서 속성 추가
linktitle: Word에서 사용자 정의 문서 속성 추가
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 사용자 지정 문서 속성으로 Word 문서를 개선하는 방법을 알아보세요. 이 포괄적인 가이드는 프로세스를 안내합니다.
type: docs
weight: 10
url: /ko/net/tutorials/words/mastering-document-properties/adding-custom-document-properties-in-word/
---
## 소개

환영합니다! Aspose.Words for .NET을 탐색하고 Word 파일에 사용자 지정 문서 속성을 추가하는 방법을 알고 싶다면 올바른 곳에 왔습니다. 사용자 지정 속성은 기본 제공 속성에서 다루지 않는 추가 메타데이터를 저장하는 데 매우 중요합니다. 문서 승인, 개정 번호 또는 특정 날짜를 추적해야 하는 경우 사용자 지정 속성이 도움이 될 수 있습니다. 이 자습서에서는 Aspose.Words for .NET을 사용하여 이러한 속성을 원활하게 추가하는 단계를 안내합니다. 시작해 봅시다!

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

1.  Aspose.Words for .NET 라이브러리: 다운로드[여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 IDE.
3. C#에 대한 기본 지식: C#과 .NET에 대한 지식이 있으면 도움이 됩니다.
4.  샘플 문서: 이름이 지정된 샘플 Word 문서를 준비하세요.`Properties.docx` 수정을 위해서.

## 네임스페이스 가져오기

Aspose.Words의 기능에 액세스하려면 코드 시작 부분에 필요한 네임스페이스를 가져와야 합니다.

```csharp
using System;
using Aspose.Words;
```

## 1단계: 문서 경로 설정

 다음으로 Word 문서 경로를 정의해 보겠습니다. 이 단계는 Word 문서를 찾고 여는 데 필수적입니다.`Properties.docx` 파일.

```csharp
// 문서 디렉토리의 경로를 지정하세요.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

 교체를 꼭 해주세요`"YOUR DOCUMENT DIRECTORY"` 문서의 실제 경로를 입력합니다.

## 2단계: 사용자 정의 문서 속성 액세스

이제 사용자 정의 메타데이터가 저장될 Word 문서의 사용자 정의 문서 속성에 액세스해 보겠습니다.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

이 줄을 통해 작업할 사용자 정의 속성 컬렉션에 액세스할 수 있습니다.

## 3단계: 기존 속성 확인

새로운 속성을 추가하기 전에 중복을 피하기 위해 해당 속성이 이미 존재하는지 확인하는 것이 좋습니다.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

이 코드는 "Authorized" 속성이 이미 존재하는지 확인합니다. 그렇다면 메서드가 일찍 종료되어 중복을 방지합니다.

## 4단계: 부울 속성 추가

문서가 승인되었는지 여부를 나타내는 사용자 지정 부울 속성을 추가해 보겠습니다.

```csharp
customDocumentProperties.Add("Authorized", true);
```

 이 줄은 "Authorized"라는 속성을 추가하고 해당 값을 다음과 같이 설정합니다.`true`.

## 5단계: 문자열 속성 추가

다음으로, 문자열 속성을 추가하여 문서를 누가 승인했는지 지정합니다.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

"John Smith"를 원하는 이름으로 바꿔도 됩니다.

## 6단계: 날짜 속성 추가

문서가 승인된 시점을 추적하려면 날짜 속성을 추가해 보겠습니다.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

 이 줄은 "인증 날짜"라는 속성을 추가하고 이를 사용하여 오늘 날짜를 지정합니다.`DateTime.Today`.

## 7단계: 개정 번호 추가

버전 제어를 위해 문서의 개정 번호를 추적하는 속성을 추가할 수 있습니다.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

여기에 문서의 현재 개정 번호를 보관하는 "승인된 개정" 속성을 추가합니다.

## 8단계: 숫자 속성 추가

마지막으로 예산 수치와 같은 승인된 금액을 저장하기 위해 숫자형 속성을 추가해 보겠습니다.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

 이 줄은 "Authorized Amount"라는 속성을 값을 추가합니다.`123.45`필요에 따라 이 숫자를 조정할 수 있습니다.

## 결론

축하합니다! Aspose.Words for .NET을 사용하여 Word 문서에 사용자 지정 문서 속성을 성공적으로 추가했습니다. 이러한 속성은 권한 세부 정보, 개정 번호 또는 특정 금액을 추적하든 요구 사항에 맞게 조정된 메타데이터를 저장하는 강력한 방법입니다.

## 자주 묻는 질문

### 사용자 정의 문서 속성이란 무엇인가요?
사용자 지정 문서 속성은 기본 제공 속성에서 다루지 않는 추가 정보를 저장하기 위해 Word 문서에 추가할 수 있는 메타데이터입니다.

### 문자열과 숫자 외에 다른 속성을 추가할 수 있나요?
네, 부울 값, 날짜, 심지어 사용자 정의 객체까지 다양한 유형의 속성을 추가할 수 있습니다.

### Word 문서에서 이러한 속성에 어떻게 액세스할 수 있나요?
Aspose.Words를 사용하여 사용자 지정 속성에 프로그래밍 방식으로 액세스하거나 문서 속성을 통해 Word에서 직접 볼 수 있습니다.

### 사용자 정의 속성을 편집하거나 삭제할 수 있나요?
물론입니다! Aspose.Words에서 제공하는 메서드를 사용하여 사용자 지정 속성을 쉽게 편집하거나 삭제할 수 있습니다.

### 사용자 정의 속성을 문서 필터링에 사용할 수 있나요?
네! 사용자 지정 속성은 특정 메타데이터를 기준으로 문서를 분류하고 필터링하는 데 매우 좋습니다.