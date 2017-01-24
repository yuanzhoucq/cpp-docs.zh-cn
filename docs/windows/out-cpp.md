---
title: "out (C++) | Microsoft Docs"
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
  - "vc-attr.out"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "out 特性"
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# out (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标识从被调用过程返回到调用过程（从服务器到客户端）的指针参数。  
  
## 语法  
  
```  
  
[out]  
  
```  
  
## 备注  
 **out** C\+\+ 属性具有与 [out](http://msdn.microsoft.com/library/windows/desktop/aa367136) MIDL 属性相同的功能。  
  
## 示例  
 请参阅 [bindable](../windows/bindable.md) 示例以了解 **out** 的示例使用。  
  
## 要求  
  
### 特性上下文  
  
|||  
|-|-|  
|**适用对象**|接口参数|  
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见[特性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [defaultvalue](../windows/defaultvalue.md)   
 [id](../windows/id.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)