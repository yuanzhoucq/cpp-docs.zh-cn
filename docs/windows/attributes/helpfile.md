---
title: 帮助帮助（c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 641823779346bf5417ec0db26b83083fa949e960
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222116"
---
# <a name="helpfile"></a>helpfile

设置类型库的帮助文件的名称。

## <a name="syntax"></a>语法

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>参数

*filename*<br/>
包含帮助主题的文件的名称。

## <a name="remarks"></a>备注

"**帮助**程序" c + + 属性与 "[帮助](/windows/win32/Midl/helpfile)台 MIDL" 特性具有相同的功能。

## <a name="example"></a>示例

有关如何使用**帮助**程序的示例，请参阅[模块](module-cpp.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**interface**、 **`typedef`** ， **`class`** 、method、**`property`**|
|**且**|否|
|**必需属性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)
