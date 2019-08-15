---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 19f28963a18abf42c6f629ac0f6491628387aa6d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491001"
---
# <a name="custom-c"></a>custom (C++)

为类型库中的对象定义元数据。

## <a name="syntax"></a>语法

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>参数

*uuid*<br/>
唯一 ID。

*值*<br/>
可以放入变量中的值。

## <a name="remarks"></a>备注

**自定义** C++特性将导致信息放置到类型库中。 你将需要一个从类型库读取自定义值的工具。

**自定义**特性具有与[自定义](/windows/win32/Midl/custom)MIDL 特性相同的功能。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|非 COM**接口**,**类**,**枚举** `idl_module` s, 方法, 接口成员, 接口参数, **typedef**s,**联合**,**结构**s|
|**可重复**|是|
|**必需的特性**|**coclass**(当用于类时)|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[接口特性](interface-attributes.md)