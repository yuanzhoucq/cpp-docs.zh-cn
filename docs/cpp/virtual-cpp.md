---
title: virtual (C++)
ms.date: 11/04/2016
f1_keywords:
- virtual_cpp
- virtual
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
ms.openlocfilehash: f68bd2e500ebe16c43ef6c3d7a5aede26421b27d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605057"
---
# <a name="virtual-c"></a>virtual (C++)

**虚拟**关键字声明的虚函数或虚拟基类。

## <a name="syntax"></a>语法

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>参数

*类型说明符*<br/>
指定此虚拟成员函数的返回类型。

*成员函数声明符*<br/>
声明一个成员函数。

*访问说明符*<br/>
为基类，定义的访问级别**公共**，**保护**或**专用**。 可以在之前或之后出现**虚拟**关键字。

*基本类名*<br/>
标识一个以前声明的类类型。

## <a name="remarks"></a>备注

请参阅[虚函数](../cpp/virtual-functions.md)有关详细信息。

另请参阅以下关键字：[类](../cpp/class-cpp.md)，[专用](../cpp/private-cpp.md)，[公共](../cpp/public-cpp.md)，以及[受保护的](../cpp/protected-cpp.md)。

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)