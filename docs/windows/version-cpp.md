---
title: "version (C++) | Microsoft Docs"
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
  - "vc-attr.version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "version attribute"
  - "version information, version attribute"
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# version (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标识在类中的多个版本的特定版本。  
  
## 语法  
  
```  
  
      [ version(  
   "version"  
) ]  
```  
  
#### 参数  
 *Version — 版本*  
 coclass 的版本号。  如果未指定， 1.0 在 .idl 文件将放置。  
  
## 备注  
 **版本** C\+\+ 特性具有与 [版本](http://msdn.microsoft.com/library/windows/desktop/aa367306) MIDL 属性与和传递到生成的 .idl 文件。  
  
## 示例  
 请参见 [可绑定](../windows/bindable.md) 示例为 **版本**的示例使用。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|**coclass**|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)