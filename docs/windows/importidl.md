---
title: "importidl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.importidl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "importidl attribute"
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# importidl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

插入指定的 .idl 文件添加到生成的 .idl 文件中。  
  
## 语法  
  
```  
  
      [ importidl(  
   idl_file  
) ];  
```  
  
#### 参数  
 `idl_file`  
 标识要与 .idl 文件合并为应用程序将生成 .idl 文件的名称。  
  
## 备注  
 **importidl** C\+\+ 特性将部分在库的外部块 \(在 `idl_file`\) 到程序的生成的 .idl 文件和库部分 \(在 `idl_file`\) 到程序中生成的 .idl 文件的库 " 一节。  
  
 ，如果要使用已生成的 .idl 文件中，一手动编写代码的 .idl 文件，如您可能需要使用 **importidl**。  
  
## 示例  
  
```  
// cpp_attr_ref_importidl.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[importidl("import.idl")];  
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
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [import](../windows/import.md)   
 [importlib](../windows/importlib.md)   
 [include](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)