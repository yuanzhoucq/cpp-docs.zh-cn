---
title: "编译器警告（等级 1）C4441 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4441"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4441"
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器警告（等级 1）C4441
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已忽略“cc1”的调用约定；改用了“cc2”  
  
 托管用户定义类型和全局函数泛型中的成员函数必须使用 [\_\_clrcall](../../cpp/clrcall.md) 调用约定。编译器使用了 `__clrcall`。  
  
## 示例  
 下面的示例生成 C4441。  
  
```  
// C4441.cpp  
// compile with: /clr /W1 /c  
generic <class ItemType>  
void __cdecl Test(ItemType item) {}   // C4441  
// try the following line instead  
// void Test(ItemType item) {}  
  
ref struct MyStruct {  
   void __cdecl Test(){}   // C4441  
   void Test2(){}   // OK  
};  
```