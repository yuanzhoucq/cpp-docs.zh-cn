---
title: "helpcontext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.helpcontext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpcontext attribute"
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# helpcontext
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定可获取有关此元素的用户查看信息在帮助文件的上下文 ID。  
  
## 语法  
  
```  
  
      [ helpcontext(  
   id  
) ]  
```  
  
#### 参数  
 `id`  
 帮助主题的上下文 ID。  请参见 [HTML 帮助：为程序提供区分上下文的帮助](../mfc/html-help-context-sensitive-help-for-your-programs.md) 有关上下文 ID 的更多信息。  
  
## 备注  
 **helpcontext** C\+\+ 特性具有与 [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) MIDL 属性相同。  
  
## 示例  
 有关示例的 [defaultvalue](../windows/defaultvalue.md) 参见示例中使用 **helpcontext**。  
  
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
 [helpstring](../windows/helpstring.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)