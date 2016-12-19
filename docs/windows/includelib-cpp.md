---
title: "includelib (C++) | Microsoft Docs"
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
  - "vc-attr.includelib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "includelib attribute"
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# includelib (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

导致在生成的 .idl 文件将包含的 .idl 或 .h 文件。  
  
## 语法  
  
```  
  
      [ includelib(  
   name.idl  
) ];  
```  
  
#### 参数  
 *name.idl*  
 .idl 文件的名称作为生成的 .idl 文件的一部分，您要包括。  
  
## 备注  
 `includelib` C\+\+ 特性会在生成的 .idl 文件将包含的 .idl 或 .h 文件，在 `importlib` 语句之后。  
  
## 示例  
 下面的代码在 .cpp 文件示:  
  
```  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|是|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [import](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [include](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)