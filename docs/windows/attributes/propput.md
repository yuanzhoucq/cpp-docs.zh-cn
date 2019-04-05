---
title: propput （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: c9853b38675abfa0a94a319ac752eb2ef61a48e0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031727"
---
# <a name="propput"></a>propput

指定属性设置功能。

## <a name="syntax"></a>语法

```cpp
[propput]
```

## <a name="remarks"></a>备注

**Propput** c + + 属性具有相同的功能[propput](/windows/desktop/Midl/propput) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](bindable.md)的示例使用**propput**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|方法|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|`propget`, `propputref`|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)