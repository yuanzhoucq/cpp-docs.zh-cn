---
title: 编译器警告（等级1） C4581
ms.date: 11/04/2016
f1_keywords:
- C4581
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
ms.openlocfilehash: 5931516e3f4eba91c3b7a3ab4d0ca4979ce1ed84
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965928"
---
# <a name="compiler-warning-level-1-c4581"></a>编译器警告（等级1） C4581

弃用的行为： "string1" "已替换为" string2 "以处理特性

此错误可能是由于为 Visual Studio 2005 执行了编译器一致性工作而生成的：针对视觉对象C++属性的参数检查。

在以前的版本中，无论属性值是否括在引号中，均可接受。 如果值为枚举，则不得用引号将其引起来。

## <a name="example"></a>示例

下面的示例生成 C4581。

```cpp
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