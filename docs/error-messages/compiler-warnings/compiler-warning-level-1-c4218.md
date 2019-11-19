---
title: 编译器警告（等级1） C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: f1db3eabc3b614019676dc4494e83104c62fe579
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627305"
---
# <a name="compiler-warning-level-1-c4218"></a>编译器警告（等级1） C4218

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