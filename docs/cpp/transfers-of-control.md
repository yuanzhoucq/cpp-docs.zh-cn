---
title: 控制的转移
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: ef437d0a691ceff72485be1ff9584052f540031a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232178"
---
# <a name="transfers-of-control"></a>控制的转移

您可以 **`goto`** **`case`** 在语句中使用语句或标签 **`switch`** 来指定分支过时的程序。 此类代码是非法的，除非包含初始值设定项的声明在跳转语句发生的块所封闭的块中。

下面的示例显示了声明和初始化对象 `total`、`ch` 和 `i` 的循环。 还有一个错误 **`goto`** 的语句，它将控制转移到初始值设定项之后。

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

在前面的示例中， **`goto`** 语句尝试将控制转移到的初始化之后 `i` 。 但是，如果已声明但未初始化 `i`，则该传递是合法的。

`total` `ch` *statement* **`while`** 当使用语句退出该块时，将销毁在块中声明的对象和（用作语句的语句） **`break`** 。
