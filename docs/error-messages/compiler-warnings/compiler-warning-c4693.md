---
title: "编译器警告 C4693 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4693"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4693"
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告 C4693
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：密封的抽象类不能具有任何实例成员“Test”  
  
 如果一个类型被标记为 [sealed](../../windows/sealed-cpp-component-extensions.md) 和 [abstract](../../windows/abstract-cpp-component-extensions.md)，则它只能具有静态成员。  
  
## 示例  
 下面的示例生成 C4693。  
  
```  
// C4693.cpp // compile with: /clr /c public ref class Public_Ref_Class sealed abstract { public: void Test() {}   // C4693 static void Test2() {}   // OK };  
```