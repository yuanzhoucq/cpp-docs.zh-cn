---
title: "在 c + + （DllImport 特性） 中使用显式 PInvoke |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d05c88167629bcb6bf86dc600afde0ea3162064f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>在 C++ 中使用显式 PInvoke（DllImport 特性）
.NET Framework 提供了显式平台调用 （或 PInvoke） 功能与`Dllimport`特性以允许使用托管应用程序调用 Dll 中打包的非托管的函数。 显式 PInvoke 是必需的情况下的非托管的 Api 会打包为 Dll，其中的源代码不可用。 例如，调用 Win32 函数需要 PInvoke。 否则，请使用隐式 P {Invoke，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)有关详细信息。  
  
 PInvoke 工作方式是使用<xref:System.Runtime.InteropServices.DllImportAttribute>。 此属性，将 DLL 作为其第一个参数的名称，位于将使用每个 DLL 入口点的函数声明之前。 函数的签名必须匹配的 DLL 导出的函数的名称 (但可以通过定义隐式执行某种类型转换`DllImport`根据托管类型的声明。)  
  
 结果是一个托管的入口点，每个包含的必要转换代码 （或转换 （thunk）） 的本机 DLL 函数和简单的数据转换。 然后，托管的函数可以调入通过这些入口点 DLL。 将代码插入到模块，完全托管的 PInvoke 结果以及有关支持显式 PInvoke **/clr**， **/clr: pure**，和**/clr: safe**编译。 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。 有关详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## <a name="in-this-section"></a>本节内容  
  
-   [从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)  
  
-   [如何：使用 PInvoke 从托管代码调用本机 DLL](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送处理字符串](../dotnet/how-to-marshal-strings-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送结构](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送数组](../dotnet/how-to-marshal-arrays-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送函数指针](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送嵌入式指针](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)  
  
## <a name="see-also"></a>请参阅  
 [从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)