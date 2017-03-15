---
title: "object (C++) | Microsoft Docs"
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
  - "vc-attr.object"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "object attribute"
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# object (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标识自定义接口。  
  
## 语法  
  
```  
  
[object]  
  
```  
  
## 备注  
 在前面接口定义时， **对象** C\+\+ 特性在 .idl 文件错误引起接口将作为自定义接口。  
  
 已标记的所有接口的对象必须从 **IUnknown**继承。  ，如果任何基接口从 **IUnknown**，继承此满足条件。  如果基接口不从 **IUnknown**继承，编译器将导致标记的接口。 **对象** 从 **IUnknown**派生。  
  
## 示例  
 为的示例演示如何参见 [nonbrowsable](../windows/nonbrowsable.md) 使用 **对象**。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [dual](../windows/dual.md)   
 [dispinterface](../windows/dispinterface.md)   
 [custom](../windows/custom-cpp.md)   
 [\_\_interface](../cpp/interface.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)