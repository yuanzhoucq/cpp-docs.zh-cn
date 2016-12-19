---
title: "last_is | Microsoft Docs"
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
  - "vc-attr.last_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "last_is attribute"
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# last_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定要传输的最后一个数组元素的索引。  
  
## 语法  
  
```  
  
      [ last_is(  
   "expression"  
) ]  
```  
  
#### 参数  
 *表达式*  
 一个或多个 C 语言表达式。  空参数允许槽。  
  
## 备注  
 **last\_is** C\+\+ 特性具有与 [last\_is](http://msdn.microsoft.com/library/windows/desktop/aa367066) MIDL 属性相同。  
  
## 示例  
 为的示例演示如何参见 [first\_is](../windows/first-is.md) 指定数组的一部分。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|字段在 `struct` 或 **联合**，接口参数，接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [first\_is](../windows/first-is.md)   
 [max\_is](../windows/max-is.md)   
 [length\_is](../windows/length-is.md)   
 [size\_is](../windows/size-is.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)