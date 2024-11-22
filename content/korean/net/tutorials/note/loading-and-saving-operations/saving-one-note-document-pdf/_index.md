---
title: Aspose.Note for .NET을 사용하여 OneNote 문서를 PDF로 저장
linktitle: OneNote 문서를 PDF로 저장
second_title: Aspose.Note .NET API
description: Aspose.Note for .NET을 사용하여 Microsoft OneNote 문서를 PDF 파일로 효율적으로 저장하는 방법을 알아보세요. 이 가이드는 필요한 전제 조건을 안내하고 유용한 FAQ를 제공합니다.
type: docs
weight: 26
url: /ko/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## 소개

이 튜토리얼에서는 Aspose.Note for .NET을 사용하여 문서를 PDF 형식으로 저장하는 방법을 살펴보겠습니다. Aspose.Note는 개발자가 Microsoft OneNote 파일을 프로그래밍 방식으로 사용할 수 있도록 하는 강력한 라이브러리입니다. 필수 구성 요소를 다루고, 네임스페이스를 가져오고, 다양한 페이지 레이아웃으로 문서를 PDF로 저장하기 위한 단계별 가이드를 제공합니다.

## 필수 조건
1. Visual Studio: 설치되어 있는지 확인하세요.
2. .NET용 Aspose.Note: 라이브러리를 다운로드하여 설치하세요.
3. C# 지식: 언어에 대한 기본적인 이해가 필요합니다.

## 필요한 네임스페이스 가져오기
계속하기 전에 코드에서 다음 네임스페이스를 가져오세요.

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## 1단계: Letter 페이지 설정으로 PDF로 저장
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // 이 경로를 업데이트하세요
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
OneNote 문서를 로드하고 Letter 크기 페이지 설정을 사용하여 PDF로 저장합니다.

## 2단계: A4 페이지 설정으로 PDF로 저장(높이 제한 없음)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // 이 경로를 업데이트하세요
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
1단계와 비슷하지만 높이 제한 없이 A4 페이지 설정을 사용합니다.

## 결론
이 튜토리얼은 Aspose.Note를 사용하여 OneNote 파일을 PDF 형식으로 변환하는 방법을 성공적으로 보여줍니다. 다양한 페이지 설정을 활용함으로써 개발자는 문서 관리에 유연성을 얻습니다.

## 자주 묻는 질문
### Aspose.Note는 복잡한 OneNote 파일을 처리할 수 있나요?
네, 복잡한 OneNote 파일의 다양한 기능을 효과적으로 처리합니다.

### Aspose.Note는 상업 프로젝트에 적합합니까?
네, 라이선스를 구매한 후 상업용으로 사용할 수 있습니다.

### Aspose.Note는 무료 체험판을 제공합니까?
네, 무료 체험판을 이용해 보세요.

### Aspose.Note에 대한 문서는 어디에서 찾을 수 있나요?
자세한 문서는 Aspose 참조 사이트에서 확인할 수 있습니다.

### 추가 지원이 필요하신가요?
질문과 지원이 필요하면 Aspose.Note 포럼을 참조하세요.
