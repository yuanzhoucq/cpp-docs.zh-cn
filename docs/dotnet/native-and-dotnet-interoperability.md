---
title: 本机和.NET 互操作性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6f62ff29ce104362d3057773e09a3cea1f69eed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420475"
---
# <a name="native-and-net-interoperability"></a>本机和 .NET 的互操作性

Visual c + + 支持互操作性功能，允许托管和非托管构造共存和交互操作在同一程序集中，即使在同一文件中。 此功能，如 P/Invoke，一小部分支持的其他.NET 语言，但大部分提供 Visual c + + 的互操作性支持不可用其他语言中。

## <a name="in-this-section"></a>本节内容

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
介绍与生成的程序集[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)编译器选项的同时包含托管和非托管功能。

[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
讨论如何使用 MFC 应用程序内承载 Windows 窗体控件的 MFC Windows 窗体支持类。

[从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)<br/>
介绍如何通过.NET 应用程序使用非 CLR Dll。

## <a name="see-also"></a>请参阅

