---
title: 编译器警告（等级 1）C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 9e370bcff0c30fb508ebc22aaff1f6a56dd420a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625112"
---
# <a name="compiler-warning-level-1-c4581"></a>编译器警告（等级 1）C4581

已否决的行为:"string1"替换为 string2 进程属性

为 Visual c + + 2005年执行的编译器一致性工作可以生成此错误： 正在检查的 Visual c + + 特性的参数。

在上一版本中，属性值已被接受，指示已用引号引起来。 如果值是一个枚举，它必须不括在引号中。

## <a name="example"></a>示例

下面的示例生成 C4581。

```
// C4581.cpp
// compile with: /c /W1
#include "unknwn.h"
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI : IUnknown {};

[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581
// try the following line instead
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]
class CSample : public IMyI {};
```