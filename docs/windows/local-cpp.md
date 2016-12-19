---
title: "local (C++) | Microsoft Docs"
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
  - "vc-attr.local"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "local attribute"
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# local (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当在接口头，允许您使用 MIDL 编译器作为页眉生成器。  当在单个函数，即存根未生成一个本地程序。  
  
## 语法  
  
```  
  
[local]  
  
```  
  
## 备注  
 `local` C\+\+ 特性具有与 [本地](http://msdn.microsoft.com/library/windows/desktop/aa367071) MIDL 属性相同。  
  
## 示例  
 为的示例演示如何参见 [call\_as](../windows/call-as.md) 使用 `local`。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`，接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|**dispinterface**|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [call\_as](../windows/call-as.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)