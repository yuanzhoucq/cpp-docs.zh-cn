---
title: "no_injected_text | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.no_injected_text"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_injected_text attribute"
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# no_injected_text
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由于属性使用，以防止编译器插入代码。  
  
## 语法  
  
```  
  
      [ no_injected_text(  
   boolean  
) ];  
```  
  
#### 参数  
 `boolean`\(可选\)  
 **true** ，如果不需要插入的代码，允许代码的 **错误** 插入。  **true** 是默认设置。  
  
## 备注  
 最常见 **no\_injected\_text** C\+\+ 特性由 [\/Fx](../build/reference/fx-merge-injected-code.md) 编译器选项，插入 **no\_injected\_text** 属性设置为 .mrg 文件中。  
  
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
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)