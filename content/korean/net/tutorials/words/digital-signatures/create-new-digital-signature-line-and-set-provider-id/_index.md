---
title: 새로운 디지털 서명 줄을 만들고 공급자 ID를 설정합니다.
linktitle: 새로운 디지털 서명 줄을 만들고 공급자 ID를 설정합니다.
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에 서명 줄을 프로그래밍 방식으로 추가하는 방법을 알아보세요. 이 포괄적인 가이드는 개발 환경 설정부터 서명 줄 삽입 및 문서에 안전하게 서명하는 것까지 모든 것을 다룹니다.
type: docs
weight: 10
url: /ko/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## 소개

안녕하세요, 기술 매니아 여러분! Word 문서에 서명 줄을 자동으로 포함하고 싶었던 적이 있나요? 오늘은 Aspose.Words for .NET을 사용하여 이를 달성하는 방법을 알아보겠습니다. 이 단계별 가이드에서는 서명 줄을 만들고 공급자 ID를 설정하는 방법을 안내하여 문서 처리 작업을 보다 효율적이고 간소화합니다.

## 필수 조건

시작하기에 앞서 모든 것이 설정되어 있는지 확인해 보겠습니다.

1.  .NET용 Aspose.Words: 아직 설치하지 않았다면 다운로드하세요.[여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio나 C# 개발 설정을 사용하세요.
3. .NET Framework: 컴퓨터에 .NET Framework가 설치되어 있는지 확인하세요.
4. PFX 인증서: 문서에 서명하려면 PFX 인증서가 필요한데, 신뢰할 수 있는 인증 기관에서 얻을 수 있습니다.

## 필요한 네임스페이스 가져오기

시작하려면 필요한 네임스페이스를 C# 프로젝트로 가져오세요.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

이제 새로운 서명란을 만들고 공급자 ID를 설정하는 방법에 대해 자세히 알아보겠습니다.

## 1단계: 새 문서 만들기

먼저, 서명란의 캔버스 역할을 할 새 Word 문서를 만들어야 합니다.

```csharp
// 문서 디렉토리의 경로를 지정하세요.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 여기서 우리는 새로운 것을 초기화합니다`Document` 그리고`DocumentBuilder`, 이를 통해 요소를 쉽게 추가할 수 있습니다.

## 2단계: 서명란 옵션 정의

다음으로 서명자의 이름, 직함, 이메일 및 기타 관련 세부 정보를 포함하여 서명란에 대한 옵션을 정의합니다.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

이러한 옵션을 사용하면 서명란을 개인화하여 명확하고 전문적인 느낌으로 만들 수 있습니다.

## 3단계: 서명란 삽입

옵션이 준비되었으므로 이제 문서에 서명 줄을 삽입할 수 있습니다.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 그만큼`InsertSignatureLine`이 방법은 서명 줄을 추가하고, 여기에 고유한 공급자 ID를 할당합니다.

## 4단계: 문서 저장

서명란을 삽입한 후 문서를 저장해 보겠습니다.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

이렇게 하면 새로 추가된 서명 줄이 포함된 문서가 저장됩니다.

## 5단계: 서명 옵션 설정

이제 서명 줄 ID, 공급자 ID, 주석, 서명 시간을 포함한 서명 옵션을 구성해 보겠습니다.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

이러한 설정을 통해 문서에 올바른 세부 정보가 서명되었는지 확인할 수 있습니다.

## 6단계: 인증서 보유자 생성

문서에 서명하려면 PFX 인증서를 사용하여 인증서 보유자를 만들어야 합니다.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 바꾸다`"morzal.pfx"` 실제 인증서 파일 이름과`"aw"` 인증서 비밀번호를 입력하세요.

## 7단계: 문서 서명

마지막으로 디지털 서명 유틸리티를 사용하여 문서에 서명합니다.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

이 프로세스에서는 문서에 서명하고 새 파일로 저장합니다.

## 결론

축하합니다! Aspose.Words for .NET을 사용하여 Word 문서에서 서명 줄을 성공적으로 만들고 공급자 ID를 설정했습니다. 이 강력한 라이브러리는 문서 처리 작업을 간소화하여 워크플로를 더 효율적으로 만듭니다. 시도해 보고 프로젝트를 어떻게 향상시킬 수 있는지 확인하세요!

## 자주 묻는 질문

### 서명란의 모양을 사용자 지정할 수 있나요?
 물론입니다! 다양한 옵션을 조정할 수 있습니다.`SignatureLineOptions` 귀하의 스타일과 요구 사항에 맞게.

### PFX 인증서가 없으면 어떻게 하나요?
디지털 서명 문서에 필수적이므로 신뢰할 수 있는 인증 기관에서 인증서를 받아야 합니다.

### 문서에 여러 개의 서명줄을 추가할 수 있나요?
네, 다양한 옵션으로 삽입 과정을 반복하여 여러 개의 서명 줄을 추가할 수 있습니다.

### Aspose.Words for .NET은 .NET Core와 호환됩니까?
네, Aspose.Words for .NET은 .NET Core를 지원하므로 다양한 개발 환경에 적합합니다.

### 디지털 서명은 얼마나 안전한가요?
Aspose.Words로 생성된 디지털 서명은 유효하고 신뢰할 수 있는 인증서를 사용하는 경우 매우 안전합니다.