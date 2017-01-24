---
title: "cpp_quote | Microsoft Docs"
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
  - "vc-attr.cpp_quote"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cpp_quote attribute"
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# cpp_quote
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

发出该指定字符串，因此，不带引号字符，到生成的 .idl 文件。  
  
## 语法  
  
```  
  
      [ cpp_quote(  
   "statement"  
) ];  
```  
  
#### 参数  
 *statement*  
 对. 命令。  
  
## 备注  
 ，如果您在 .idl 文件中，要将预处理器指令 **cpp\_quote** C\+\+ 特性非常有用。  
  
 作为 MIDL 生成的一部分，也可以使用 **cpp\_quote** 和生成 .h 文件。  例如，因此，如果您具有 c. C\+\+ 使用 C\+\+ IDL 特性的头文件，但不能为某任务使用该文件，然后可以生成它创建一个 MIDL 生成的 .h 文件，您应当能够使用。  
  
 **cpp\_quote** 属性具有与 [cpp\_quote](http://msdn.microsoft.com/library/windows/desktop/aa366765) MIDL 属性相同。  
  
## 示例  
 为 [双](../windows/dual.md) 参见本示例对示例使用如何使用 **cpp\_quote**。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)