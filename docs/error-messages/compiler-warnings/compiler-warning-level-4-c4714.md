---
title: "编译器警告 （等级 4） C4714 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4714
dev_langs: C++
helpviewer_keywords: C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d49ff1bbf6538965d277b0afdd6c96fd9c71ef0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4714"></a>编译器警告（等级 4）C4714
函数 function 标记为 __forceinline 不内联  
  
 为内联展开选定了给定的函数，但编译器没有执行内联。  
  
 尽管`__forceinline`是比编译器的更强指示`__inline`、 内联仍会在编译器自行执行但没有试探方法用于确定受益内联此函数。  
  
 在某些情况下，编译器将会机械原因而不内联某个特定的函数。 例如，编译器将不内联：  
  
-   如果这会导致混合使用 SEH 和 c + + EH 函数。  
  
-   某些函数使用复制构造上-GX/EHs/EHa 时通过值传递的对象。  
  
-   -GX/EHs/EHa 上时按值返回的不可展开对象的函数。  
  
-   使用内联程序集没有-Og/Ox/O1/O2 编译时的函数。  
  
-   使用变量自变量列表的函数。  
  
-   具有函数**重**（c + + 异常处理） 语句。  
  
 下面的示例生成 C4714:  
  
```  
// C4714.cpp  
// compile with: /Ob1 /GX /W4  
__forceinline void func1()  
{  
   try  
   {  
   }  
   catch (...)  
   {  
   }  
}  
  
void func2()  
{  
   func1();   // C4714  
}  
  
int main()  
{  
}  
```