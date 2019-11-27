---
title: 编译器警告（等级 4）C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: 6387f58430098e49e7add25e8915bf6b181634e9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541833"
---
# <a name="compiler-warning-level-4-c4211"></a>编译器警告（等级 4）C4211

使用了非标准扩展：将 extern 重定义为 static

使用默认的 Microsoft 扩展（/Ze），可以将 `extern` 标识符重新定义为**静态**。

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
