---
title: 서명된 Excel 파일에 새 디지털 서명 추가
linktitle: 서명된 Excel 파일에 새 디지털 서명 추가
second_title: Aspose.Cells .NET Excel 처리 API
description: Aspose.Cells for .NET을 사용하여 기존 서명된 Excel 파일에 새 디지털 서명을 추가하는 방법을 알아보세요. 이 포괄적인 가이드는 모든 필수 조건, 단계별 지침 및 코드 예제를 다룹니다.
type: docs
weight: 12
url: /ko/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## 소개

오늘날의 디지털 환경에서 문서의 진위성과 무결성을 보장하는 것은 그 어느 때보다 중요합니다. 디지털 서명은 문서가 변경되지 않았고 합법적인 출처에서 온 것이라는 것을 확인하는 신뢰할 수 있는 방법을 제공합니다. .NET에서 Excel 파일을 사용하고 이미 서명된 파일에 새 디지털 서명을 추가해야 하는 경우 이 가이드가 도움이 될 것입니다! Aspose.Cells for .NET을 사용하여 기존에 서명된 Excel 파일에 디지털 서명을 추가하는 프로세스를 안내해 드리겠습니다.

## 필수 조건

구현에 들어가기 전에 다음 사항이 있는지 확인하세요.

1.  .NET용 Aspose.Cells: Aspose.Cells를 다운로드하여 설치하세요.[릴리스 페이지](https://releases.aspose.com/cells/net/).
2. .NET Framework: 컴퓨터에 .NET Framework가 설치되어 있고 기본 .NET 프로그래밍 개념을 알고 있는지 확인하세요.
3. 디지털 인증서: .pfx 형식의 유효한 디지털 인증서를 얻으세요. 테스트를 위해 자체 서명 인증서를 만들 수 있습니다.
4. 개발 환경: Visual Studio와 같은 IDE를 사용하여 C# 코드를 작성하고 실행합니다.
5. 샘플 Excel 파일: 이미 디지털 서명이 된 기존 Excel 파일이 있는데, 이 파일을 사용해서 새 서명을 추가합니다.

이러한 전제 조건을 갖추었으니, 이제 코드로 들어가 보겠습니다!

## 필요한 패키지 가져오기

C# 파일의 맨 위에 다음 네임스페이스를 포함하여 필요한 클래스와 메서드에 액세스하세요.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## 1단계: 디렉토리 정의

소스 파일의 디렉토리와 출력 파일을 저장할 위치를 지정하세요.

```csharp
// 소스 디렉토리
string sourceDir = "Your Document Directory"; // 실제 디렉토리로 바꾸세요
// 출력 디렉토리
string outputDir = "Your Document Directory"; // 실제 디렉토리로 바꾸세요
```

## 2단계: 기존 서명된 통합 문서 로드

이미 서명된 Excel 통합 문서를 로드합니다.

```csharp
// 이미 디지털 서명된 통합 문서를 로드합니다.
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## 3단계: 디지털 서명 컬렉션 만들기

디지털 서명을 관리하기 위한 컬렉션을 만드세요.

```csharp
//디지털 서명 컬렉션 만들기
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## 4단계: 인증서 로드

새로운 서명을 만드는 데 사용될 디지털 인증서를 로드합니다.

```csharp
// 인증서 파일 및 비밀번호
string certFileName = sourceDir + "AsposeDemo.pfx"; // 귀하의 인증서 파일
string password = "aspose"; // 귀하의 인증서 비밀번호

// 새로운 인증서 생성
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## 5단계: 새 디지털 서명 만들기

이제 새로운 디지털 서명을 만들어 컬렉션에 추가하세요.

```csharp
// 새로운 디지털 서명을 만들어 컬렉션에 추가하세요
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## 6단계: 통합 문서에 서명 컬렉션 추가

통합 문서에 디지털 서명 컬렉션을 추가합니다.

```csharp
// 통합 문서에 디지털 서명 컬렉션 추가
workbook.AddDigitalSignature(dsCollection);
```

## 7단계: 통합 문서 저장

새로운 디지털 서명이 포함된 통합 문서를 저장합니다.

```csharp
// 통합 문서 저장
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## 8단계: 성공 확인

성공적인 실행에 대한 피드백을 제공합니다.

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## 결론

축하합니다! Aspose.Cells for .NET을 사용하여 이미 서명된 Excel 파일에 새 디지털 서명을 성공적으로 추가했습니다. 이 프로세스는 문서의 보안을 강화하고 문서의 진위성과 무결성을 보장합니다.

## 자주 묻는 질문

### 디지털 서명이란 무엇인가요?

디지털 서명은 디지털 메시지나 문서의 진위성과 무결성을 검증하여 이들이 변경되지 않았음을 보장하고 서명자의 신원을 확인하는 수학적 체계입니다.

### 디지털 서명을 만들려면 특별한 인증서가 필요합니까?

네, 유효한 디지털 서명을 만들려면 신뢰할 수 있는 인증 기관(CA)에서 발급한 디지털 인증서가 필요합니다.

### 테스트에 자체 서명된 인증서를 사용할 수 있나요?

물론입니다! 개발 및 테스트 목적으로는 자체 서명 인증서를 사용할 수 있지만 프로덕션의 경우 신뢰할 수 있는 CA의 인증서를 사용하는 것이 좋습니다.

### 서명되지 않은 문서에 서명을 추가하려고 하면 어떻게 되나요?

아직 서명되지 않은 문서에 디지털 서명을 추가하려고 하면 문제없이 작동하지만 원래 서명은 존재하지 않습니다.

### Aspose.Cells에 대한 자세한 정보는 어디에서 볼 수 있나요?

 자세한 가이드 및 API 참조는 다음을 확인하세요.[Aspose.Cells 설명서](https://reference.aspose.com/cells/net/).