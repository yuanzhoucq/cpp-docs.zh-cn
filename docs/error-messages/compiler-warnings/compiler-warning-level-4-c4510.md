---
title: "编译器警告 （等级 4） C4510 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4510
dev_langs: C++
helpviewer_keywords: C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4bfef2780f338357b600f8fae28559d4c7c00e49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4510"></a>编译器警告（等级 4）C4510
class： 无法生成默认构造函数  
  
 没有用户定义的构造函数的创建和编译器无法生成指定的类的默认构造函数。 你将无法创建此类型的对象。  
  
 防止生成默认构造函数，编译器的几种情况包括：  
  
-   Const 的数据成员。  
  
-   为引用数据成员。  
  
 你需要创建用户定义的默认构造函数初始化这些成员的类。  
  
 下面的示例生成 C4510:  
  
```  
// C4510.cpp  
// compile with: /W4  
struct A {  
   const int i;  
   int &j;  
   A& operator=( const A& ); // C4510 expected  
   // uncomment the following line to resolve this C4510  
   // A(int ii, int &jj) : i(ii), j(jj) {}  
};   // C4510  
  
int main() {  
}  
```