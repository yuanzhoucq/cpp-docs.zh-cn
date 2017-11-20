---
title: "编译器错误 C2524 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2524
dev_langs: C++
helpviewer_keywords: C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f0b80ac9029f530b68afdc379d7660bba1ff76cb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2524"></a>编译器错误 C2524
析构函数： 析构函数/终结器必须具有 void 参数列表  
  
 析构函数或终结器具有不是一个参数列表[void](../../cpp/void-cpp.md)。 不允许其他参数类型。  
  
## <a name="example"></a>示例  
 下面的代码再现 C2524。  
  
```  
// C2524.cpp  
// compile with: /c  
class A {  
   A() {}  
   ~A(int i) {}    // C2524  
   // try the following line instead  
   // ~A() {}  
};  
```  
  
## <a name="example"></a>示例  
 下面的代码再现 C2524。  
  
```  
// C2524_b.cpp  
// compile with: /clr /c  
ref struct I1 {  
protected:  
   !I1(int i);   // C2524  
   // try the following line instead  
   // !I1();  
};  
```