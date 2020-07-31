---
title: 编译器警告（等级 1）C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: 3a89d5c0924e6fd12a4ccf8afa957f8908670d49
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223234"
---
# <a name="compiler-warning-level-1-c4228"></a>编译器警告（等级 1）C4228

使用了非标准扩展：忽略声明符列表中逗号后面的限定符

声明变量时使用 **`const`** 逗号（如或后的限定符 **`volatile`** ）是 Microsoft 扩展（[/ze](../../build/reference/za-ze-disable-language-extensions.md)）。

## <a name="example"></a>示例

```cpp
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```
