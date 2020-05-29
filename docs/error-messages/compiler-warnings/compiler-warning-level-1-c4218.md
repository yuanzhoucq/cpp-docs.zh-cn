---
title: 编译器警告（等级 1）C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: f7553b30a17f50f559351353552fd656fceb8657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199792"
---
# <a name="compiler-warning-level-1-c4218"></a>编译器警告（等级 1）C4218

使用了非标准扩展：必须至少指定一个存储类或一个类型

使用默认的 Microsoft 扩展（/Ze），可以在不指定类型或存储类的情况下声明变量。 默认类型为 `int`。

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
