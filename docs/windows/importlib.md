---
title: "importlib | Microsoft Docs"
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
  - "vc-attr.importlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "importlib attribute"
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# importlib
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使已编译到另一个类型库中的类型可供所创建的类型库使用。  
  
## 语法  
  
```  
  
        [ importlib(  
   "tlb_file"  
) ];  
```  
  
#### 参数  
 *tlb\_file*  
 要导入当前项目类型库中的 .tlb 文件的名称（用引号引起来）。  
  
## 备注  
 **importlib** C\+\+ 特性使 `importlib` 语句放置在生成的 .idl 文件的库块中。  **importlib** 特性具有与 [importlib](http://msdn.microsoft.com/library/windows/desktop/aa367050) MIDL 特性相同的功能。  
  
## 示例  
 下面的代码演示如何使用 **importlib** 的示例：  
  
```  
// cpp_attr_ref_importlib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importlib("importlib.tlb")];  
```  
  
## 要求  
  
### 特性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关详细信息，请参见[特性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [import](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [include](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)