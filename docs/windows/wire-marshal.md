---
title: "wire_marshal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.wire_marshal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wire_marshal attribute"
ms.assetid: 244f9d72-776d-4ebd-b60a-cee600a126b5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# wire_marshal
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定在传输将使用而不是一个特定的数据类型的数据类型。  
  
## 语法  
  
```  
  
[wire_marshal]  
  
```  
  
## 备注  
 **wire\_marshal** C\+\+ 特性具有与 [wire\_marshal](http://msdn.microsoft.com/library/windows/desktop/aa367309) MIDL 属性相同。  
  
## 示例  
 下面的代码演示 **wire\_marshal**的使用:  
  
```  
// cpp_attr_ref_wire_marshal.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[export, public] typedef unsigned long _FOUR_BYTE_DATA;  
  
[export] typedef struct _TWO_X_TWO_BYTE_DATA {  
   unsigned short low;  
   unsigned short high;  
} TWO_X_TWO_BYTE_DATA ;  
  
[export, wire_marshal(TWO_X_TWO_BYTE_DATA)] typedef _FOUR_BYTE_DATA FOUR_BYTE_DATA;  
```  
  
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
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)