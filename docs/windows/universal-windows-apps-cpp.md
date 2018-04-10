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
通用 Windows 平台 (UWP) 应用体现了一套设计原则，强调采用简单的用户界面，以内容为中心，在不同的设备上针对不同的屏幕大小自动进行调整。可以采用 XAML 标记语言创建 UI，并使用本地 C++ 创建代码隐藏。此外，还可创建可供以其他语言编写的 UWP 应用使用的组件 (DLL)。UWP 应用的 API 图面是 Windows 运行时，这是一个分解好的库，提供各种操作系统服务。

> [!TIP]  
> 在 Windows 10 中，可以使用桌面应用转换器将现有的桌面应用程序打包，以便部署到 Windows 应用商店。有关详细信息，请参阅 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) （在 Centennial 项目中使用 VC 运行时）和 [Bring your desktop app to the Universal Windows Platform (UWP) with the Desktop Bridge](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root)（使用桌面桥将桌面应用引入通用 Windows 平台 (UWP)）。
  
  
## <a name="uwp-apps-that-use-ccx"></a>使用 C++/CX 的 UWP 应用  
  
|||  
|-|-|  
|[Visual C++ 语言参考 (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|描述了一套扩展，该扩展可简化 C++ 对 Windows 运行时 API 的使用并允许根据异常进行错误处理。|
|[生成应用程序和库 (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|描述如何创建可从 C++/CX 应用或组件进行访问的 Dll 和静态库。|  
|[教程：使用 C++ 创建第一个 Windows 应用商店应用](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|一个演练，介绍在 C++ 中进行的通用 Windows 平台应用开发的基本概念。（尚未针对 Windows 10 上的 UWP 开发进行更新。）|  
|[C + + 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何创建其他的通用 Windows 平台应用程序和组件可以使用的 Dll。|  
|[开发游戏](https://docs.microsoft.com/en-us/windows/uwp/gaming/)|介绍如何使用 DirectX 和 C++ 来创建游戏。|  
  
## <a name="universal-windows-platform-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>使用 Windows 运行时 c + + 模板库 (WRL) 的通用 Windows 平台应用 
Windows 运行时 C++ 模板库提供低级别的 COM 接口，让 ISO C++ 代码可以在无异常的环境中访问 Windows 运行时。在大多数情况下，建议使用 C++/CX 而不是Windows 运行时 C++ 模板库来开发通用 Windows 平台应用程序。有关 Windows 运行时 C++ 模板库的信息，请参阅 [Windows 运行时 C++ 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。 
  
## <a name="see-also"></a>请参阅  
 [Visual C++](../visual-cpp-in-visual-studio.md)

