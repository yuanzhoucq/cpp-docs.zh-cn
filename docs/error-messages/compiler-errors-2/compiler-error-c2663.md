---
title: "编译器错误 C2663 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2663"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2663"
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2663
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: number 重载没有“this”指针的合法转换  
  
 编译器未能将 `this` 转换为该成员函数的任何重载版本。  
  
 此错误可能是由对 `const` 对象调用非 `const` 成员函数引起的。可能的解决方案：  
  
1.  从对象声明中移除 `const`。  
  
2.  将 `const` 添加到成员函数重载之一。  
  
 下面的示例生成 C2663：  
  
```  
// C2663.cpp  
struct C {  
   void f() volatile {}  
   void f() {}  
};  
  
struct D {  
   void f() volatile;  
   void f() const {}  
};  
  
const C *pcc;  
const D *pcd;  
  
int main() {  
   pcc->f();    // C2663  
   pcd->f();    // OK  
}  
```