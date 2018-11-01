---
title: pointer_default （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pointer_default
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
ms.openlocfilehash: 8261d789f50c2750cccce48dac675ef478a70420
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504385"
---
# <a name="pointerdefault"></a>pointer_default

指定所有指针，除顶级指针在参数列表中显示的默认指针特性。

## <a name="syntax"></a>语法

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>参数

*value*<br/>
描述指针类型的值： **ptr**， **ref**，或**唯一**。

## <a name="remarks"></a>备注

**Pointer_default** c + + 属性具有相同的功能[pointer_default](/windows/desktop/Midl/pointer-default) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[defaultvalue](defaultvalue.md)的示例使用**pointer_default**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)