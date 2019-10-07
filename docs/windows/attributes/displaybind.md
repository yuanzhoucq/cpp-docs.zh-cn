---
title: displaybind (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.displaybind
helpviewer_keywords:
- displaybind attribute
ms.assetid: b3d70396-78e4-43d9-9583-16ddb8c9bb1f
ms.openlocfilehash: 168db224e7b15656308259f9507e1079744f1a73
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490888"
---
# <a name="displaybind"></a>displaybind

指示应作为可绑定属性显示给用户的属性。

## <a name="syntax"></a>语法

```cpp
[displaybind]
```

## <a name="remarks"></a>备注

**Displaybind** C++特性具有与[displaybind](/windows/win32/Midl/displaybind) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用**displaybind**的示例, 请参阅可[绑定](bindable.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|接口方法|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[数据成员特性](data-member-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)