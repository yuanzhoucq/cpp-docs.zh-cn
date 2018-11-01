---
title: 编译器警告 （等级 2） C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: 73805afc897d14c6d2cc87490dfa0769a8de5193
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488395"
---
# <a name="compiler-warning-level-2-c4094"></a>编译器警告 （等级 2） C4094

未标记 token 未声明符号

编译器检测到使用标记的结构、 联合或类的空声明。 声明将被忽略。

## <a name="example"></a>示例

```
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

这种情况会生成在 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。