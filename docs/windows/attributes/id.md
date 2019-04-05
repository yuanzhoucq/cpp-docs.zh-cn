---
title: id （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 5faf08418771deda3086a434cff6b1900a37e36e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034691"
---
# <a name="id"></a>id

指定*dispid* （属性或方法，请在接口或调度接口） 的成员函数的参数。

## <a name="syntax"></a>语法

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>参数

*dispid*<br/>
接口方法的调度 ID。

## <a name="remarks"></a>备注

**Id** c + + 属性具有相同的功能[id](/windows/desktop/Midl/id) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](bindable.md)有关如何使用的示例**id**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口方法|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[数据成员特性](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[中的](in-cpp.md)<br/>
[out](out-cpp.md)