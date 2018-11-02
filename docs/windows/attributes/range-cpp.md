---
title: 范围 （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: b75915b901f55ce7ef8d295531ab5148c6535c93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644955"
---
# <a name="range-c"></a>range (C++)

指定参数或在运行时设置其值的字段的允许值的范围。

## <a name="syntax"></a>语法

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>参数

*low*<br/>
范围下限值。

*high*<br/>
高范围值。

## <a name="remarks"></a>备注

**范围**c + + 属性具有相同的功能[范围](/windows/desktop/Midl/range)MIDL 特性。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_range.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口方法，接口参数|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[数据成员特性](data-member-attributes.md)