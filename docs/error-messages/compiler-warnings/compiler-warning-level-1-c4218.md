---
title: 编译器警告（等级 1）C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 226bc91c272ff62ebe127aa190384d30a214b05d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223247"
---
# <a name="compiler-warning-level-1-c4218"></a>编译器警告（等级 1）C4218

使用了非标准扩展：必须至少指定一个存储类或一个类型

使用默认的 Microsoft 扩展（/Ze），可以在不指定类型或存储类的情况下声明变量。 默认类型为 **`int`** 。

## <a name="example"></a>示例

```cpp
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

此类声明在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下无效。
