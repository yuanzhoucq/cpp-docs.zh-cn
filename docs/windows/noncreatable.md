---
title: "noncreatable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.noncreatable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "noncreatable attribute"
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# noncreatable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义不能单独实例化的对象。  
  
## 语法  
  
```  
  
[noncreatable]  
  
```  
  
## 备注  
 **不可创建** C\+\+ 特性具有与 [不可创建](http://msdn.microsoft.com/library/windows/desktop/aa367118) MIDL 属性相同通过自动传递到生成的 .IDL 文件编译器。  
  
 当此属性在使用 ATL 项目中时，属性的行为更改。  除了上面的行为之外，特性也插入 [OBJECT\_ENTRY\_NON\_CREATEABLE\_EX\_AUTO](../Topic/OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO.md) 宏。  此宏指示为 ATL 对象无法创建外部。  
  
## 示例  
  
```  
// cpp_attr_ref_noncreatable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("11111111-1111-1111-1111-111111111111")]  
__interface A   
{  
};  
  
[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]  
class CMyClass : public A   
{  
   HRESULT xx();  
};  
```  
  
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
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)