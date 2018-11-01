---
title: 字符化运算符 (#@)
ms.date: 11/04/2016
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: 7259487a3289173bc77517c8c616638c370041c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568333"
---
# <a name="charizing-operator-"></a>字符化运算符 (#@)
**Microsoft 专用**

charizing 运算符只能与宏的自变量一起使用。 如果`#@`的形参前有宏的定义，在实际自变量是括在单引号内，扩展宏时视为一个字符。 例如：

```
#define makechar(x)  #@x
```

导致以下语句

```
a = makechar(b);
```

扩展为

```
a = 'b';
```

单引号字符不能与 charizing 运算符一起使用。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[预处理器运算符](../preprocessor/preprocessor-operators.md)