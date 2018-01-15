---
title: "聚合 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.aggregatable
dev_langs: C++
helpviewer_keywords: aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec044e18fdd8bcd21fbad8d2e46c847c876cc00d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="aggregatable"></a>aggregatable
指示的类支持聚合。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ aggregatable(   
   value  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *值*（可选）  
 用于指示何时可聚合 COM 对象的参数：  
  
-   **永远不会**COM 对象无法聚合。  
  
-   **允许**可以直接创建 COM 对象或可聚合。 这是默认设置。  
  
-   **始终**COM 对象不能直接创建和仅可聚合。 当调用`CoCreateInstance`对于此对象，你必须指定聚合对象的**IUnknown**接口 (控制**IUnknown**)。  
  
## <a name="remarks"></a>备注  
 **聚合**c + + 属性具有相同的功能[聚合](http://msdn.microsoft.com/library/windows/desktop/aa366721)MIDL 特性。 这意味着，编译器将通过**聚合**属性通过生成的.idl 文件。  
  
 此属性要求 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi_progid](../windows/vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果应用 **progid** ，则也会应用 **vi_progid** 和 **coclass** 。  
  
 **ATL 项目**  
  
 如果在使用 ATL 的项目中使用此属性，该属性的行为将会更改。 除了前面所述的行为，该属性还添加以下宏之一与目标类：  
  
|参数值|插入的宏|  
|---------------------|--------------------|  
|**永远不会**|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|  
|**允许**|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|  
|始终|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|  
  
## <a name="example"></a>示例  
  
```  
// cpp_attr_ref_aggregatable.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="MyModule")];  
  
[ coclass, aggregatable(allowed),  
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]  
class CMyClass {};  
```  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**， `struct`|  
|**可重复**|否|  
|**必需的特性**|以下一个或多个属性： **coclass**、 **progid**或 **vi_progid**。|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
