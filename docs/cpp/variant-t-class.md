---
title: _variant_t 类
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: 69976cab9caed653a8278f80821569b613f690eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165940"
---
# <a name="variantt-class"></a>_variant_t 类

**Microsoft 专用**

一个 **_variant_t**对象将封装`VARIANT`数据类型。 类管理资源分配和解除分配，并使对函数调用`VariantInit`和`VariantClear`根据需要。

### <a name="construction"></a>构造

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|构造 **_variant_t**对象。|

### <a name="operations"></a>操作

|||
|-|-|
|[附加](../cpp/variant-t-attach.md)|将附加`VARIANT`对象插入 **_variant_t**对象。|
|[清除](../cpp/variant-t-clear.md)|清除封装`VARIANT`对象。|
|[ChangeType](../cpp/variant-t-changetype.md)|更改的类型 **_variant_t**所指示的对象`VARTYPE`。|
|[分离](../cpp/variant-t-detach.md)|分离封装`VARIANT`从此对象 **_variant_t**对象。|
|[SetString](../cpp/variant-t-setstring.md)|将字符串分配给此 **_variant_t**对象。|

### <a name="operators"></a>运算符

|||
|-|-|
|[Operator =](../cpp/variant-t-operator-equal.md)|将新值分配到现有 **_variant_t**对象。|
|[operator ==, !=](../cpp/variant-t-relational-operators.md)|比较两个 **_variant_t**对象是否相等。|
|[提取器](../cpp/variant-t-extractors.md)|从封装中提取数据`VARIANT`对象。|

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头：** \<comutil.h >

**Lib:** comsuppw.lib 或 comsuppwd.lib (请参阅[/zc: wchar_t （wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)有关详细信息)

## <a name="see-also"></a>请参阅

[编译器 COM 支持类](../cpp/compiler-com-support-classes.md)