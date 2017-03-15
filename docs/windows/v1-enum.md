---
title: "v1_enum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.v1_enum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "v1_enum attribute"
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# v1_enum
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命令，指定的枚举类型传输作为 32 位实体而不是该 16 位默认值。  
  
## 语法  
  
```  
  
[v1_enum]  
  
```  
  
## 备注  
 **v1\_enum** C\+\+ 特性具有与 [v1\_enum](http://msdn.microsoft.com/library/windows/desktop/aa367303) MIDL 属性相同。  
  
## 示例  
 下面的代码演示 **v1\_enum**的使用:  
  
```  
// cpp_attr_ref_v1_enum.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export, v1_enum]   
enum eList {   
   e1 = 1,   
   e2 = 2  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|枚举类型|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)