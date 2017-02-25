---
title: "编译器错误 C2842 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2842"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2842"
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 编译器错误 C2842
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“类”：托管或 WinRT 类型不能定义自己的“operator new”或“operator delete”  
  
 可以定义自己的 [operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md) 或 [operator delete](../Topic/operator%20delete%20\(%3Cnew%3E\).md) 来管理本机堆上的内存分配。  但是，引用类不能定义这些运算符，因为它们仅分配在托管堆上。  
  
 有关详细信息，请参阅[用户定义的运算符](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## 示例  
 以下示例生成 C2842。  
  
```  
// C2842.cpp  
// compile with: /clr /c  
ref class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```  
  
## 示例  
 以下示例生成 C2842。  
  
```  
// C2842_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```