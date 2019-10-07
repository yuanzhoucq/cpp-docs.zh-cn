---
title: range (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.range
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
ms.openlocfilehash: d1221192eb1813d759f293fe5555d7aaa5b367ab
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514142"
---
# <a name="range-c"></a>range (C++)

为其值在运行时设置的参数或字段指定一系列允许的值。

## <a name="syntax"></a>语法

```cpp
[ range(low, high) ]
```

### <a name="parameters"></a>参数

*low*<br/>
低范围值。

*high*<br/>
高范围值。

## <a name="remarks"></a>备注

**Range** C++特性具有与[范围](/windows/win32/Midl/range)MIDL 特性相同的功能。

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
|**适用于**|接口方法, 接口参数|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[参数特性](parameter-attributes.md)<br/>
[数据成员特性](data-member-attributes.md)