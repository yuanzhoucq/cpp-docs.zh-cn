---
title: oleautomation （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.oleautomation
dev_langs:
- C++
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3a0ec5a39d6e99e5ceb6ec4ed089373e3057c1e
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790350"
---
# <a name="oleautomation"></a>oleautomation

指示接口使用自动化兼容。

## <a name="syntax"></a>语法

```cpp
[oleautomation]
```

## <a name="remarks"></a>备注

**Oleautomation** c + + 属性具有相同的功能[oleautomation](/windows/desktop/Midl/oleautomation) MIDL 特性。

## <a name="example"></a>示例

请参阅有关[defaultvalue](defaultvalue.md)并[nonextensible](nonextensible.md)的示例使用**oleautomation**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**interface**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|**dispinterface**|

有关特性上下文的详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)  