---
title: "custom (C++) | Microsoft Docs"
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
  - "vc-attr.custom"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "custom attributes, defining"
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# custom (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义对象的元数据在类型库。  
  
## 语法  
  
```  
  
      [ custom(  
   uuid,   
   value  
) ];  
```  
  
#### 参数  
 *uuid*  
 唯一 ID。  
  
 *值*  
 可以将其置于变量的值。  
  
## 备注  
 **自定义** C\+\+ 属性将导致信息放置到类型库。  您将需要读取从类型库的自定义值的工具。  
  
 **自定义** 属性具有与 [自定义](http://msdn.microsoft.com/library/windows/desktop/aa366766) MIDL 属性相同。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|非 COM `interface`， **类**， `enum`的， `idl_module` 方法，接口成员，接口参数， `typedef`的， **联合**的， `struct`。|  
|**可重复**|是|  
|**必需的特性**|**coclass** \(当使用类\)|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)