---
title: "helpfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.helpfile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "helpfile attribute"
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# helpfile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

设置帮助文件的名称类型库。  
  
## 语法  
  
```  
  
      [ helpfile(  
   "filename"  
) ]  
```  
  
#### 参数  
 *filename*  
 包含帮助主题文件的名称。  
  
## 备注  
 **helpfile** C\+\+ 特性具有与 [helpfile](http://msdn.microsoft.com/library/windows/desktop/aa366853) MIDL 属性相同。  
  
## 示例  
 有关示例的 [模块](../windows/module-cpp.md) 参见示例中使用 **helpfile**。  
  
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
 [helpcontext](../windows/helpcontext.md)   
 [helpstring](../windows/helpstring.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)