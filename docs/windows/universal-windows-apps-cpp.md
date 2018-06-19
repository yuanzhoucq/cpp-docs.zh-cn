---
title: 通用 Windows 应用 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9914e9ac83efcc43ef120259254b65ef4f1e0ee9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891118"
---
# <a name="universal-windows-apps-c"></a>通用 Windows 应用 (C++)

通用 Windows 平台 (UWP) 应用体现了一套设计原则，强调采用简单的用户界面，以内容为中心，在不同的设备上针对不同的屏幕大小自动进行调整。 可以采用 XAML 标记语言创建 UI，并使用本地 C++ 创建代码隐藏。 此外，还可创建可供以其他语言编写的 UWP 应用使用的组件 (DLL)。 UWP 应用的 API 图面是 Windows 运行时，这是一个分解好的库，提供各种操作系统服务。

> [!TIP]  
> 在 Windows 10 中，可以使用桌面应用转换器将现有的桌面应用程序打包，以便部署到 Windows 应用商店。 有关详细信息，请参阅 [Using Visual C++ Runtime in Centennial project](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) （在 Centennial 项目中使用 VC 运行时）和 [Bring your desktop app to the Universal Windows Platform (UWP) with the Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root)（使用桌面桥将桌面应用引入通用 Windows 平台 (UWP)）。

## <a name="uwp-apps-that-use-cwinrt"></a>UWP 应用使用 C + + /cli WinRT

C + + /cli WinRT 是新的标头专用库基于 c + + 语言投影的 Windows 运行时使用完全标准 c + +，与不同的是 C + + /cli CX 实现。 C + + /cli WinRT 不使用非标准语法或 Microsoft 语言扩展，并且它充分利用 c + + 编译器创建高度优化的输出。 有关详细信息，请参阅[C + + /cli WinRT](/windows/uwp/cpp-and-winrt-apis)。 有关介绍 C + + /cli WinRT 和代码快速入门，请参阅[简介 C + + /cli WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)。

## <a name="uwp-apps-that-use-ccx"></a>UWP 应用使用 C + + /cli CX

|||
|-|-|
|[Visual C++ 语言参考 (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)|介绍的一套扩展，可简化的 Windows 运行时 Api 的 c + + 消耗并启用了基于异常的错误处理。|
|[生成应用程序和库 (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|描述如何创建可从 C++/CX 应用或组件进行访问的 Dll 和静态库。|
|[教程： 创建 UWP"Hello，World"应用程序在 C + + /cli CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|一个演练，介绍的基本概念的 UWP 应用开发，在 C + + /cli CX。 |
|[创建 Windows 运行时组件在 C + + /cli CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|描述如何创建其他 UWP 应用和组件可以使用的 Dll。|
|[UWP 游戏编程](/windows/uwp/gaming/)|介绍如何使用 DirectX 和 C + + /cli CX 来创建游戏。|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>UWP 应用使用 Windows 运行时 c + + 模板库 (WRL)

Windows 运行时 C++ 模板库提供低级别的 COM 接口，让 ISO C++ 代码可以在无异常的环境中访问 Windows 运行时。 在大多数情况下，建议使用 C++/CX 而不是Windows 运行时 C++ 模板库来开发通用 Windows 平台应用程序。 有关 Windows 运行时 C++ 模板库的信息，请参阅 [Windows 运行时 C++ 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。

## <a name="see-also"></a>请参阅

[Visual C++](../visual-cpp-in-visual-studio.md)<br/>
