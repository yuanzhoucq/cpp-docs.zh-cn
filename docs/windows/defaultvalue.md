---
title: defaultvalue |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultvalue
dev_langs:
- C++
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a27120869c464a9009f8d19cf0f84bfde7a02e96
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446046"
---
# <a name="defaultvalue"></a>defaultvalue

允许类型化可选参数的默认值的规范。

## <a name="syntax"></a>语法

```cpp
[ defaultvalue= value ]
```

### <a name="parameters"></a>参数

*value*<br/>
参数的默认值。

## <a name="remarks"></a>备注

**Defaultvalue** c + + 属性具有相同的功能[defaultvalue](/windows/desktop/Midl/defaultvalue) MIDL 特性。

## <a name="example"></a>示例

下面的代码显示了接口的方法使用**defaultvalue**属性：

```cpp
// cpp_attr_ref_defaultvalue.cpp
// compile with: /LD
#include <windows.h>

[export] typedef long HRESULT;
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;

[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"),
   dual, oleautomation,
   helpstring("IFireTabCtrl Interface"),
   helpcontext(122), pointer_default(unique) ]

__interface IFireTabCtrl : IDispatch {
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);
   [bindable, propput] HRESULT put_Size([in] int nSize);
};

[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",
      version="1.0", helpstring="ATLFire 1.0 Type Library") ];
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口参数|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[参数特性](../windows/parameter-attributes.md)<br/>
[out](../windows/out-cpp.md)<br/>
[retval](../windows/retval.md)<br/>
[in](../windows/in-cpp.md)<br/>
[pointer_default](../windows/pointer-default.md)<br/>
[unique](../windows/unique-cpp.md)  