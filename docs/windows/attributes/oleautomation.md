---
title: oleautomation （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 201916eeb235d48473d21188da42d19cafb93bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214644"
---
# <a name="oleautomation"></a>oleautomation

指示接口与自动化兼容。

## <a name="syntax"></a>语法

```cpp
[oleautomation]
```

## <a name="remarks"></a>备注

**Oleautomation** C++特性具有与[oleautomation](/windows/win32/Midl/oleautomation) MIDL 特性相同的功能。

## <a name="example"></a>示例

若要使用**oleautomation**的示例，请参阅[defaultvalue](defaultvalue.md)和[nonextensible](nonextensible.md)的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**接口**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|**dispinterface**|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)
