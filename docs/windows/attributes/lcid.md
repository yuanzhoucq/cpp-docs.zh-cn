---
title: lcid (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.lcid
helpviewer_keywords:
- LCID attribute
ms.assetid: 7f248c69-ee1c-42c3-9411-39cf27c9f43d
ms.openlocfilehash: 7c737661bb8429e416b515e4e7fcaf54956385d0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514534"
---
# <a name="lcid"></a>lcid

使你可以将区域设置标识符传递给函数。

## <a name="syntax"></a>语法

```cpp
[lcid]
```

## <a name="remarks"></a>备注

**Lcid** C++特性实现[lcid](/windows/win32/Midl/lcid) MIDL 特性的功能。 如果要实现库块的区域设置, 请将**lcid =** `lcid`参数用于[module](module-cpp.md)特性。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_lcid.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];
typedef long HRESULT;

[dual, uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA")]
__interface IStatic {
   HRESULT MyFunc([in, lcid] long LocaleID, [out, retval] BSTR * ReturnVal);
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|接口参数|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[参数特性](parameter-attributes.md)