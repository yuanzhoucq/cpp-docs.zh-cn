---
title: "hidden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.hidden"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hidden attribute"
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# hidden
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示该项目在面向用户的浏览器存在，但不应显示。  
  
## 语法  
  
```  
  
[hidden]  
  
```  
  
## 备注  
 **隐藏** C\+\+ 特性具有与 [隐藏](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL 属性相同。  
  
## 示例  
 有关示例的 [可绑定](../windows/bindable.md) 参见示例中使用 **隐藏**。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`， **类**， `struct`，方法，属性|  
|**可重复**|否|  
|**必需的特性**|**coclass** \(当应用于 **类** 或 `struct`\)|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)