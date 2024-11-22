---
title: 원시 3D 모델링 생성
linktitle: 원시 3D 모델링 생성
second_title: Aspose.3D .NET API
description: 상자와 원통을 포함한 기본 3D 모델을 만들고 사용자 정의하는 방법을 알아보고 이를 FBX 형식으로 손쉽게 저장하세요.
type: docs
weight: 10
url: /ko/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## 소개

Aspose.3D for .NET을 사용한 몰입형 3D 모델링 세계에 오신 것을 환영합니다! 이 포괄적인 튜토리얼에서는 기본 3D 모델을 단계별로 만드는 과정을 안내합니다. 숙련된 개발자이든 배우고 싶어 하는 초보자이든 이 가이드는 프로젝트에 시각적으로 멋진 3D 요소를 만들 수 있는 힘을 줄 것입니다.

## 필수 조건

3D 모델링을 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

-  .NET용 Aspose.3D: Aspose.3D for .NET 라이브러리를 다운로드하여 설치하세요.[다운로드 페이지](https://releases.aspose.com/3d/net/).
  
- .NET 개발 환경: Visual Studio 등 Aspose.3D와 호환되는 환경을 설정합니다.

모든 준비가 끝났으니, 3D 모델링 모험을 시작해볼까요!

## 필요한 네임스페이스 가져오기

Aspose.3D 기능에 액세스하는 데 필요한 네임스페이스를 가져오는 것으로 시작합니다.

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

이러한 네임스페이스는 3D 모델을 조작하고 제작물을 저장하는 데 필요한 도구를 제공합니다.

## 1단계: Scene 객체 초기화

3D 모델의 캔버스 역할을 하는 새로운 장면 객체를 만듭니다.

```csharp
// Scene 객체 초기화
Scene scene = new Scene();
```

이 장면에는 여러분이 만들려고 하는 원시적인 모양이 담겨 있습니다.

## 2단계: 상자 모델 만들기

다음으로, 장면에 상자 모델을 추가해 보겠습니다.

```csharp
// 박스 모델 생성
scene.RootNode.CreateChildNode("box", new Box());
```

귀하의 창의적인 비전에 맞춰 상자의 크기와 속성을 사용자 정의할 수 있습니다.

## 3단계: 실린더 모델 생성

이제 실린더를 추가하여 장면을 향상시키세요.

```csharp
// 실린더 모델 생성
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

상자와 마찬가지로, 원하는 모습을 얻을 수 있도록 실린더의 매개변수를 자유롭게 조정하세요.

## 4단계: FBX 형식으로 장면 저장

3D 모델을 보존하려면 FBX 형식으로 저장하세요.

```csharp
// FBX 포맷으로 도면 저장
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

모델에 적합한 출력 디렉토리와 파일 이름을 선택해야 합니다.

## 5단계: 성공 메시지 표시

마지막으로, 다음과 같은 메시지를 표시하여 성공을 축하하세요.

```csharp
// 성공 메시지 표시
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

원시 모델로 구성된 3D 장면이 이제 완성되어 저장되었습니다!

## 결론

 Aspose.3D for .NET을 사용하여 놀라운 3D 모델을 만든 것을 축하합니다! 이 튜토리얼에서는 기본 모델링의 기본 사항을 다루었지만 가능성은 무한합니다. 고급 기능 및 기술에 대해 자세히 알아보려면[선적 서류 비치](https://reference.aspose.com/3d/net/).

## 자주 묻는 질문

### .NET 이외의 프로그래밍 언어에서도 Aspose.3D for .NET을 사용할 수 있나요?

Aspose.3D는 주로 .NET을 지원하지만, Java 및 기타 플랫폼용 버전도 있습니다.

### 무료 체험이 가능한가요?

 예, Aspose.3D의 기능을 사용해 볼 수 있습니다.[무료 체험](https://releases.aspose.com/).

### .NET용 Aspose.3D에 대한 지원은 어디에서 찾을 수 있나요?

 커뮤니티 지원을 받으려면 다음을 방문하세요.[Aspose.3D 포럼](https://forum.aspose.com/c/3d/18).

### 임시 면허는 어떻게 얻을 수 있나요?

 임시 면허를 요청할 수 있습니다.[여기](https://purchase.conholdate.com/temporary-license/).

### 추가 튜토리얼이 있나요?

 네! 더 많은 튜토리얼과 예제를 탐색하세요.[선적 서류 비치](https://reference.aspose.com/3d/net/).