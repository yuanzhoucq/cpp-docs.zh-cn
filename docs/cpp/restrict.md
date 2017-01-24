---
title: "restrict | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "restrict"
  - "restrict_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], restrict"
  - "restrict __declspec 关键字"
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# restrict
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 应用于函数声明或定义，该声明或定义返回指针类型，并通知编译器该函数将返回不会将任何其他指针作为别名的对象。  
  
## 语法  
  
```  
__declspec(restrict) return_type f();  
```  
  
## 备注  
 编译器将传播 `__declspec(restrict)`。  例如，CRT `malloc` 函数是使用 `__declspec(restrict)` 修饰的，因此，使用 `malloc` 初始化为内存位置的指针也暗示不使用别名。  
  
 编译器不检查指针到底有没有使用别名。  开发人员负责确保程序没有对使用 `restrict __declspec` 修饰符标记的指针使用别名。  
  
 有关变量的类似语义，请参阅 [\_\_restrict](../cpp/extension-restrict.md)。  
  
## 示例  
 有关使用 [noalias](../cpp/noalias.md) 的示例，请参阅 `restrict`。  
  
 有关作为 C\+\+ AMP 的一部分的限制关键字的信息，请参阅[restrict \(C\+\+ AMP\)](../cpp/restrict-cpp-amp.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)