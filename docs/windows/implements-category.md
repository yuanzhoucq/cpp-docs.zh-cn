---
title: "implements_category | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.implements_category"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "implements_category attribute"
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# implements_category
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定目标类实现的组件类。  
  
## 语法  
  
```  
  
      [ implements_category(  
   implements_category="uuid"  
) ]  
```  
  
#### 参数  
 **implements\_category**  
 实现的类的 ID。  
  
## 备注  
 **implements\_category** C\+\+ 特性指定目标类实现的组件类。  这是通过创建类映射和添加 **implements\_category** 属性指定的单独的项完成。  有关更多信息，请参见 [什么是如何组件类及其工作?](http://msdn.microsoft.com/library/windows/desktop/ms694322)。  
  
 此特性要求 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi\_progid](../windows/vi-progid.md) 属性 \(或表示这些中为\) 的其他特性也适用于同一元素。  如果使用任何单一属性，自动应用其他两个。  例如，因此，如果 **progid** 是应用的，也适用 **vi\_progid** 和 **coclass** 。  
  
## 示例  
 下面的代码指定以下对象实现控件类。  
  
```  
// cpp_attr_ref_implements_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLib")];  
[ coclass, implements_category("CATID_Control"),  
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]  
class CMyClass {};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|是|  
|**必需的特性**|下列操作之一: **coclass**、 **progid**或 **vi\_progid**|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [IMPLEMENTED\_CATEGORY](../Topic/IMPLEMENTED_CATEGORY.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)