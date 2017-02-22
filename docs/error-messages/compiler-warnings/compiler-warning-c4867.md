---
title: "编译器警告 C4867 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4867"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4867"
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# 编译器警告 C4867
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 函数调用缺少参数列表；使用“call”创建指向成员的指针  
  
 错误地初始化了指向成员函数的指针。  
  
 为 Visual C\+\+ 2005 执行的编译器一致性工作可能导致此警告：增强的指向成员的指针的一致性。现在，在 Visual C\+\+ 2005 前编译的代码将生成 C4867。  
  
 此警告始终按错误发出。  使用 [警告](../../preprocessor/warning.md) 杂注可禁用此警告。  有关 C4867 和 MFC\/ATL 的更多信息，请参见 [\_ATL\_ENABLE\_PTM\_WARNING](../Topic/_ATL_ENABLE_PTM_WARNING.md)。  
  
## 示例  
 下面的示例生成 C4867。  
  
```  
// C4867.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b = {f};   // C4867  
      B b2 = {&A::f};   // OK  
   }  
};  
```