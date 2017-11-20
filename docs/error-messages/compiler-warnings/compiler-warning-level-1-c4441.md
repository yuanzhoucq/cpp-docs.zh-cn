---
title: "编译器警告 （等级 1） C4441 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4441
dev_langs: C++
helpviewer_keywords: C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fc83284e7de2c381413dd48f60a82dd68942568f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4441"></a>编译器警告（等级 1）C4441
调用约定 cc1 忽略;cc2 改用  
  
 托管的用户定义类型和全局函数泛型中的成员函数必须使用[__clrcall](../../cpp/clrcall.md)调用约定。  所用编译器`__clrcall`。  
  
## <a name="example"></a>示例  
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