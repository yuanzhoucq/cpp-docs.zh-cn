---
title: uidefault (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uidefault
helpviewer_keywords:
- uidefault attribute
ms.assetid: 200de0e0-2e34-40a2-bae4-8d485a62264d
ms.openlocfilehash: b4090011aade4ebab2f5c07a8e56e91253cc7c49
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513899"
---
# <a name="uidefault"></a>uidefault

指示类型信息成员是在用户界面中显示的默认成员。

## <a name="syntax"></a>语法

```cpp
[uidefault]
```

## <a name="remarks"></a>备注

**Uidefault** C++特性具有与[uidefault](/windows/win32/Midl/uidefault) MIDL 特性相同的功能。

## <a name="example"></a>示例

下面的代码演示**uidefault**的示例:

```cpp
// cpp_attr_ref_uidefault.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom{
   HRESULT Custom([in] long l, [out, retval] long *pLong);
   [uidefault]HRESULT id0([in] long l);
   [uidefault]HRESULT id1([in] long l);

   [uidefault, propget] HRESULT get_y(int *y);
   [uidefault, propput] HRESULT put_y(int y);
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|接口方法|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)