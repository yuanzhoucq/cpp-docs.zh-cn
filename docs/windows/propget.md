---
title: propget |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 17c5742fccdc32396b36d058188f3609caf08791
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586741"
---
# <a name="propget"></a>propget

指定的属性访问器函数。

## <a name="syntax"></a>语法

```cpp
[propget]
```

## <a name="remarks"></a>备注

**Propget** c + + 属性具有相同的功能[propget](http://msdn.microsoft.com/library/windows/desktop/aa367145) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](../windows/bindable.md)的示例使用**propget**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|`propput`, `propputref`|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[方法特性](../windows/method-attributes.md)  
[propput](../windows/propput.md)  
[propputref](../windows/propputref.md)  