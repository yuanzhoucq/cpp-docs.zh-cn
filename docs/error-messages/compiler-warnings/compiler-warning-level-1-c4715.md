---
title: 编译器警告（等级 1）C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: f165ea3b54b78e2f8fae995815e309d55101244e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501226"
---
# <a name="compiler-warning-level-1-c4715"></a>编译器警告（等级 1）C4715

function： 并非所有控件路径都返回值

指定的函数可能不返回值。

## <a name="example"></a>示例

```
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

若要防止出现此警告，修改代码，使所有路径将返回值都分配给该函数：

```
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

它是包含你的代码可能永远不会返回，如以下示例所示的函数调用：

```
// C4715c.cpp
// compile with: /W1 /LD
void fatal()
{
}
int glue()
{
   if(0)
      return 1;
   else if(0)
      return 0;
   else
      fatal();   // C4715
}
```

此代码还会生成一条警告，因为编译器不知道的`fatal`永远不会返回。 若要防止此代码生成一条错误消息，声明`fatal`使用[__declspec （noreturn)](../../cpp/noreturn.md)。