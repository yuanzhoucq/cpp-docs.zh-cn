---
title: "retval | Microsoft Docs"
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
  - "vc-attr.retval"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "retval attribute"
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# retval
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定接收该成员的返回值的参数。  
  
## 语法  
  
```  
  
[retval]  
  
```  
  
## 备注  
 **retval** C\+\+ 特性具有与 [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) MIDL 属性相同。  
  
 **retval** 必须出现在函数声明中的最后一个参数。  
  
## 示例  
 为 [可绑定](../windows/bindable.md) 参见示例为 **retval**的示例使用。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|接口参数，接口方法|  
|**可重复**|否|  
|**必需的特性**|**out**|  
|**无效的特性**|**in**|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)