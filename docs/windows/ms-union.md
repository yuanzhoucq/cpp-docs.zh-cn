---
title: "ms_union | Microsoft Docs"
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
  - "vc-attr.ms_union"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ms_union attribute"
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ms_union
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控件 nonencapsulated 联合的网络数据表示形式对齐。  
  
## 语法  
  
```  
  
[ms_union]  
  
```  
  
## 备注  
 **ms\_union** C\+\+ 特性具有与 [ms\_union](http://msdn.microsoft.com/library/windows/desktop/aa367100) MIDL 属性相同。  
  
## 示例  
 下面的代码演示 **ms\_union**的位置:  
  
```  
// cpp_attr_ref_ms_union.cpp  
// compile with: /LD  
#include <unknwn.h>  
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl {  
   HRESULT DisplayString([in, string] char * p1);  
};  
  
[export, switch_type(short)] union _WILLIE_UNION_TYPE  {  
   [case(24)]  
      float fMays;  
   [case(25)]  
      double dMcCovey;  
   [default]  
      int x;  
 };  
  
[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;  
  
[module(name="ATLFIRELib")];  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|Nonencapsulated 联合|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|**dispinterface**|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)