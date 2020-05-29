---
title: 编译器警告（等级 1）C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: 7dba86d591f18fd7c9c562078204916000d47384
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175319"
---
# <a name="compiler-warning-level-1-c4715"></a>编译器警告（等级 1）C4715

"function"：并非所有的控件路径都返回值

指定的函数可能不会返回值。

## <a name="example"></a>示例

```cpp
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

若要防止出现此警告，请修改代码，使所有路径都向函数分配一个返回值：

```cpp
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

你的代码可能包含对从不返回的函数的调用，如以下示例中所示：

```cpp
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

此代码还会生成一个警告，因为编译器不知道 `fatal` 绝不会返回。 若要阻止此代码生成错误消息，请使用[__declspec （noreturn）](../../cpp/noreturn.md)声明 `fatal`。
