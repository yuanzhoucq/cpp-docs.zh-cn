---
title: 控制的转移 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e773a0188eb3450ab1a13a24fc556fa8e8c4f874
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464264"
---
# <a name="transfers-of-control"></a>控制的转移
可以使用**goto**语句或**用例**中的标签**切换**语句来指定分支超出初始值设定项的程序。 此类代码是非法的，除非包含初始值设定项的声明在跳转语句发生的块所封闭的块中。  
  
 下面的示例显示了声明和初始化对象 `total`、`ch` 和 `i` 的循环。 此外，还有的错误**goto**语句将控制权传递过初始值设定项。  
  
```cpp 
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
  
 在前面的示例中， **goto**语句尝试将控制权传递过的初始化`i`。 但是，如果已声明但未初始化 `i`，则该传递是合法的。  
  
 对象`total`并`ch`用作的块中声明*语句*的**而**语句，使用退出该块时销毁**中断**语句。  