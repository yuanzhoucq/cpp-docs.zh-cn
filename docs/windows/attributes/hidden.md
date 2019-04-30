---
title: 隐藏 (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: d1d87ea057b22984a0e0f8f5518899e36f7d0221
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409507"
---
# <a name="hidden"></a>隐藏

指示该项存在，但不是应在面向用户的浏览器中显示。

## <a name="syntax"></a>语法

```cpp
[hidden]
```

## <a name="remarks"></a>备注

**隐藏**C++属性具有相同的功能[隐藏](/windows/desktop/Midl/hidden)MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](bindable.md)有关如何使用的示例**隐藏**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**接口**，**类**，**结构**，方法、 属性|
|**可重复**|否|
|**必需的特性**|**组件类**(当应用于**类**或**结构**)|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[方法特性](method-attributes.md)