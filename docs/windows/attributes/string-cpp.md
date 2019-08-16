---
title: string (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 978f1f546c0df8de4ff167ddf5ddf724feb31b6e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514015"
---
# <a name="string-c"></a>string (C++)

指示必须将一维**char**、 **wchar_t**、 `byte` (或等效) 数组或指向此类数组的指针视为字符串。

## <a name="syntax"></a>语法

```cpp
[string]
```

## <a name="remarks"></a>备注

**String** C++特性具有与[字符串](/windows/win32/Midl/string)MIDL 特性相同的功能。

## <a name="example"></a>示例

下面的代码演示如何在接口和 typedef 上使用**字符串**:

```cpp
// cpp_attr_ref_string.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, string] typedef char a[21];
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1)] HRESULT Method3([in, string] char *pC);
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|数组、接口参数、接口方法的数组或指针|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[数组特性](array-attributes.md)<br/>
[export](export.md)