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
ms.openlocfilehash: a8948594bade940834e041adc73d56cc7847acc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187500"
---
# <a name="virtual-c"></a>virtual (C++)

**Virtual**关键字声明虚拟函数或虚拟基类。

## <a name="syntax"></a>语法

```
virtual [type-specifiers] member-function-declarator
virtual [access-specifier] base-class-name
```

#### <a name="parameters"></a>parameters

*类型说明符*<br/>
指定此虚拟成员函数的返回类型。

*成员函数-声明符*<br/>
声明一个成员函数。

*访问说明符*<br/>
定义对基类（**公共**、**受保护**或**私有**）的访问级别。 可以出现在**虚**关键字之前或之后。

*基类名*<br/>
标识一个以前声明的类类型。

## <a name="remarks"></a>备注

有关详细信息，请参阅[虚拟函数](../cpp/virtual-functions.md)。

另请参阅以下关键字： [class](../cpp/class-cpp.md)、 [private](../cpp/private-cpp.md)、 [public](../cpp/public-cpp.md)和[protected](../cpp/protected-cpp.md)。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)
