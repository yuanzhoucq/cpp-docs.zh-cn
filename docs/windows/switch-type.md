---
title: switch_type |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1870e1ee623d8495e9f19dd8f32ea9382070bc14
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890173"
---
# <a name="switchtype"></a>switch_type
标识用作联合判别变量的类型。  
  
## <a name="syntax"></a>语法  
  
```  
  
[switch_type(  
type  
}]  
  
```  
  
#### <a name="parameters"></a>参数  
 `type`  
 交换机类型可以是整数、 字符、 布尔值或枚举类型。  
  
## <a name="remarks"></a>备注  
 **Switch_type** c + + 属性具有相同的功能[switch_type](http://msdn.microsoft.com/library/windows/desktop/aa367276) MIDL 特性。  
  
 不支持 c + + 特性[封装联合](http://msdn.microsoft.com/library/windows/desktop/aa366811)。 [Nonencapsulated 的联合](http://msdn.microsoft.com/library/windows/desktop/aa367119)仅支持以下形式：  
  
```  
// cpp_attr_ref_switch_type.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
[ export ]  
struct SizedValue2 {  
   [switch_type("char"), switch_is(kind)] union {  
      [case(1), string]  
         wchar_t* wval;  
      [default, string]  
         char* val;  
   };  
   char kind;  
};  
```  
  
## <a name="example"></a>示例  
 请参阅[用例](../windows/case-cpp.md)更大的示例的示例使用**switch_type**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`typedef`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   
