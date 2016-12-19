---
title: "在 C++ 中使用显式 PInvoke（DllImport 特性） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 互操作, 平台调用"
  - "数据封送处理 [C++], 平台调用"
  - "互操作 [C++], 平台调用"
  - "封送处理 [C++], 平台调用"
  - "平台调用 [C++], 在 C++ 中进行封送处理"
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 C++ 中使用显式 PInvoke（DllImport 特性）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

.NET Framework 通过 `Dllimport` 特性提供了显式平台调用（或 PInvoke）功能，允许托管应用程序调用打包在 DLL 中的非托管函数。  在非托管 API 打包为 DLL 并且源代码不可用的情况下，需要使用显式 PInvoke。  例如，调用 Win32 函数就需要 PInvoke。  否则，请使用隐式 P{Invoke；有关更多信息，请参见[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 通过使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 可使用 PInvoke。  此特性将 DLL 的名称作为其第一个参数，放置于要使用的每个 DLL 入口点的函数声明之前。  函数的签名必须与 DLL 导出的函数名称相匹配（对于托管类型，可通过定义 `DllImport` 声明隐式执行某种类型转换）。  
  
 得到的结果是每个本机 DLL 函数的托管入口点，其中包含必需的转换代码（或 thunk）和简单数据转换。  然后托管函数可通过这些入口点调入 DLL。  作为 PInvoke 的结果插入到模块中的代码是完全托管的，并且 **\/clr**、**\/clr:pure** 和 **\/clr:safe** 编译也支持显式 PInvoke。  有关详细信息，请参阅[纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## 本节内容  
  
-   [从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)  
  
-   [如何：使用 PInvoke 从托管代码调用本机 DLL](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送处理字符串](../dotnet/how-to-marshal-strings-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送结构](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送数组](../dotnet/how-to-marshal-arrays-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送函数指针](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)  
  
-   [如何：使用 PInvoke 封送嵌入式指针](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)  
  
## 请参阅  
 [从托管代码调用本机函数](../dotnet/calling-native-functions-from-managed-code.md)