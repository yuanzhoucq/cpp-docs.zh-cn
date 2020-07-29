---
title: first_is （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.first_is
helpviewer_keywords:
- first_is attribute
ms.assetid: 89acbf56-3b38-4d44-83e8-1ce2f6f74ffd
ms.openlocfilehash: 192d08471241526cace895bd5a5147070316cd6d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228058"
---
# <a name="first_is"></a>first_is

指定要传输的第一个数组元素的索引。

## <a name="syntax"></a>语法

```cpp
[ first_is("expression") ]
```

### <a name="parameters"></a>参数

*expression*<br/>
一个或多个 C 语言表达式。 允许空参数槽。

## <a name="remarks"></a>备注

**First_is** c + + 特性具有与[first_is](/windows/win32/Midl/first-is) MIDL 特性相同的功能。

## <a name="example"></a>示例

下面的代码演示了在数组中指定节的各种方式：

```cpp
// cpp_attr_ref_first_is.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"

[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind,
requestedit] HRESULT get_I([out, retval]long *i);
   HRESULT Proc1([in] short First, [in] short Last,
[first_is(First), last_is(Last), size_is(Last-First)] char Arr1[]);
   HRESULT Proc2([in] short First, [in] short Last,
[last_is(First), size_is(Last)] char Arr2[]);
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|或中的字段 **`struct`** **`union`** ，接口参数，接口方法|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[参数属性](parameter-attributes.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
