---
title: "aggregatable | Microsoft Docs"
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
  - "vc-attr.aggregatable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregatable attribute"
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# aggregatable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示类支持聚合。  
  
## 语法  
  
```  
  
      [ aggregatable(   
   value  
) ]  
```  
  
#### 参数  
 *值* \(可选\)  
 指示 COM 对象时的参数可聚合:  
  
-   **从未** COM 对象不能聚合。  
  
-   **允许** COM 对象可以直接创建或其进行聚合。  这是默认值。  
  
-   **始终** COM 对象不直接创建并只能聚合。  当调用此对象的 `CoCreateInstance` 时，必须指定复合对象的 **IUnknown** 接口 \(控件 **IUnknown**\)。  
  
## 备注  
 **可聚集的** C\+\+ 特性具有与 [可聚集的](http://msdn.microsoft.com/library/windows/desktop/aa366721) MIDL 属性相同。  这意味着编译器将通过 **可聚集的** 属性设置为生成的 .idl 文件。  
  
 此特性要求 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi\_progid](../windows/vi-progid.md) 属性 \(或表示这些中为\) 的其他特性也适用于同一元素。  如果使用任何单一属性，自动应用其他两个。  例如，因此，如果 **progid** 是应用的，也适用 **vi\_progid** 和 **coclass** 。  
  
 **ATL 项目**  
  
 如果此属性在使用 ATL 项目中使用，属性的行为更改。  除该前面所述的行为之外，特性也添加下面的宏之一添加到目标类:  
  
|参数值|插入的宏|  
|---------|----------|  
|**从不**|[DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)|  
|**允许**|[DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md)|  
|**始终**|[DECLARE\_ONLY\_AGGREGATABLE](../Topic/DECLARE_ONLY_AGGREGATABLE.md)|  
  
## 示例  
  
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
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|一个或多个以下各项: **coclass**、 **progid**或 **vi\_progid**。|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Aggregation](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)