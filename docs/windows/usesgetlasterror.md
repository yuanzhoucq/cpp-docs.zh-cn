---
title: "usesgetlasterror | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.usesgetlasterror"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "usesgetlasterror attribute"
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# usesgetlasterror
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通知调用方，则出现错误，则调用该函数，则调用方可以调用 `GetLastError` 检索错误代码。  
  
## 语法  
  
```  
  
[usesgetlasterror]  
  
```  
  
## 备注  
 **usesgetlasterror** C\+\+ 特性具有与 [usesgetlasterror](http://msdn.microsoft.com/library/windows/desktop/aa367297) MIDL 属性相同。  
  
## 示例  
 有关示例如何参见 [idl\_module](../windows/idl-module.md) 示例使用 **usesgetlasterror**。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**模块** 属性|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)