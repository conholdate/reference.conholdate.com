---
title: C#를 사용하여 MHT 글꼴 사용자 지정 변경
linktitle: C#를 사용하여 MHT 글꼴 사용자 지정 변경
second_title: Aspose.Email .NET 이메일 처리 API
description: Aspose.Email for .NET을 사용하여 MHT 변환 중에 글꼴을 변경하는 방법을 알아보세요. 쉬운 사용자 지정을 위한 이 단계별 가이드를 따르세요.
type: docs
weight: 11
url: /ko/net/tutorials/email/mastering-email-header-manipulation/changing-mht-font-customization/
---
## 소개

웹 커뮤니케이션의 세계에서 MHT(MHTML) 파일은 이미지, 링크, 스타일이 포함된 웹 콘텐츠를 저장하고 공유하는 편리한 방법입니다. 하지만 글꼴을 변경하여 MHT 파일을 멋지게 만들어야 할 때는 어떻게 해야 할까요? Aspose.Email for .NET 덕분에 이 작업이 아주 쉬워졌습니다. 이 튜토리얼에서는 MHT 변환 중에 글꼴을 변경하는 과정을 단계별로 안내해 드리겠습니다. 이메일 서식을 처리하는 애플리케이션을 개발하든, 비즈니스에 맞게 문서를 사용자 지정하려는 경우, 이 가이드는 필요한 지식을 제공합니다.

## 필수 조건

코드를 살펴보기 전에 꼭 준비해야 할 몇 가지 필수 사항이 있습니다.

1. Visual Studio: C# 프로젝트 작업을 위해서는 IDE(통합 개발 환경)가 필요합니다.
2.  Aspose.Email for .NET 라이브러리: 라이브러리가 설치되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다.[링크](https://releases.aspose.com/email/net/).
3. .NET Framework: 프로젝트는 .NET Framework와 호환되어야 합니다. 일반적으로 .NET Core 이상 버전이 잘 작동합니다.

다 정렬했나요? 대단해요! 시작해 볼까요.

## 패키지 가져오기

먼저, 프로젝트가 필요한 네임스페이스를 사용하도록 설정되어 있는지 확인하세요. C# 파일 맨 위에 다음을 포함해야 합니다.

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Tools;
```

이 패키지를 사용하면 MHT 파일을 다루고 해당 내용을 수정하는 데 필요한 기능에 액세스할 수 있습니다.

이제 MHT 변환 중에 글꼴을 변경하는 데 필요한 단계를 살펴보겠습니다.

## 1단계: MHT 파일 로드

 가장 먼저 해야 할 일은 MHT 파일을 로드하는 것입니다.`MailMessage` 객체. 여기서 해당 콘텐츠에 접근하고 조작할 수 있습니다.

```csharp
MailMessage message = MailMessage.Load("input.mht", new MhtmlLoadOptions());
```

 설명: 여기,`"input.mht"` 는 MHT 파일에 대한 경로입니다.`MhtmlLoadOptions()`예를 들어, 첨부 파일이나 링크된 리소스를 다르게 처리하는 등 파일 로드 방법을 구성할 수 있습니다.

## 2단계: 대체 뷰를 통해 반복

MHT 파일에는 종종 여러 개의 대체 뷰가 있는데, 특히 HTML 콘텐츠가 포함되어 있는 경우 더욱 그렇습니다. 수정하려는 뷰를 찾으려면 이러한 뷰를 반복해야 합니다.

```csharp
foreach (var alternateView in message.AlternateViews)
{
    if (alternateView.ContentType.MediaType == "text/html")
    {
        var htmlView = (AlternateView)alternateView;
        var linkedResources = htmlView.LinkedResources;
```

 설명: 각각을 확인하고 있습니다`AlternateView` HTML 유형인지 확인하려면. 그렇다면 액세스할 수 있습니다.`LinkedResources`HTML에 링크된 모든 글꼴이 일반적으로 저장되는 곳입니다.

## 3단계: 글꼴 식별 및 사용자 지정

이제 링크된 리소스에 액세스할 수 있으므로 어떤 리소스가 글꼴인지 식별하고 필요에 따라 사용자 정의할 수 있습니다.

```csharp
foreach (var linkedResource in linkedResources)
{
    if (linkedResource.ContentType.MediaType == "application/x-font-ttf")
    {
        linkedResource.ContentType.Name = "Arial";  // 원하는 글꼴로 변경
        linkedResource.TransferEncoding = TransferEncoding.Base64;  // 올바르게 인코딩되었는지 확인하세요
    }
}
```

 설명: 이 루프는 링크된 리소스의 콘텐츠 유형이 TrueType 글꼴인지 확인합니다. 일치하면 글꼴 이름을 원하는 대로 변경할 수 있습니다(이 예에서는 "Arial").`TransferEncoding`문서가 저장될 때 글꼴 데이터가 올바르게 인코딩되도록 설정해야 합니다.

## 4단계: 업데이트된 MHT 파일 저장

글꼴을 사용자 지정한 후에는 수정된 MHT 파일을 저장할 차례입니다. 파일의 무결성을 유지하려면 올바른 저장 옵션을 사용해야 합니다.

```csharp
message.Save("output.mht", SaveOptions.DefaultMhtml);
```

 설명: 이 코드 줄에서`"output.mht"` 업데이트된 콘텐츠를 저장할 파일의 이름입니다. 사용`SaveOptions.DefaultMhtml` 새로운 파일이 MHT 형식을 유지하도록 합니다.

## 결론

MHT 파일에서 글꼴을 변경하면 문서의 모양과 느낌이 크게 향상될 수 있습니다. Aspose.Email for .NET을 활용하면 몇 줄의 코드만으로 MHT 파일을 쉽게 로드하고, 내용을 수정하고, 변경 사항을 저장할 수 있습니다. 개인 프로젝트나 대규모 애플리케이션을 작업하든 이러한 기술을 숙달하면 정보를 표현하는 방식을 개선할 수 있습니다.

## 자주 묻는 질문

### MHT 형식이란 무엇인가요?
MHT는 HTML 문서, 이미지 및 기타 리소스를 단일 파일에 저장하는 웹 페이지 아카이브 형식입니다.

### Aspose를 사용하여 MHT 파일의 다른 측면을 변경할 수 있나요?
물론입니다! Aspose.Email을 사용하면 첨부 파일, 헤더 등을 포함하여 MHT 파일의 거의 모든 측면을 수정할 수 있습니다.

### .NET용 Aspose.Email은 무료인가요?
 Aspose는 무료 체험판을 제공하지만 전체 버전에는 라이센스가 필요합니다. 임시 라이센스는 다음에서 받을 수 있습니다.[여기](https://purchase.aspose.com/temporary-license/).

### Aspose.Email에 대한 추가 문서는 어디에서 찾을 수 있나요?
 포괄적인 문서와 예제는 다음에서 찾을 수 있습니다.[Aspose 이메일 문서 페이지](https://reference.aspose.com/email/net/).

### Aspose를 사용하는 동안 문제가 발생하면 어떻게 해야 하나요?
 문제가 발생하면 지원을 요청할 수 있습니다.[Aspose 지원 포럼](https://forum.aspose.com/c/email/12/).