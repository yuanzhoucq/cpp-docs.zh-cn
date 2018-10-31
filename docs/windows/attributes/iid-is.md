---
title: iid_is （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.iid_is
dev_langs:
- C++
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b777be28fcee3c11a8f3ae2058d6197f39d2ba22
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060164"
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
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[参数特性](parameter-attributes.md)