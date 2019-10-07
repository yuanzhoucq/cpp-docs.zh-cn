---
title: defaultbind (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultbind
helpviewer_keywords:
- defaultbind attribute
ms.assetid: b20a8437-24e6-4b6d-a2df-09fe5e1006e0
ms.openlocfilehash: a2f612c4869a62a84a6a2af99057ced365f875f2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490995"
---
# <a name="defaultbind"></a>defaultbind

指示最能表示对象的单个可绑定属性。

## <a name="syntax"></a>语法

```cpp
[defaultbind]
```

## <a name="remarks"></a>备注

**Defaultbind** C++特性具有与[defaultbind](/windows/win32/Midl/defaultbind) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用**defaultbind**的示例, 请参阅可[绑定](bindable.md)的示例。

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
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)