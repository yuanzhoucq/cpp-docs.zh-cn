---
title: 数学错误 M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 0b1cd0d3fcd86a2174b19da41176dd97f547a295
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193701"
---
# <a name="math-error-m6201"></a>数学错误 M6201

"function"： _DOMAIN 错误

给定函数的参数超出了该函数的合法输入值的域。

## <a name="example"></a>示例

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

此错误将调用具有函数名称、其参数和错误类型的 `_matherr` 函数。 您可以重写 `_matherr` 函数，以自定义对某些运行时浮点算术错误的处理。
