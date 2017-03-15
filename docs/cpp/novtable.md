---
title: "novtable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "novtable"
  - "novtable_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], novtable"
  - "novtable __declspec 关键字"
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# novtable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 这是 `__declspec` 扩展特性。  
  
 此形式的 `__declspec` 可应用于任何类声明，但只应该应用于纯接口类，即，永远不会独立实例化的类。  `__declspec` 可阻止编译器生成用来初始化类的构造函数和析构函数中的 vfptr 的代码。  在许多情况下，这将移除对与类关联的 vtable 的唯一引用，因此链接器将移除它。  使用此形式的 `__declspec` 可使代码大小显著显减小。  
  
 如果尝试实例化标记为 `novtable` 的类，然后访问类成员，您将收到访问冲突 \(AV\)。  
  
## 示例  
  
```  
// novtable.cpp  
#include <stdio.h>  
  
struct __declspec(novtable) X {  
   virtual void mf();  
};  
  
struct Y : public X {  
   void mf() {  
      printf_s("In Y\n");  
   }  
};  
  
int main() {  
   // X *pX = new X();  
   // pX->mf();   // Causes a runtime access violation.  
  
   Y *pY = new Y();  
   pY->mf();  
}  
```  
  
  **In Y**   
## 结束 Microsoft 专用  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)