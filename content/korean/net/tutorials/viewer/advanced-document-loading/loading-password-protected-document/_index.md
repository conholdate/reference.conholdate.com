---
title: 암호로 보호된 문서 로딩
linktitle: 암호로 보호된 문서 로드
second_title: GroupDocs.Viewer .NET API
description: GroupDocs.Viewer를 사용하여 .NET 애플리케이션에 문서 보기 기능을 손쉽게 통합하는 방법을 알아보세요. 이 튜토리얼은 포괄적이고 단계별 가이드를 제공합니다.
type: docs
weight: 12
url: /ko/net/tutorials/viewer/advanced-document-loading/loading-password-protected-document/
---
## 소개

디지털 환경에서 다양한 문서 형식을 관리하고 볼 수 있는 기능은 기업과 개인에게 매우 중요합니다. .NET용 GroupDocs.Viewer는 개발자가 문서 보기 기능을 애플리케이션에 손쉽게 통합할 수 있는 강력한 솔루션을 제공합니다. 이 튜토리얼은 암호로 보호된 문서를 단계별로 로드하는 과정을 안내하여 프로젝트에서 이 기능을 원활하게 구현할 수 있도록 합니다.

## 필수 조건

시작하기 전에 다음 사항이 있는지 확인하세요.

1.  .NET용 GroupDocs.Viewer 설치: 여기에서 다운로드하세요.[웹사이트](https://releases.groupdocs.com/viewer/net/).
2. 암호로 보호된 문서: 테스트를 위해 암호로 보호된 문서를 준비해 두세요.

## 필요한 네임스페이스 가져오기

프로젝트에 필요한 네임스페이스를 가져오는 것으로 시작합니다.

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## 1단계: 출력 디렉토리 정의

렌더링된 출력을 저장할 위치를 지정하세요.

```csharp
string outputDirectory = "Your Document Directory";
```
 교체를 꼭 해주세요`"Your Document Directory"` 실제로 사용하고자 하는 경로와 함께 사용합니다.

## 2단계: 페이지 파일 경로 형식 설정

렌더링된 각 페이지의 파일 경로에 대한 형식을 정의합니다.

```csharp
string pageFilePathFormat = Path.Combine(outputDirectory, "page_{0}.html");
```

 이렇게 하면 다음과 같은 경로가 생성됩니다.`"Your Document Directory/page_1.html"`, `"Your Document Directory/page_2.html"`, 등.

## 3단계: 로드 옵션 구성

암호를 포함하여 암호로 보호된 문서에 대한 로드 옵션을 설정합니다.

```csharp
LoadOptions loadOptions = new LoadOptions
{
    Password = "12345"  // 문서의 비밀번호로 바꾸세요
};
```

## 4단계: 뷰어 초기화

문서와 로드 옵션을 사용하여 GroupDocs.Viewer 인스턴스를 만듭니다.

```csharp
using (Viewer viewer = new Viewer("Path_to_your_document", loadOptions))
{
    // 다음 단계에서 보기 옵션에 대한 코드가 추가됩니다.
}
```
 교체를 꼭 해주세요`"Path_to_your_document"` 문서의 실제 경로를 입력합니다.

## 5단계: HTML 보기 옵션 구성

내장된 리소스로 문서를 렌더링하기 위한 HTML 보기 옵션을 설정합니다.

```csharp
HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources(pageFilePathFormat);
```

## 6단계: 문서 렌더링

이제 구성된 뷰어와 보기 옵션을 사용하여 문서를 렌더링합니다.

```csharp
viewer.View(options);
```

## 7단계: 성공 메시지 표시

마지막으로, 문서가 성공적으로 렌더링되었음을 사용자에게 알립니다.

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## 결론

이 튜토리얼에서는 GroupDocs.Viewer for .NET을 사용하여 암호로 보호된 문서를 로드하는 방법을 살펴보았습니다. 이러한 단계를 따르면 개발자는 이 기능을 애플리케이션에 쉽게 통합하여 사용자가 보호된 문서를 손쉽게 볼 수 있습니다.

## 자주 묻는 질문

### GroupDocs.Viewer는 암호로 보호된 문서 외에도 다른 문서 형식을 처리할 수 있나요?

네, GroupDocs.Viewer는 PDF, DOCX, XLSX, PPTX 등 다양한 형식을 지원합니다.

### GroupDocs.Viewer는 .NET Core와 호환됩니까?

물론입니다! GroupDocs.Viewer는 .NET Framework와 .NET Core 환경 모두와 호환됩니다.

### 문서의 렌더링 옵션을 사용자 정의할 수 있나요?

네, GroupDocs.Viewer는 다양한 렌더링 옵션을 제공하여 사용자의 요구 사항에 맞게 보기 환경을 맞춤 설정할 수 있습니다.

### GroupDocs.Viewer는 문서 주석을 지원합니까?

네, 문서 주석을 지원하여 사용자가 댓글, 강조 표시 및 기타 메모를 추가할 수 있습니다.

### GroupDocs.Viewer의 평가판이 있나요?

 네, 무료 체험판을 받으실 수 있습니다.[웹사이트](https://releases.groupdocs.com/).