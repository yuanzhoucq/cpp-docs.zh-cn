---
title: "通用 Windows 应用 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55a6f21a8b4589b5288b8aff462dbb0234a10300
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2018
---
# <a name="universal-windows-apps-c"></a>通用 Windows 应用 (C++)
通用 Windows 平台 (UWP) 应用体现了一套设计原则，强调以针对各种设备上诸多屏幕大小而自动调整内容为中心的简单用户界面。可在 XAML 标记中创建用户界面，并使用本地 C++ 创建代码后置。 此外，还可创建可供以其他语言编写的 UWP 应用使用的组件 (DLL)。 UWP 应用的 API 表面是 Windows 运行时，这是一个良好分解的库，它提供各种操作系统服务。  

> [!TIP]  
> 在 Windows 10 中，你可以使用桌面应用转换器打包你现有桌面应用程序以部署到 Windows 应用商店。 有关详细信息，请参阅 [在Centennial项目中使用VC运行时 project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) 和 [使用桌面桥将桌面应用移植到通用Windows 平台 (UWP)](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root)。
  
  
## <a name="uwp-apps-that-use-ccx"></a>使用 C++/CX 的 UWP 应用  
  
|||  
|-|-|  
|[Visual C++ 语言参考 (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|描述一套简化Windows 运行时 Api 在 c++ 中的使用并启用了基于异常的错误处理的一套扩展。|
|[生成应用程序和库 (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|描述如何创建可从 C++/CX 应用或组件进行访问的 Dll 和静态库。|  
|[教程：使用 C++ 创建第一个 Windows 应用商店应用](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|一个演练，介绍在 c + + 中的通用 Windows 平台应用开发的基本概念。 |  
|[C + + 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何创建其他的通用 Windows 平台应用程序和组件可以使用的 Dll。|  
|[开发游戏](https://docs.microsoft.com/en-us/windows/uwp/gaming/)|介绍如何使用 DirectX 和 C++ 来创建游戏。|  
  
## <a name="universal-windows-platform-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 运行时 c + + 模板库 (WRL) 的通用 Windows 平台应用 
 Windows 运行时 c + + 模板库提供低级别的 COM 接口让ISO c + + 代码可以在无异常的环境中访问 Windows 运行时。 在大多数情况下，我们建议你使用的 C + + /CX 而不是Windows 运行时 c + + 模板库来开发通用 Windows 平台应用程序。 关于Windows 运行时 c + + 模板库有关的信息，请参阅[Windows 运行时 c + + 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。  
  
## <a name="see-also"></a>请参阅  
 [Visual C++](../visual-cpp-in-visual-studio.md)

