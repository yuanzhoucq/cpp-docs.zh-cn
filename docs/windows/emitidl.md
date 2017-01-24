---
title: "emitidl | Microsoft Docs"
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
  - "vc-attr.emitidl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "emitidl attribute"
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# emitidl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

确定所有后续 IDL 特性是否在生成的 .idl 文件进行处理和放置。  
  
## 语法  
  
```  
  
      [ emitidl([boolean],  
   defaultimports=[boolean]  
) ] ;  
```  
  
#### 参数  
 `boolean`  
 可能的值: **true**、 **错误**、 **强制**、 **限制**、 **驱动器**或 **方式安排**。  
  
-   如果 **true**，源代码文件中遇到的任何 IDL category 特性在生成的 .idl 文件将放置。  将设置为 **emitidl**的默认设置。  
  
-   如果 **错误**，源代码文件中遇到的任何 IDL category 特性在生成的 .idl 文件不会放置。  
  
-   如果 **限制**，允许 IDL 特性在文件，而不 [模块](../windows/module-cpp.md) 属性。  编译器不会生成 .idl 文件。  
  
-   如果 **强制**，重写一个后续 **限制** 属性，需要一个文件具有 **模块** 属性，如果在文件的 IDL 特性。  
  
-   **驱动器** 可以保存当前 **emitidl** 设置为内部 **emitidl** 堆栈，并且， **方式安排** 允许您设置 **emitidl** 到任何值是在内部 **emitidl** 堆栈顶部。  
  
 **defaultimports** *\=*\[\(可选\) 的 `boolean`\]  
 -   如果 `boolean` 是 **true**， docobj.idl 将导入到生成的 .idl 文件。  此外，; 如果有名称的 .idl 文件和 .h 文件位于要 `#include` 到源代码中的目录中查找和 .h 文件，然后生成的 .idl 文件相同将包含该的 imports 语句 .idl 文件。  
  
-   如果 `boolean` 是 **错误**， docobj.idl 不会导入到生成的 .idl 文件。  您将需要显式导入具有 [导入](../windows/import.md)的 .idl 文件。  
  
## 备注  
 在 **emitidl** C\+\+ 特性在源代码文件后遇到， IDL category 特性在生成的 .idl 文件将放置。  如果没有 **emitidl** 属性，在源代码文件的 IDL 特性将为输出到生成的 .idl 文件。  
  
 在源代码文件的多个 **emitidl** 属性是可能的。  如果 `[emitidl(false)];` 在遇到文件，而无需后续 `[emitidl(true)];`，则属性不会处理到生成的 .idl 文件。  
  
 每次编译器遇到了新文件， **emitidl** 隐式设置为 **true**。  
  
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
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)