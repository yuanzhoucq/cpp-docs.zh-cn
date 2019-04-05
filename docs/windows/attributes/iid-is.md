---
title: iid_is （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: b91fb7937bb0e20f2500eace9695bc0ddba21b26
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038552"
---
# <a name="iidis"></a>iid_is

指定的接口指针指向了 COM 接口的 IID。

## <a name="syntax"></a>语法

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>参数

*表达式*<br/>
指定 COM 接口的 IID 是 C 语言表达式指向一个接口指针。

## <a name="remarks"></a>备注

**Iid_is** c + + 属性具有相同的功能[iid_is](/windows/desktop/Midl/iid-is) MIDL 特性。

## <a name="example"></a>示例

下面的代码演示如何使用**iid_is**:

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口参数，数据成员|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Parameter 特性](parameter-attributes.md)