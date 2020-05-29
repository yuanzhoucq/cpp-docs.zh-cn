---
title: helpstringdll （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 4ec0d959b2fc10fc34bfc7050a1970359dae5bbc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168117"
---
# <a name="helpstringdll"></a>helpstringdll

指定要用于执行文档字符串查找（本地化）的 DLL 的名称。

## <a name="syntax"></a>语法

```cpp
[ helpstringdll("string") ]
```

### <a name="parameters"></a>parameters

*string*<br/>
要用于执行文档字符串查找的 DLL。

## <a name="remarks"></a>备注

**Helpstringdll** C++特性具有与[helpstringdll](/windows/win32/Midl/helpstringdll) MIDL 特性相同的功能。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**、**接口**、接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)
