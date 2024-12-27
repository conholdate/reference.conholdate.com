---
title: GroupDocs.Signature를 사용하여 메타데이터가 있는 PDF 서명 가이드
linktitle: 메타데이터가 있는 PDF 서명 가이드
second_title: GroupDocs.Signature .NET API
description: GroupDocs.Signature for .NET을 사용하여 메타데이터로 서명하여 PDF 문서의 보안과 추적성을 강화하는 방법을 알아보세요. 이 포괄적인 튜토리얼은 명확한 정보를 제공합니다.
type: docs
weight: 11
url: /ko/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## 소개

이 튜토리얼에서는 GroupDocs.Signature for .NET을 사용하여 PDF 문서에 서명하고 메타데이터를 추가하는 방법을 알아봅니다. 메타데이터를 추가하면 작성자, 생성 날짜, 문서 ID 등과 같은 필수 정보를 제공하여 문서가 향상됩니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1.  .NET용 GroupDocs.Signature: 여기에서 다운로드하세요.[여기](https://releases.groupdocs.com/signature/net/).
2. PDF 문서: 서명을 위한 샘플 PDF 파일을 준비하세요.
3. C# 프로그래밍에 대한 기본 지식: 코드 예제를 이해하려면 C# 구문에 대한 지식이 필요합니다.

## 네임스페이스 가져오기

필요한 클래스와 메서드에 액세스하려면 필요한 네임스페이스를 가져오는 것으로 시작합니다.

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## 1단계: PDF 문서 로드

서명하려는 PDF 문서의 경로를 지정하세요:

```csharp
string filePath = "sample.pdf";
```

## 2단계: 출력 파일 경로 지정

메타데이터가 포함된 서명된 PDF가 저장될 위치를 정의합니다.

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## 3단계: 서명 인스턴스 생성

 초기화`Signature` PDF 문서 경로가 있는 인스턴스:

```csharp
using (Signature signature = new Signature(filePath))
{
    // 서명 관련 코드는 여기에 있습니다.
}
```

## 4단계: 메타데이터 옵션 정의

 만들다`MetadataSignOptions` 그리고 값과 함께 메타데이터 필드를 추가합니다.

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) // 문자열 값
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       // DateTime 값
    .Add(new PdfMetadataSignature("DocumentId", 123456))            // 정수값
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         // 두 배의 값
    .Add(new PdfMetadataSignature("Amount", 123.456M))              // 10진수 값
    .Add(new PdfMetadataSignature("Total", 123.456F));              // 부동 소수점 값
```

## 5단계: 문서 서명

지정된 메타데이터 옵션으로 PDF 문서에 서명하고 서명된 문서를 저장합니다.

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## 결론

이 튜토리얼에서는 GroupDocs.Signature for .NET을 사용하여 메타데이터로 PDF 문서에 서명하는 방법을 다루었습니다. 이러한 단계를 따르면 귀중한 메타데이터로 PDF 파일을 쉽게 풍부하게 만들어 추적성과 유용성을 개선할 수 있습니다.

## 자주 묻는 질문

### PDF 문서에 사용자 정의 메타데이터 필드를 추가할 수 있나요?

네, .NET용 GroupDocs.Signature를 사용하여 필드 이름과 해당 값을 지정하여 사용자 지정 메타데이터 필드를 추가할 수 있습니다.

### .NET용 GroupDocs.Signature는 모든 버전의 .NET Framework와 호환됩니까?

.NET용 GroupDocs.Signature는 다양한 버전의 .NET Framework와 호환되어 유연성과 통합 용이성을 보장합니다.

### GroupDocs.Signature는 PDF 외에 다른 문서 형식의 서명을 지원합니까?

네, GroupDocs.Signature는 Word, Excel, PowerPoint 등 다양한 문서 형식을 지원합니다.

### GroupDocs.Signature for .NET을 사용하여 여러 문서에 대량으로 서명할 수 있습니까?

물론입니다! 파일 목록을 반복하고 서명 프로세스를 프로그래밍 방식으로 적용하여 여러 문서에 대량으로 서명할 수 있습니다.

### GroupDocs.Signature 사용자에게 기술 지원을 제공할 수 있나요?

 네, GroupDocs는 포럼을 통해 전담 기술 지원을 제공합니다. 지원 포럼에 액세스할 수 있습니다.[여기](https://forum.groupdocs.com/c/signature/13).