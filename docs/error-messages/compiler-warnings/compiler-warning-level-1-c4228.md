---
title: 编译器警告（等级 1）C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: c216143f2b47148f73502c847175201ea9a74fee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175891"
---
# <a name="compiler-warning-level-1-c4228"></a>编译器警告（等级 1）C4228

使用了非标准扩展：忽略声明符列表中逗号后面的限定符

声明变量时，使用以逗号（如**const**或 `volatile`）作为 Microsoft 扩展（[/ze](../../build/reference/za-ze-disable-language-extensions.md)）的限定符。

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
