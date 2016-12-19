---
title: "aggregates | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.aggregates"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregates 特性"
  - "聚合 [C++]"
  - "聚合对象 [C++], aggregates 属性"
  - "聚合 [C++]"
ms.assetid: 67a084c9-941f-474b-a029-9c93b38ebe9a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# aggregates
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示对象聚合由 CLSID 指定的对象。  
  
## 语法  
  
```  
  
[ aggregates(  
clsid,  
variable_name  
) ]  
  
```  
  
#### 参数  
 `clsid`  
 指定可聚合对象的 CLSID。  
  
 `variable_name`  
 要插入的变量的名称。 此变量包含所聚合的对象的 **IUnknown**。  
  
## 备注  
 应用于对象时，**aggregates** C\+\+ 属性会为所聚合的对象（由 `clsid` 指定）实现外部包装器。  
  
 此属性要求 [coclass](../windows/coclass.md)、[progid](../windows/progid.md) 或 [vi\_progid](../windows/vi-progid.md) 属性（或隐含这些属性之一的其他属性）也应用于同一个元素。 如果使用任何单个属性，则会自动应用另外两个属性。 例如，如果应用 **progid**，则也会应用 **vi\_progid** 和 **coclass**。  
  
 **ATL 项目**  
  
 如果在使用 ATL 的项目中使用此属性，该属性的行为将会更改。 首先，将以下条目添加到目标对象的 COM 映射：  
  
```  
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(_m_spAttrXXX, clsid)  
```  
  
 其次，还会添加 [DECLARE\_GET\_CONTROLLING\_UNKNOWN](../Topic/DECLARE_GET_CONTROLLING_UNKNOWN.md) 宏。  
  
## 示例  
  
```  
// cpp_attr_ref_aggregates.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
// requires 'aggregatable.dll'  
// see aggregatable attribute to create 'aggregatable.dll'  
class DECLSPEC_UUID("1a8369cc-1c91-42c4-befa-5a5d8c9d2529") CMyClass;  
  
[module (name="MYObject")];  
[object, uuid("ab006d85-e754-47c5-9ef4-2744ff32a20c")]  
__interface IObject  
{  
};  
  
[ coclass, aggregates(__uuidof(CMyClass)),   
  uuid("91cb2c06-8931-432a-baac-206e55c4edfb")]  
struct CObject : IObject  
{  
   int i;  
};  
```  
  
## 要求  
  
### 特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**，`struct`|  
|**可重复**|是|  
|**必需的特性**|以下一个或多个属性：**coclass**、**progid** 或 **vi\_progid**。|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见[特性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
 [可聚合](http://msdn.microsoft.com/library/windows/desktop/aa366721)   
 [COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE\_BLIND](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)