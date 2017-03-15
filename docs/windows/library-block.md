---
title: "library_block | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.library_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "library_block attribute"
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# library_block
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 IDL 库中的构造块。  
  
## 语法  
  
```  
  
[library_block]  
  
```  
  
## 备注  
 当您将在库中的构造块，确保它将传递给类型库，无论其是否引用。  默认情况下， [coclass](../windows/coclass.md)、 [dispinterface](../windows/dispinterface.md)和 [idl\_module](../windows/idl-module.md) 属性修改的构造仅在库中放置块。  
  
## 示例  
 在下面的代码中，自定义接口放置在库中块。  
  
```  
// cpp_attr_ref_library_block.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib")];  
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface IMyInterface {  
   HRESULT f1();  
};  
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
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)