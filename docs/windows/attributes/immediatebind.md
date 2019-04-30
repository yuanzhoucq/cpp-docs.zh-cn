---
title: immediatebind (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: 1844e72ecd1fe7c0f4255426eb48f5c70471e5f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409468"
---
# <a name="immediatebind"></a>immediatebind

指示数据库将立即收到通知的所有更改将数据绑定对象的属性。

## <a name="syntax"></a>语法

```cpp
[immediatebind]
```

## <a name="remarks"></a>备注

**Immediatebind** C++属性具有相同的功能[immediatebind](/windows/desktop/Midl/immediatebind) MIDL 特性。

## <a name="example"></a>示例

请参阅[可绑定](bindable.md)有关如何使用的示例**immediatebind**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口方法|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)