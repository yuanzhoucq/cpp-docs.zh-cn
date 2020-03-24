---
title: 隐藏（C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 6b420e8f50bd217de460a81f5faaf9583c701376
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168091"
---
# <a name="hidden"></a>hidden

指示该项存在，但不应在面向用户的浏览器中显示。

## <a name="syntax"></a>语法

```cpp
[hidden]
```

## <a name="remarks"></a>备注

**Hidden** C++特性具有与[隐藏](/windows/win32/Midl/hidden)MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用**hidden**的示例，请参阅可[绑定](bindable.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**接口**、**类**、**结构**、方法、属性|
|**可重复**|否|
|**必需的特性**|**coclass** （应用于**类**或**结构**时）|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)
