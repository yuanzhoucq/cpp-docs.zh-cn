---
title: requires_category |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.requires_category
dev_langs:
- C++
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ddcfe01ec5bd838a84ddad351f43802a8142b44
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606096"
---
# <a name="requirescategory"></a>requires_category
指定目标类的所需的组件类别。  
  
## <a name="syntax"></a>语法  
  
```  
[ requires_category(   
  requires_category  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *requires_category*  
 所需的类别的 ID。  
  
## <a name="remarks"></a>备注  
 **Requires_category** c + + 属性指定目标类所需的组件类别。 有关详细信息，请参阅[REQUIRED_CATEGORY](../atl/reference/category-macros.md#required_category)。  
  
 此属性要求 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi_progid](../windows/vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。  
  
## <a name="example"></a>示例  
 下面的代码要求该对象实现的控制类别。  
  
```cpp  
// cpp_attr_ref_requires_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLibrary")];  
  
[ coclass, requires_category("CATID_Control"),  
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]  
class CMyClass {};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**，**结构**|  
|**可重复**|否|  
|**必需的特性**|一个或多个以下： `coclass`， `progid`，或`vi_progid`。|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [COM 特性](../windows/com-attributes.md)   
 [implements_category](../windows/implements-category.md)   