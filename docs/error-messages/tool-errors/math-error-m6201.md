---
title: 数学错误 M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 6d3f107de7e45653374036ecafaa864cb3eff5b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393241"
---
# <a name="math-error-m6201"></a>数学错误 M6201

function: （_d） 错误

给定函数的参数是合法的输入值，该函数的域之外。

## <a name="example"></a>示例

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

此错误调用`_matherr`函数名称、 其参数与错误类型的函数。 您可以重写`_matherr`函数以自定义某些运行时浮点数学错误处理。