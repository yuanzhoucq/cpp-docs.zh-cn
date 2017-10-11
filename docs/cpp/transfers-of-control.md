---
title: "控制的转移 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a604c95bb21ad0098a3d4563738971791fc94a07
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="transfers-of-control"></a>控制的转移
你可以使用`goto`语句或**用例**标签英寸`switch`语句要指定分支过初始值设定项的程序。 此类代码是非法的，除非包含初始值设定项的声明在跳转语句发生的块所封闭的块中。  
  
 下面的示例显示了声明和初始化对象 `total`、`ch` 和 `i` 的循环。 也存在将控制权传递过初始值设定项的错误 `goto` 语句。  
  
```  
// transfers_of_control.cpp  
// compile with: /W1  
// Read input until a nonnumeric character is entered.  
int main()  
{  
   char MyArray[5] = {'2','2','a','c'};  
   int i = 0;  
   while( 1 )  
   {  
      int total = 0;  
  
      char ch = MyArray[i++];  
  
      if ( ch >= '0' && ch <= '9' )  
      {  
         goto Label1;  
  
         int i = ch - '0';  
      Label1:  
         total += i;   // C4700: transfers past initialization of i.  
      } // i would be destroyed here if  goto error were not present  
   else  
      // Break statement transfers control out of loop,  
      //  destroying total and ch.  
      break;  
   }  
}  
```  
  
 在前面的示例中，`goto` 语句尝试将控制权传递过 `i` 的初始化。 但是，如果已声明但未初始化 `i`，则该传递是合法的。  
  
 对象`total`和`ch`、 用作块中声明*语句*的`while`语句，在使用退出该块时销毁`break`语句。  
  

