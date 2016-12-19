---
title: "registration_script | Microsoft Docs"
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
  - "vc-attr.registration_script"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "registration_script attribute"
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# registration_script
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

执行指定的自定义脚本注册。  
  
## 语法  
  
```  
  
      [ registration_script(   
   script   
) ]  
```  
  
#### 参数  
 *script*  
 自定义注册脚本 \(.rgs\) 文件的完整路径。  **无**的值，如 `script = "none"`，指示 coclass 没有注册要求。  
  
## 备注  
 **registration\_script** C\+\+ 特性执行 **脚本**指定的自定义脚本注册。  如果未指定该特性， \(包含注册的元素信息\) 使用标准 .rgs 文件。  有关 .rgs 文件的更多信息，请参见 [ATL 注册表元素 \(管理员\)](../atl/atl-registry-component-registrar.md)。  
  
 此特性要求 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi\_progid](../windows/vi-progid.md) 属性 \(或表示这些中为\) 的其他特性也适用于同一元素。  
  
## 示例  
 下面的代码指定元素具有调用 cpp\_attr\_ref\_registration\_script.rgs 的一个注册表脚本。  
  
```  
// cpp_attr_ref_registration_script.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="REG")];  
  
[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]  
__interface IFace {};  
  
// requires "cpp_attr_ref_registration_script.rgs"  
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist  
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),  
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]  
class CMyClass:public IFace {};  
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
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [rdx](../windows/rdx.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)