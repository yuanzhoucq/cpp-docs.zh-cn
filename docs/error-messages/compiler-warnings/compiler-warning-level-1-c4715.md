---
title: 编译器警告 （等级 1） C4715 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4715
dev_langs:
- C++
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3de829992bfa650280768a2fcd761feaeaece0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061365"
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