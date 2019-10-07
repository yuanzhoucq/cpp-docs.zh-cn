---
title: propget (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 044562ba870d6e36ddfcec0c7e84253b111a9eea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514208"
---
# <a name="propget"></a>propget

指定属性访问器函数。

## <a name="syntax"></a>语法

```cpp
[propget]
```

## <a name="remarks"></a>备注

**Propget** C++特性具有与[propget](/windows/win32/Midl/propget) MIDL 特性相同的功能。

## <a name="example"></a>示例

有关**propget**的示例用法, 请参阅可[绑定](bindable.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|方法|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|`propput`， `propputref`|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)