---
title: nonextensible （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: 2a1cd4d685e2fd141c6e11feaea488f44a884c80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214647"
---
# <a name="nonextensible"></a>nonextensible

指定 `IDispatch` 实现仅包含接口说明中列出的属性和方法，而不能在运行时与其他成员一起扩展。

## <a name="syntax"></a>语法

```cpp
[nonextensible]
```

## <a name="remarks"></a>备注

**Nonextensible** C++特性具有与[nonextensible](/windows/win32/Midl/nonextensible) MIDL 特性相同的功能。

使用**nonextensible**还需要[oleautomation](oleautomation.md)属性。

## <a name="example"></a>示例

下面的代码演示**nonextensible**属性的一种用法：

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**接口**|
|**可重复**|否|
|**必需的特性**|`dual` 和 `oleautomation`或 `dispinterface`|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)
