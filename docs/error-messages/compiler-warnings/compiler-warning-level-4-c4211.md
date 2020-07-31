---
title: 编译器警告（等级 4）C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: df19f90e17d6737a2639eb1245da197881e35c96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218099"
---
# <a name="compiler-warning-level-4-c4211"></a>编译器警告（等级 4）C4211

使用了非标准扩展：将 extern 重定义为 static

使用默认的 Microsoft 扩展（/Ze），可以将标识符重定义 **`extern`** 为 **`static`** 。

## <a name="example"></a>示例

```c
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

此类重新定义在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下无效。
