---
title: helpstringcontext (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: a6df5b63291fbc54d6c12a116fccd8372e8ced9a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026105"
---
# <a name="helpstringcontext"></a>helpstringcontext

在.hlp 或.chm 文件中指定的帮助主题的 ID。

## <a name="syntax"></a>语法

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>参数

*contextID*<br/>
中的 32 位的帮助上下文标识符**帮助**文件。

## <a name="remarks"></a>备注

**Helpstringcontext** C++属性具有相同的功能[helpstringcontext](/windows/desktop/Midl/helpstringcontext) ODL 特性。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**接口**，接口方法|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[module](module-cpp.md)