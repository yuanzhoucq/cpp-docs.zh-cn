---
title: 编译器警告（等级 1）C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: e1f28f5afb1879229ff0d408cb576312966e1c81
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200104"
---
# <a name="compiler-warning-level-1-c4138"></a>编译器警告（等级 1）C4138

在注释外找到“*/”

结束注释分隔符前面没有开始注释分隔符。 编译器将假定星号 (<strong>\*</strong>) 和正斜杠 (/) 之间留有一个空格。

## <a name="example"></a>示例

```cpp
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

此警告可由嵌套注释引起。

如果注释掉包含注释的代码段，在 **#if / #endif** 块中包含代码，并将控制表达式设置为零，可能会解决此警告：

```cpp
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```
