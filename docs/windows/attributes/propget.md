---
title: propget (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 8f60e8e8fc98ba3b75acefe80812069bfac78e6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407622"
---
# <a name="propget"></a>propget

指定的属性访问器函数。

## <a name="syntax"></a>语法

```cpp
[propget]
```

## <a name="remarks"></a>备注

**Propget** C++属性具有相同的功能[propget](/windows/desktop/Midl/propget) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](bindable.md)的示例使用**propget**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|方法|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|`propput`， `propputref`|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)