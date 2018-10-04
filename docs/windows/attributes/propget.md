---
title: propget （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propget
dev_langs:
- C++
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44a5b06a4d94bc431d33fa29cdcef4738e43ca54
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790491"
---
# <a name="propget"></a>propget

指定的属性访问器函数。

## <a name="syntax"></a>语法

```cpp
[propget]
```

## <a name="remarks"></a>备注

**Propget** c + + 属性具有相同的功能[propget](/windows/desktop/Midl/propget) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](bindable.md)的示例使用**propget**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|`propput`, `propputref`|

有关特性上下文的详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[方法特性](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)  