---
title: Excel 통합 문서 간 VBA 사용자 양식 및 매크로 전송
linktitle: Excel 통합 문서 간 VBA 사용자 양식 및 매크로 전송
second_title: Aspose.Cells .NET Excel 처리 API
description: Aspose.Cells for .NET을 사용하여 VBA 사용자 양식과 매크로를 워크북 간에 전송하는 방법에 대한 포괄적인 가이드로 Excel 자동화의 힘을 활용하세요. 초보자와 숙련된 개발자 모두에게 적합합니다.
type: docs
weight: 11
url: /ko/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## 소개

VBA 매크로와 사용자 양식을 사용하여 Excel 경험을 향상시키기 위한 최고의 가이드에 오신 것을 환영합니다! 이 튜토리얼에서는 강력한 Aspose.Cells for .NET 라이브러리를 사용하여 VBA 매크로 사용자 양식 디자이너를 한 통합 문서에서 다른 통합 문서로 전송하는 방법을 살펴보겠습니다. 숙련된 개발자이든 초보자이든 이 단계별 가이드는 Excel 파일을 프로그래밍 방식으로 처리하는 데 필요한 지식을 제공합니다. 시작할 준비가 되셨나요? 시작해 봅시다!

## 필수 조건
코딩에 들어가기 전에 먼저 필요한 모든 것이 있는지 확인해 보겠습니다.

1. C# 개발 환경: Visual Studio를 활용한 C# 개발 작업 환경이 적극 권장됩니다.
2.  .NET 라이브러리용 Aspose.Cells: Aspose.Cells 라이브러리를 프로젝트에 통합해야 합니다. 쉽게[여기서 다운로드하세요](https://releases.aspose.com/cells/net/).
3. VBA와 Excel 매크로에 대한 기본 지식: VBA와 Excel 매크로의 기능에 대한 지식이 있으면 이 자습서에 대한 이해도가 높아질 것입니다.
4. 사용자 양식이 포함된 Excel 파일: 사용자 양식이 포함된 Excel 통합 문서를 만들거나 가져옵니다(매크로가 활성화된 것이 좋습니다.`.xlsm` 파일).

## 필수 패키지 가져오기
Aspose.Cells에서 제공하는 기능을 활용하려면 C# 파일 맨 위에 다음 네임스페이스를 포함하세요.

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

이러한 네임스페이스를 사용하면 Aspose.Cells 라이브러리에 내장된 강력한 도구에 액세스할 수 있습니다.

## 1단계: 소스 및 출력 디렉토리 정의
먼저, 파일의 위치를 확인하세요.

```csharp
// 소스 및 출력 디렉토리 정의
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

플레이스홀더 경로를 파일이 저장된 실제 디렉토리로 바꾸세요.

## 2단계: 빈 대상 워크북 만들기
다음으로, 사용자 양식과 매크로를 복사할 새 통합 문서를 만듭니다.

```csharp
// 빈 대상 통합 문서 만들기
Workbook target = new Workbook();
```

이렇게 하면 빈 통합 문서가 초기화되어 향후 데이터 전송을 위한 캔버스 역할을 합니다.

## 3단계: 템플릿 워크북 로드
사용자 양식과 매크로가 포함된 통합 문서를 로드합니다.

```csharp
// VBA-매크로 디자이너 사용자 양식이 포함된 Excel 파일을 로드합니다.
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

조정하다`"sampleDesignerForm.xlsm"` 실제 파일 이름으로 변경하세요.

## 4단계: 대상 워크북에 워크시트 복사
이제 템플릿에서 대상 통합 문서로 워크시트를 복사해 보겠습니다.

```csharp
// 모든 템플릿 워크시트를 대상 통합 문서로 복사합니다.
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // 대상 워크시트의 A2 셀에 메시지를 추가합니다.
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

이 코드는 템플릿의 각 워크시트를 순환하여 대상 통합 문서에 복사하여 모든 데이터가 원활하게 전송되도록 합니다.

## 5단계: 템플릿에서 VBA 매크로 복사
다음으로, UserForm Designer 모듈을 포함한 VBA 매크로를 새 통합 문서에 복사합니다.

```csharp
// 템플릿에서 대상으로 VBA-매크로 디자이너 사용자 양식 복사
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // 이 워크북 모듈 코드 복사
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // 다른 모듈의 코드와 데이터를 복사합니다.
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // 사용자 양식 디자이너 저장소 가져오기
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // 대상 Vba 프로젝트에 디자이너 저장소 추가
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

이 코드를 사용하면 코드뿐만 아니라 사용자 양식 디자인도 복사되어 매크로의 기능이 그대로 유지됩니다.

## 6단계: 대상 워크북 저장
복사 과정을 완료한 후 새 통합 문서를 저장합니다.

```csharp
// 대상 통합 문서 저장
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

필요에 따라 출력 파일 이름을 수정합니다. 이 단계에서는 매크로와 사용자 양식으로 채워진 사용자 지정 워크북을 만듭니다.

## 7단계: 성공 확인
마지막으로 콘솔에 성공 메시지를 출력합니다.

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

이 간단한 문구는 귀하의 작업이 순조롭게 진행되었음을 재확인시켜줍니다. 귀하의 노고에 대한 필수적인 확인이죠!

## 결론
축하합니다! Aspose.Cells for .NET을 사용하여 VBA 매크로 사용자 양식 디자이너를 한 통합 문서에서 다른 통합 문서로 복사하는 방법을 성공적으로 배웠습니다. 처음에는 어려울 수 있지만 연습하면 통합 문서 조작에 능숙해질 것입니다. 코딩은 실험에 관한 것이므로 Excel 파일 내에서 다양한 기능을 탐색하는 것을 주저하지 마십시오. 질문이 있거나 도움이 필요한 경우 Aspose 포럼과 설명서는 지원을 위한 훌륭한 리소스입니다.

## 자주 묻는 질문

### Aspose.Cells는 어떤 버전의 Excel을 지원하나요?
Aspose.Cells는 XLSX, XLSM, CSV 등 다양한 Excel 형식을 지원합니다.

### Aspose.Cells를 무료로 사용할 수 있나요?
 네! 무료 체험판으로 라이브러리를 평가해 보세요:[무료 체험](https://releases.aspose.com/).

### 이 코드를 실행하려면 Visual Studio가 필요합니까?
Visual Studio는 사용자 친화적인 기능으로 인해 권장되지만 .NET 개발을 지원하는 C# IDE라면 무엇이든 괜찮습니다.

### 더 많은 예와 문서는 어디에서 볼 수 있나요?
 탐색할 수 있습니다[Aspose.Cells 문서](https://reference.aspose.com/cells/net/) 더 많은 예와 자세한 설명은 여기에서 확인하세요.

### Aspose.Cells를 사용하는 동안 문제를 해결하려면 어떻게 해야 하나요?
 당신은 방문해야합니다[Aspose 지원 포럼](https://forum.aspose.com/c/cells/9) 커뮤니티와 Aspose 지원 직원에게 도움을 요청하세요.