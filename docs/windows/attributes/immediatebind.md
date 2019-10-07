---
title: immediatebind (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: 8c659f23d6828616c4a48522b61330336e994cbb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514648"
---
# <a name="immediatebind"></a>immediatebind

指示将立即通知数据库对数据绑定对象的属性所做的所有更改。

## <a name="syntax"></a>语法

```cpp
[immediatebind]
```

## <a name="remarks"></a>备注

**Immediatebind** C++特性具有与[immediatebind](/windows/win32/Midl/immediatebind) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关如何使用**immediatebind**的示例, 请参阅可[绑定](bindable.md)。

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
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)