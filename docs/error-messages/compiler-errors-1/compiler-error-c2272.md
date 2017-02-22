---
title: "编译器错误 C2272 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2272"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2272"
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2272
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 静态成员函数上不允许使用修饰符  
  
 用内存模型说明符（如 [const](../../cpp/const-cpp.md) 或 [volatile](../../cpp/volatile-cpp.md)）声明了 `static` 成员函数，而在 `static` 成员函数上不允许这样的修饰符。  
  
 下面的示例生成 C2272：  
  
```  
// C2272.cpp  
// compile with: /c  
class CMyClass {  
public:  
   static void func1() const volatile;   // C2272  func1 is static  
   void func2() const volatile;   // OK  
};  
```