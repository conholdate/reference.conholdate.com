---
title: Aspose.Email for .NET을 사용하여 이메일 전환 진행 상황 추적
linktitle: Aspose.Email for .NET을 사용하여 이메일 전환 진행 상황 추적
second_title: Aspose.Email .NET 이메일 처리 API
description: Aspose.Email for .NET을 사용하여 C#에서 이메일 전환 진행 상황을 추적하는 방법을 단계별로 알아보세요. 이 자세한 튜토리얼로 프로젝트 효율성을 높이세요.
type: docs
weight: 12
url: /ko/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## 소개

이메일 문서를 효율적으로 관리하려면 종종 변환 진행 상황을 추적해야 합니다. Aspose.Email for .NET은 이를 달성하기 위한 강력한 도구를 제공하여 개발자가 이메일 작업을 원활하게 처리할 수 있도록 합니다. 이 튜토리얼은 C#에서 이메일 문서 변환 진행 상황을 추적하는 방법을 자세히 살펴보고 이해하기 쉽도록 프로세스를 단계별로 분석합니다.  

## 필수 조건  

튜토리얼을 시작하기에 앞서 모든 것이 설정되어 있는지 확인해 보겠습니다.  

1.  .NET용 Aspose.Email: 다운로드 및 설치[.NET용 Aspose.Email](https://releases.aspose.com/email/net/) 도서관.  
2. 개발 환경: Visual Studio나 기타 .NET 호환 IDE를 설치합니다.  
3. .NET Framework: .NET Framework 4.5 이상이 설치되어 있는지 확인하세요.  
4.  임시 면허: 취득을 고려하세요[임시 면허](https://purchase.aspose.com/temporary-license/) Aspose.Email의 모든 기능을 살펴보세요.  
5.  샘플 이메일 파일: 준비`.eml` 파일(예:`test.eml`)을 샘플로 사용합니다.  

## 패키지 가져오기  

프로젝트에서 Aspose.Email을 사용하려면 필요한 네임스페이스를 가져와야 합니다. 파일 맨 위에 다음 using 문을 추가합니다.  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## 1단계: 프로젝트 설정  

Visual Studio에서 새 C# 콘솔 애플리케이션을 만드는 것으로 시작합니다. 이는 이메일 문서 전환 추적을 구현하는 기반이 됩니다.  
  
1. Visual Studio를 열고 새 콘솔 애플리케이션 프로젝트를 만듭니다.  
2. Aspose.Email NuGet 패키지를 설치하세요:  
```sh
Install-Package Aspose.Email
```  
3.  추가하다`.eml` 프로젝트 디렉토리에 파일을 추가합니다.  

## 2단계: 이메일 파일 로드  

 이제 이메일 파일을 로드하세요.`MailMessage` 객체. 이것은 이메일 데이터 작업의 첫 번째 단계입니다.  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`: 이메일 파일이 있는 디렉토리를 지정합니다.  
- `MailMessage.Load` : 읽습니다`.eml` 파일을 저장하고 추가 작업을 위해 준비합니다.  

## 3단계: 메모리 스트림 초기화  

 다음으로, 다음을 생성합니다.`MemoryStream` 변환된 이메일 데이터를 일시적으로 저장하는 객체입니다.  
 
```csharp
MemoryStream ms = new MemoryStream();
```

 에이`MemoryStream` 여기서는 데이터를 디스크에 직접 저장하지 않고 변환 프로세스의 출력을 관리하는 데 사용됩니다.  

## 4단계: 변환 옵션 정의  

 설정하다`EmlSaveOptions` 사용자 정의 진행률 핸들러를 사용하여 전환 진행률을 추적합니다.  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`: 출력 형식을 지정합니다.  
- `CustomProgressHandler`: 진행 상황을 모니터링하기 위한 사용자 지정 처리기 함수를 할당합니다.  

## 5단계: 이메일을 메모리 스트림에 저장  

저장하다`MailMessage` 지정된 옵션을 사용하여 개체를 생성하여 진행률 추적 기능을 활성화합니다.  
 
```csharp
msg.Save(ms, opt);
```
 
이 단계에서는 이메일 변환 프로세스가 시작되고 진행률 처리기로 업데이트가 전송됩니다.  

## 6단계: 진행률 핸들러 구현  

 정의하다`ShowEmlConversionProgress` 진행 상황 업데이트를 처리하고 콘솔에 표시하는 방법입니다.  
 
```csharp
private static void ShowEmlConversionProgress(ProgressEventHandlerInfo info)
{
    int total;
    int saved;

    switch (info.EventType)
    {
        case ProgressEventType.MimeStructureCreated:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimeStructureCreated - TotalMimePartCount: {total}");
            Console.WriteLine($"MimeStructureCreated - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.MimePartSaved:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimePartSaved - TotalMimePartCount: {total}");
            Console.WriteLine($"MimePartSaved - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.SavedToStream:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"SavedToStream - TotalMimePartCount: {total}");
            Console.WriteLine($"SavedToStream - SavedMimePartCount: {saved}");
            break;
    }
}
```
 
- `ProgressEventHandlerInfo`: 변환 과정에 대한 세부정보를 제공합니다.  
-  케이스 전환: 변환의 다양한 단계를 처리합니다.`MimeStructureCreated`, `MimePartSaved` , 그리고`SavedToStream`.  

### 무엇을 기대해야 하나요?  
변환이 진행됨에 따라 다음과 같은 자세한 업데이트가 콘솔에 인쇄됩니다.  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## 결론  

Aspose.Email for .NET 덕분에 C#에서 이메일 문서의 변환 진행 상황을 추적하는 것이 그 어느 때보다 쉬워졌습니다. 이 튜토리얼을 따라하면 이메일 파일을 로드하고, 진행 상황 처리기를 설정하고, 전체 프로세스를 모니터링하면서 이메일 데이터를 저장하는 방법을 배웠습니다. 이 기능을 사용하면 이메일 문서 작업 중에 정보를 얻고 제어할 수 있습니다.  

## 자주 묻는 질문  

###  이 코드를 다른 형식에도 사용할 수 있나요?`.eml`?  
 네, 수정합니다`MailMessageSaveType`MSG나 MHTML과 같은 다른 형식에 맞게.  

### 대용량 이메일 파일을 어떻게 처리하나요?  
 사용을 고려하세요`FileStream` 대신에`MemoryStream` 대용량 파일을 처리할 때 더 나은 성능을 위해.  

### 임시 면허란 무엇이고, 어떻게 받을 수 있나요?  
 임시 라이선스를 사용하면 라이브러리의 모든 기능을 무료로 평가할 수 있습니다. 받기[여기](https://purchase.aspose.com/temporary-license/).  

### 이 코드를 웹 애플리케이션에 통합할 수 있나요?  
네, 해당 코드는 ASP.NET이나 비슷한 프레임워크를 사용하는 웹 애플리케이션과 호환됩니다.  

### 추가 자료는 어디에서 찾을 수 있나요?  
 확인해보세요[선적 서류 비치](https://reference.aspose.com/email/net/) 또는 방문하세요[지원 포럼](https://forum.aspose.com/c/email/12/) 도움을 요청하세요.  