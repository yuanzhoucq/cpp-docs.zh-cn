---
title: oleautomation (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 74701742de904b76e7b1152c8ddb3f2f5dd953c2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031707"
---
# <a name="oleautomation"></a>oleautomation

指示接口使用自动化兼容。

## <a name="syntax"></a>语法

```cpp
[oleautomation]
```

## <a name="remarks"></a>备注

**Oleautomation** C++属性具有相同的功能[oleautomation](/windows/desktop/Midl/oleautomation) MIDL 特性。

## <a name="example"></a>示例

请参阅有关[defaultvalue](defaultvalue.md)并[nonextensible](nonextensible.md)的示例使用**oleautomation**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|**dispinterface**|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)