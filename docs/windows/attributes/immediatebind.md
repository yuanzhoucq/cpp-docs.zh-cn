---
title: immediatebind （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: 35e8ea4a761fd3cf36da335dc8519ba71772b4e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647715"
---
# <a name="immediatebind"></a>immediatebind

指示数据库将立即收到通知的所有更改将数据绑定对象的属性。

## <a name="syntax"></a>语法

```cpp
[immediatebind]
```

## <a name="remarks"></a>备注

**Immediatebind** c + + 属性具有相同的功能[immediatebind](/windows/desktop/Midl/immediatebind) MIDL 特性。

## <a name="example"></a>示例

请参阅[可绑定](bindable.md)有关如何使用的示例**immediatebind**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|接口方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)