---
title: 可绑定 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.bindable
dev_langs:
- C++
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4c529abb1ade786bf7ec0a2d5cff5c49f6197be7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601584"
---
# <a name="bindable"></a>bindable

指示该属性支持数据绑定。

## <a name="syntax"></a>语法

```cpp
[bindable]
```

## <a name="remarks"></a>备注

**可绑定**c + + 属性具有相同的功能[可绑定](http://msdn.microsoft.com/library/windows/desktop/aa366738)MIDL 特性。 可以使用它具有定义的属性上[propget](../windows/propget.md)， [propput](../windows/propput.md)，或[propputref](../windows/propputref.md)属性，或者你可以手动定义一个可绑定的方法。

以下的 MFC 示例显示了如何使用**可绑定**:

- [控件示例： 基于 MFC 的 ActiveX 控件](http://msdn.microsoft.com/a44adf86-0ba0-4504-bedb-512b6cba2e63)

- [CIRC 示例： ActiveX 控件](http://msdn.microsoft.com/9ba34d04-280e-49f4-90ae-41a6be44c95b)

- [使用工具提示和帮助 TESTHELP 示例： ActiveX 控件](http://msdn.microsoft.com/d822861d-c6f0-4d0a-ad11-970eebb1e8cd)

## <a name="example"></a>示例

下面的代码演示如何使用**可绑定**属性上：

```cpp
// cpp_attr_ref_bindable.cpp
// compile with: /LD
#include <windows.h>
[
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"),
   dispinterface,
   helpstring("property demo Interface")  
]
__interface IPropDemo : IDispatch {

   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();
};

[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[方法特性](../windows/method-attributes.md)  
[defaultbind](../windows/defaultbind.md)  
[displaybind](../windows/displaybind.md)  
[immediatebind](../windows/immediatebind.md)  
[requestedit](../windows/requestedit.md)  