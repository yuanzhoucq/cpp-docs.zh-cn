---
title: defaultvtable (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 813fb9dd4edf2f6e522e7310ba1e8bfcd55ed2b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62147946"
---
# <a name="defaultvtable"></a>defaultvtable

为 COM 对象的默认 vtable 接口定义的接口。

## <a name="syntax"></a>语法

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>参数

*interface*<br/>
你想要具有默认 vtable 的 COM 对象的指定的接口。

## <a name="remarks"></a>备注

**Defaultvtable** C++属性具有相同的功能[defaultvtable](/windows/desktop/Midl/defaultvtable) MIDL 特性。

## <a name="example"></a>示例

下面的代码演示属性使用的类上**defaultvtable**指定默认接口：

```cpp
// cpp_attr_ref_defaultvtable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI1 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMyI2 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000003")]
__interface IMyI3 {
   HRESULT x();
};

[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),
uuid("00000000-0000-0000-0000-000000000004")]
class CMyC3 : public IMyI3 {};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|否|
|**必需的特性**|**coclass**|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)