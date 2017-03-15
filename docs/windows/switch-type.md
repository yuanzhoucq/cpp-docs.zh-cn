---
title: "switch_type | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.switch_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "switch_type attribute"
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# switch_type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标识为该联合使用的变量的类型具有识别力。  
  
## 语法  
  
```  
  
[switch_type(  
type  
}]  
  
```  
  
#### 参数  
 `type`  
 切换类型，可以是整数、字符， boolean 或枚举类型。  
  
## 备注  
 **switch\_type** C\+\+ 特性具有与 [switch\_type](http://msdn.microsoft.com/library/windows/desktop/aa367276) MIDL 属性相同。  
  
 C\+\+ 特性不支持 [封装的联合](http://msdn.microsoft.com/library/windows/desktop/aa366811)。  [Nonencapsulated 联合](http://msdn.microsoft.com/library/windows/desktop/aa367119) 仅支持为以下形式:  
  
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
  
## 示例  
 请参见 [用例](../windows/case-cpp.md) 示例为 **switch\_type**的示例使用。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`typedef`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)