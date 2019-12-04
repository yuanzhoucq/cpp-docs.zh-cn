---
title: 编译器错误 C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 3766eaa83457ba6cffaf8b1599983a065772911c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750138"
---
# <a name="compiler-error-c3530"></a>编译器错误 C3530

"auto" 不能与任何其他类型说明符组合

类型说明符与 `auto` 关键字一起使用。

### <a name="to-correct-this-error"></a>更正此错误

1. 不要在使用 `auto` 关键字的变量声明中使用类型说明符。

## <a name="example"></a>示例

下面的示例将生成 C3530，因为 `auto` 关键字和类型都声明了变量 `x` `int`，并且该示例是用 **/zc： auto**编译的。

```cpp
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>另请参阅

[auto 关键字](../../cpp/auto-keyword.md)
