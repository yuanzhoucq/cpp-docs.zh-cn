---
title: "编译器警告 （等级 4） C4706 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4706
dev_langs: C++
helpviewer_keywords: C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 824028fb7fd6d563a7f49017eb6b35d1443490bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4706"></a>编译器警告（等级 4）C4706
条件表达式中的分配  
  
 条件表达式中的测试的值已作为赋值的结果。  
  
 分配都有一个值 （分配左侧的值），可以在另一个表达式，包括测试表达式中合法使用。  
  
 下面的示例生成 C4706:  
  
```  
// C4706a.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a  = b ) // C4706  
   {  
   }  
}  
```  
  
 即使两个测试条件两边的括号，则也会出现警告：  
  
```  
// C4706b.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a  =  b ) ) // C4706  
   {  
   }  
}  
```  
  
 如果您的意图是测试某一关系并不进行赋值，请使用`==`运算符。 例如，以下行测试是否和 b 是否相等：  
  
```  
// C4706c.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a == b )  
   {  
   }  
}  
```  
  
 如果你想要将测试值赋值的结果，测试，以确保该赋值非零且不为 null。 例如，下面的代码将不会生成此警告：  
  
```  
// C4706d.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a = b ) != 0 )  
   {  
   }  
}  
```