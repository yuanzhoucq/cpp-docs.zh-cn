---
title: "编译器错误 C2698 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2698
dev_langs: C++
helpviewer_keywords: C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b2bc9be3cfa38b4789feb35ae57015b78ad079c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2698"></a>编译器错误 C2698
using 声明为声明 1 不能共存与现有 using 声明为声明 2  
  
 一旦[using 声明](../../cpp/using-declaration.md)任何使用的数据成员不允许使用相同的名称与同一范围中的声明，因为只有函数可以进行重载。  
  
 下面的示例生成 C2698:  
  
```  
// C2698.cpp  
struct A {  
   int x;  
};  
  
struct B {  
   int x;  
};  
  
struct C : A, B {  
   using A::x;  
   using B::x;   // C2698  
}  
```