---
title: "size_is | Microsoft Docs"
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
  - "vc-attr.size_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size_is attribute"
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# size_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为大小的指针、大小的指向大小的指针和单项或多维数组指定内存大小分配。  
  
## 语法  
  
```  
  
      [ size_is(  
   "expression"  
) ]  
```  
  
#### 参数  
 *表达式*  
 为大小的指针分配的内存的大小。  
  
## 备注  
 **size\_is** C\+\+ 特性具有与 [size\_is](http://msdn.microsoft.com/library/windows/desktop/aa367164) MIDL 属性相同。  
  
## 示例  
 有关示例的 [first\_is](../windows/first-is.md) 参见中的示例演示如何指定数组的一部分。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|字段在 `struct` 或 **联合**，接口参数，接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|**max\_is**|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [first\_is](../windows/first-is.md)   
 [last\_is](../windows/last-is.md)   
 [max\_is](../windows/max-is.md)   
 [length\_is](../windows/length-is.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)