---
title: 在 c + + （DllImport 特性） 中使用显式 PInvoke |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bbaaee5845124dda45b4fe11ff44033e8c6a9f17
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444263"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>在 C++ 中使用显式 PInvoke（DllImport 特性）

.NET Framework 提供了显式的平台调用 （简称 PInvoke） 功能与`Dllimport`属性以允许托管应用程序调用 Dll 中打包的非托管的函数。 其中的非托管的 Api 打包为 Dll，并且源代码不可用的情况下需要显式 PInvoke。 例如，调用 Win32 函数要求 PInvoke。 否则，请使用隐式 P {Invoke，请参见[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)有关详细信息。

PInvoke 的工作原理是使用<xref:System.Runtime.InteropServices.DllImportAttribute>。 此属性，将 DLL 作为其第一个参数的名称，将使用每个 DLL 入口点的函数声明之前放置。 函数的签名必须与 DLL 导出函数的名称匹配 (但是，可以通过定义隐式执行某些类型转换`DllImport`根据托管类型的声明。)

结果是一个托管的入口点，每个包含的必要转换代码 （或转换 （thunk）） 的本机 DLL 函数和简单的数据转换。 通过这些入口点 DLL 然后可以调用托管的函数。 作为 PInvoke 的结果插入到模块的代码完全托管。

## <a name="in-this-section"></a>本节内容

- [从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)

- [如何：使用 PInvoke 从托管代码调用本机 DLL](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)

- [如何：使用 PInvoke 封送处理字符串](../dotnet/how-to-marshal-strings-using-pinvoke.md)

- [如何：使用 PInvoke 封送结构](../dotnet/how-to-marshal-structures-using-pinvoke.md)

- [如何：使用 PInvoke 封送数组](../dotnet/how-to-marshal-arrays-using-pinvoke.md)

- [如何：使用 PInvoke 封送函数指针](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)

- [如何：使用 PInvoke 封送嵌入式指针](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)

## <a name="see-also"></a>请参阅

[从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)