---
title: helpcontext （c + + COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 77c085f96e778b19886c4e6e3c8f07b43fbe8f2c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211978"
---
# <a name="helpcontext"></a>helpcontext

指定一个上下文 ID，该 ID 允许用户在**帮助**文件中查看有关此元素的信息。

## <a name="syntax"></a>语法

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>参数

*id*<br/>
帮助主题的上下文 ID。 有关上下文 Id 的详细信息，请参阅[HTML 帮助：程序的上下文相关帮助](../../mfc/html-help-context-sensitive-help-for-your-programs.md)。

## <a name="remarks"></a>备注

**Helpcontext** c + + 特性具有与[helpcontext](/windows/win32/Midl/helpcontext) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用**helpcontext**的示例，请参阅[defaultvalue](defaultvalue.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|**interface**、 **`typedef`** ， **`class`** 、method、property|
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
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
