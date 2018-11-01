---
title: 编译器警告（等级 4）C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: f1e85591d8ec989d806eb43a6be99bdb1dc62fb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659324"
---
# <a name="compiler-warning-level-4-c4211"></a>编译器警告（等级 4）C4211

使用了非标准扩展： 重新定义为静态 extern

使用默认的 Microsoft 扩展 (/Ze) 中，您可以重新定义`extern`标识符作为**静态**。

## <a name="example"></a>示例

```
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

此类重新定义是在 ANSI 兼容性无效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="see-also"></a>请参阅

