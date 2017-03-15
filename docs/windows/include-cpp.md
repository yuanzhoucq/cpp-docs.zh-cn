---
title: "include (C++) | Microsoft Docs"
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
  - "vc-attr.include"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "include attribute"
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# include (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定在生成的 .idl 文件将包含的一个或多个头文件。  
  
## 语法  
  
```  
  
      [ include(  
   header_file  
) ];  
```  
  
#### 参数  
 *header\_file*  
 文件的名称要包含在生成的 .idl 文件。  
  
## 备注  
 **包含** C\+\+ 特性在生成的 .idl 文件错误引起一个 `#include` 语句放置在 `import "docobj.idl"` 语句下面。  
  
 **包含** C\+\+ 特性具有与 [包含](http://msdn.microsoft.com/library/windows/desktop/aa367052) MIDL 属性相同。  
  
## 示例  
 下面的代码演示了如何使用 **包含**。  对于此示例，文件 include.h 只包含一个 \#include 语句。  
  
```  
// cpp_attr_ref_include.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[include(cpp_attr_ref_include.h)];  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [import](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [includelib](../windows/includelib-cpp.md)   
 [importlib](../windows/importlib.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)