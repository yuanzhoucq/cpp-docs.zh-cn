---
title: 编译器警告 （等级 3） C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: e898af8f109ed23bd1784df7b39c174bbed675f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402276"
---
# <a name="compiler-warning-level-3-c4159"></a>编译器警告 （等级 3） C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>杂注 pragma(pop,...)： 将先前入栈的标识符*标识符*

## <a name="remarks"></a>备注

你的源代码包含**推送**标识符的杂注指令后, 跟**pop**指令不含标识符。 因此，*标识符*是弹出，并且后续的用法*标识符*可能导致意外的行为。

## <a name="example"></a>示例

若要避免此警告，在中提供的标识符**pop**指令。 例如：

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```