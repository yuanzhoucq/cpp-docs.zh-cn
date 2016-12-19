---
title: "id | Microsoft Docs"
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
  - "vc-attr.id"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "id attribute"
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# id
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于成员函数 \(一个属性或将方法指定 `dispid` 参数，在接口或调度接口\)。  
  
## 语法  
  
```  
  
      [ id(  
   dispid  
) ]  
```  
  
#### 参数  
 `dispid`  
 接口方法的调度 ID。  
  
## 备注  
 **id** C\+\+ 特性具有与 [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) MIDL 属性相同。  
  
## 示例  
 有关示例的 [可绑定](../windows/bindable.md) 参见示例中使用 **id**。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Data Member Attributes](../windows/data-member-attributes.md)   
 [defaultvalue](../windows/defaultvalue.md)   
 [in](../windows/in-cpp.md)   
 [输出](../windows/out-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)