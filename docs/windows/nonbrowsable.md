---
title: "nonbrowsable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.nonbrowsable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nonbrowsable attribute"
ms.assetid: e71a98e7-4b65-454a-9829-342b9f2a84be
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# nonbrowsable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示接口成员在属性浏览器不应显示。  
  
## 语法  
  
```  
  
[nonbrowsable]  
  
```  
  
## 备注  
 **nonbrowsable** C\+\+ 特性具有与 [nonbrowsable](http://msdn.microsoft.com/library/windows/desktop/aa367117) MIDL 属性相同。  
  
## 示例  
  
```  
// cpp_attr_ref_nonbrowsable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, helpstring("help string"), helpstringcontext(1),   
uuid="11111111-1111-1111-1111-111111111111"]   
__interface IMyI  
{  
   [nonbrowsable] HRESULT xx();  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)