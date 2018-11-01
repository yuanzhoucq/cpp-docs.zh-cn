---
title: 字符串 （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 8bf708067341ecde4fb18d565b7d72866312decd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603185"
---
# <a name="string-c"></a>string (C++)

指示的一维**char**， **wchar_t**， `byte` （或等效） 必须作为字符串处理数组或指针，指向此类。

## <a name="syntax"></a>语法

```cpp
[string]
```

## <a name="remarks"></a>备注

**字符串**c + + 属性具有相同的功能[字符串](/windows/desktop/Midl/string)MIDL 特性。

## <a name="example"></a>示例

下面的代码演示如何使用**字符串**接口上和 typedef:

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
|**适用对象**|数组或指针，指向 array，接口参数，接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[数组特性](array-attributes.md)<br/>
[export](export.md)