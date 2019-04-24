---
title: 本机和 .NET 的互操作性
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++]
- .NET Framework [C++], interoperability with Visual C++
- interoperability [C++], about .NET interoperability
- interop [C++], about .NET interoperability
- managed code [C++], interoperability
- native code [C++]
- interoperability [C++]
- MFC [C++], .NET integration
- unmanaged code interoperability [C++]
- Visual C++, interoperability
- native code [C++], .NET interoperatibility
ms.assetid: f3ec6c99-c745-4256-b95b-f1d12ba17a5a
ms.openlocfilehash: 486796e404ad1aee39fbeb85251d26cc078b1160
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237141"
---
# <a name="native-and-net-interoperability"></a>本机和 .NET 的互操作性

VisualC++支持互操作性功能，允许托管和非托管构造共存和交互操作在同一程序集中，即使在同一文件中。 此功能，如 P/Invoke，一小部分支持的其他.NET 语言，但视觉对象提供的互操作性支持大多数C++在其他语言中不可用。

## <a name="in-this-section"></a>本节内容

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
介绍与生成的程序集[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)编译器选项的同时包含托管和非托管功能。

[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
讨论如何使用 MFC 应用程序内承载 Windows 窗体控件的 MFC Windows 窗体支持类。

[从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)<br/>
介绍如何通过.NET 应用程序使用非 CLR Dll。
