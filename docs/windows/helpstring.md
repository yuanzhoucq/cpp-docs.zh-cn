---
title: "helpstring | Microsoft Docs"
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
  - "vc-attr.helpstring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpstring attribute [C++]"
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# helpstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定一个字符串，该字符串用来描述它所应用的元素。  
  
## 语法  
  
```  
  
      [ helpstring(  
   "string"  
) ]  
```  
  
#### 参数  
 `string`  
 帮助字符串的文本。  
  
## 备注  
 **helpstring** C\+\+ 特性具有与 [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) MIDL 属性相同。  
  
## 示例  
 有关示例的 [defaultvalue](../windows/defaultvalue.md) 参见示例中使用 **helpstring**。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`， `typedef`， **类**，方法，属性|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [helpfile](../windows/helpfile.md)   
 [helpcontext](../windows/helpcontext.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)