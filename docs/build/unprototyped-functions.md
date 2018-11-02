---
title: 非原型函数
ms.date: 11/04/2016
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
ms.openlocfilehash: 38207be6111dadc338593e55b683b88e0480e1ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633419"
---
# <a name="unprototyped-functions"></a>非原型函数

对于完全保持原型的函数，调用方将整数值传递为整数和浮点值作为双精度。 对于浮点值，整数寄存器和浮点寄存器将包含 float 值在被调用方需要采用整数寄存器的值的情况下。

```
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="see-also"></a>请参阅

[调用约定](../build/calling-convention.md)