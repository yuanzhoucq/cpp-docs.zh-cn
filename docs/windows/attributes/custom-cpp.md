---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 227e67696e679452a9c6c0e18c04e3d918f7a93f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148168"
---
# <a name="custom-c"></a>custom (C++)

类型库中定义的对象的元数据。

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
一个值，可以将放入一个变体。

## <a name="remarks"></a>备注

**自定义**C++属性将可能会放入类型库的信息。 你将需要一种工具，从类型库中读取自定义值。

**自定义**属性具有相同的功能[自定义](/windows/desktop/Midl/custom)MIDL 特性。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|非 COM**接口**，**类**，**枚举**s，`idl_module`方法、 接口成员、 接口参数**typedef**s，**union**s，**结构**s|
|**可重复**|是|
|**必需的特性**|**组件类**（当使用类）|
|**无效的特性**|None|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[接口特性](interface-attributes.md)