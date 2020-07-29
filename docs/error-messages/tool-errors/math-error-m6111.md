---
title: 数学错误 M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 986c0e53edcddfc47eb9ba970f3c32385e0a57d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225184"
---
# <a name="math-error-m6111"></a>数学错误 M6111

堆栈下溢

浮点运算导致8087/287/387 协处理器或模拟器上出现堆栈下溢。

此错误通常是由对不返回值的函数的调用导致的 **`long double`** 。 例如，以下编译和运行时，将生成此错误：

```
long double ld() {};
main ()
{
  ld();
}
```

程序终止，退出代码为139。
