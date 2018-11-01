---
title: 编译器警告（等级 1）C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: c737a48883b97970af70014e2bda4bdc508ab471
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468674"
---
# <a name="compiler-warning-level-1-c4228"></a>编译器警告（等级 1）C4228

使用了非标准扩展： 忽略声明符列表中逗号后面的限定符

喜欢使用的限定符**const**或`volatile`逗号声明变量时是 Microsoft 扩展后 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>示例

```
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```