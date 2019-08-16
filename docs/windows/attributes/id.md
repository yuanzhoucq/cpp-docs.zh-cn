---
title: id (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 6f1d1d2b9d147e8b33b3b5fae629e0805971bb71
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501411"
---
# <a name="id"></a>id

为成员函数指定*dispid*参数 (属性或方法在接口或调度接口中)。

## <a name="syntax"></a>语法

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>参数

*dispid*<br/>
接口方法的调度 ID。

## <a name="remarks"></a>备注

**Id** C++特性具有与[id](/windows/win32/Midl/id) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用**id**的示例, 请参阅可[绑定](bindable.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|接口方法|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[数据成员特性](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)