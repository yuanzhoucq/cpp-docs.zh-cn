---
title: "通用 Windows 应用 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a293f833de7bc575209089362bcaf146d074684b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="universal-windows-apps-c"></a>通用 Windows 应用 (C++)
通用 Windows 平台 (UWP) 应用体现了一套设计原则，强调以针对不同设备上不同屏幕大小自动调整的内容为中心的简单用户界面。 可在 XAML 标记中创建 UI，并使用本机 C++ 创建代码隐藏。 此外，还可创建可供以其他语言编写的 UWP 应用使用的组件 (DLL)。 UWP 应用的 API 图面是 Windows 运行时，这是一个分解库，它提供各种操作系统服务。  

> [!TIP]  
> 对于 Windows 10 中，你可以使用桌面应用转换器你现有桌面应用程序打包以部署通过 Microsoft 应用商店。 有关详细信息，请参阅 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project)（在 Centennial 项目中使用 Visual C++ 运行时）和 [Bring your desktop app to the Universal Windows Platform (UWP) with the Desktop Bridge](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root)（使用桌面桥将桌面应用引入通用 Windows 平台 (UWP)）。
  
  
## <a name="uwp-apps-that-use-ccx"></a>使用 C++/CX 的 UWP 应用  
  
|||  
|-|-|  
|[Visual C++ 语言参考 (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|介绍的一套扩展，可简化的 Windows 运行时 Api 的 c + + 消耗并启用了基于异常的错误处理。|  
|[生成应用程序和库 (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|描述如何创建可从 C++/CX 应用或组件进行访问的 Dll 和静态库。|  
|[教程： 创建第一个 UWP 应用使用 c + +](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|一个演练，介绍 c + + 中开发 UWP 应用的基本概念。 （尚未针对 Windows 10 上的 UWP 开发进行更新。）|  
|[C + + 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何创建其他 UWP 应用和组件可以使用的 Dll。|  
|[开发游戏](https://docs.microsoft.com/en-us/windows/uwp/gaming/)|介绍如何使用 DirectX 和 C++ 来创建游戏。|  
  
## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>UWP 应用使用 Windows 运行时 c + + 模板库 (WRL) 
 Windows 运行时 c + + 模板库提供低级别的 COM 接口，ISO c + + 代码可以访问 Windows 运行时在无异常的环境中。 在大多数情况下，我们建议你使用的 C + + /cli CX 而不是适用于 UWP 应用开发 Windows 运行时 c + + 模板库。 Windows 运行时 c + + 模板库有关的信息，请参阅[Windows 运行时 c + + 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。  
  
## <a name="see-also"></a>请参阅  
 [Visual C++](../visual-cpp-in-visual-studio.md)

