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
ms.openlocfilehash: e11d31904fd8e54049f69ee4f6530d511c8c7f4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187747"
---
# <a name="_variant_t-class"></a>_variant_t 类

**Microsoft 专用**

**_Variant_t**对象封装 `VARIANT` 数据类型。 类管理资源分配和释放，并根据需要对 `VariantInit` 和 `VariantClear` 执行函数调用。

### <a name="construction"></a>建筑

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|构造一个 **_variant_t**对象。|

### <a name="operations"></a>操作

|||
|-|-|
|[附加](../cpp/variant-t-attach.md)|将 `VARIANT` 对象附加到 **_variant_t**对象中。|
|[Clear](../cpp/variant-t-clear.md)|清除封装的 `VARIANT` 对象。|
|[ChangeType](../cpp/variant-t-changetype.md)|将 **_variant_t**对象的类型更改为指示的 `VARTYPE`。|
|[分离](../cpp/variant-t-detach.md)|从此 **_variant_t**对象分离封装的 `VARIANT` 对象。|
|[SetString](../cpp/variant-t-setstring.md)|为此 **_variant_t**对象分配一个字符串。|

### <a name="operators"></a>运算符

|||
|-|-|
|[Operator =](../cpp/variant-t-operator-equal.md)|将新值分配给现有的 **_variant_t**对象。|
|[operator = =，！ =](../cpp/variant-t-relational-operators.md)|比较两个 **_variant_t**对象是否相等或不相等。|
|[提取器](../cpp/variant-t-extractors.md)|从封装的 `VARIANT` 对象中提取数据。|

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头：** \<comutil.h >

**Lib：** comsuppw.lib 或 comsuppwd.lib （有关详细信息，请参阅[/zc： Wchar_t （Wchar_t 为本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>另请参阅

[编译器 COM 支持类](../cpp/compiler-com-support-classes.md)
