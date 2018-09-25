---
title: propputref |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2afa793371f2e9840bbb98efc9f745ecbdd29b7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389325"
---
# <a name="propputref"></a>propputref

指定使用引用而不是值的属性设置函数。

## <a name="syntax"></a>语法

```cpp
[propputref]
```

## <a name="remarks"></a>备注

**Propputref** c + + 属性具有相同的功能[propputref](/windows/desktop/Midl/propputref) MIDL 特性。

## <a name="example"></a>示例

有关示例，请参阅[可绑定](../windows/bindable.md)的示例使用**propputref**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|方法|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|`propget`, `propput`|

有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[方法特性](../windows/method-attributes.md)<br/>
[propget](../windows/propget.md)<br/>
[propput](../windows/propput.md)  