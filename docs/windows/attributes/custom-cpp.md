---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 7a1d9bd64a28fa7c08477c6011dc0e8236b7bcf6
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521247"
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

### <a name="parameters"></a>parameters

*uuid*<br/>
唯一 ID。

value<br/>
可以放入变量中的值。

## <a name="remarks"></a>备注

**自定义**c + + 特性会导致将信息放入类型库中。 你将需要一个从类型库读取自定义值的工具。

**自定义**特性具有与[自定义](/windows/win32/Midl/custom)MIDL 特性相同的功能。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

- **适用**于：非 COM `interface` 、 `idl_module` 方法、接口成员、接口参数、、、、 **`typedef`** **`class`** **`enum`** **`union`** 和 **`struct`** 类型。
- 可**重复**：是。
- **必需的属性**：**组件类**（用于类时）。
- **无效的属性**： None。

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立属性](stand-alone-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[参数属性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[接口特性](interface-attributes.md)
