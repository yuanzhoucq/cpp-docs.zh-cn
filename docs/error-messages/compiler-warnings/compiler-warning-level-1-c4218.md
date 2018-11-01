---
title: 编译器警告（等级 1）C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 36d5de3b1270b41edfc391df960a556aca207709
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555293"
---
# <a name="compiler-warning-level-1-c4218"></a>编译器警告（等级 1）C4218

使用了非标准扩展： 必须指定至少一个存储类或类型

使用默认的 Microsoft 扩展 (/Ze) 中，可以声明一个变量，而无需指定类型或存储类。 默认类型为 `int`。

## <a name="example"></a>示例

```
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

此类声明是在 ANSI 兼容性无效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。