---
title: "entry | Microsoft Docs"
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
  - "vc-attr.entry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "entry attribute"
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# entry
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定一个导出函数或在一个模块的常数传递标识在 DLL 入口点。  
  
## 语法  
  
```  
  
      [ entry(  
   id  
) ]  
```  
  
#### 参数  
 `id`  
 的 ID 入口点。  
  
## 备注  
 **项** C\+\+ 特性具有与 [项](http://msdn.microsoft.com/library/windows/desktop/aa366815) MIDL 属性相同。  
  
## 示例  
 为 [idl\_module](../windows/idl-module.md) 参见示例为 **项**的示例使用。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`idl_module` 特性|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)