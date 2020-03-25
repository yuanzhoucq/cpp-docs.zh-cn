---
title: 数学错误 M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: e8abedf6a326a826d0c8ac513b15037c8bf89bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173686"
---
# <a name="math-error-m6111"></a>数学错误 M6111

堆栈下溢

浮点运算导致8087/287/387 协处理器或模拟器上出现堆栈下溢。

此错误通常是由于调用不返回值的 `long double` 函数导致的。 例如，以下编译和运行时，将生成此错误：

```
long double ld() {};
main ()
{
  ld();
}
```

程序终止，退出代码为139。
