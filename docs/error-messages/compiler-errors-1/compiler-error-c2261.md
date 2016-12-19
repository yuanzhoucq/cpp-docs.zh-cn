---
title: "编译器错误 C2261 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2261"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2261"
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2261
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“string”: 程序集引用无效并且无法解析  
  
 值无效。  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 用于指定友元程序集。  例如，如果 a.dll 要指定 b.dll 作为友元程序集，您将指定（在 a.dll 中）：InternalsVisibleTo\("b"\)。  然后，运行时就允许 b.dll 访问 a.dll 中的所有内容（私有类型除外）。  
  
 有关在指定友元程序集时的正确语法的更多信息，请参见 [友元程序集 \(C\+\+\)](../../dotnet/friend-assemblies-cpp.md)。  
  
## 示例  
 下面的示例生成 C2261。  
  
```  
// C2261.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("a,a,a")];   // C2261  
[assembly: InternalsVisibleTo("a.a")];   // OK  
[assembly: InternalsVisibleTo("a")];   // OK  
```