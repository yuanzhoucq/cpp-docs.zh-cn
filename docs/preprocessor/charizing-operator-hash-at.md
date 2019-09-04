---
title: 字符化运算符 (#@)
ms.date: 08/29/2019
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: cb2a4e07287edf5ed2d0850ec7d870c8ef307879
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218542"
---
# <a name="charizing-operator-"></a>字符化运算符 (#@)

**Microsoft 专用**

charizing 运算符只能与宏的自变量一起使用。 如果`#@`在宏的定义中的形参前面加上实参, 则在展开宏时, 实参将括在单引号中并被视为一个字符。 例如：

```cpp
#define makechar(x)  #@x
```

导致以下语句

```cpp
a = makechar(b);
```

扩展为

```cpp
a = 'b';
```

单引号字符 (`'`) 不能与 charizing 运算符一起使用。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[预处理器运算符](../preprocessor/preprocessor-operators.md)
