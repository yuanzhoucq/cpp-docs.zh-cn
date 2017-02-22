---
title: "dual | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.dual"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dual attribute"
ms.assetid: 5d4a9069-d819-42cd-ba56-bbcda17157d9
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# dual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 .idl 文件中放置一个接口该接口。  
  
## 语法  
  
```  
  
[dual]  
  
```  
  
## 备注  
 当 **双** C\+\+ 特性前面接口时，它将在生成的 .idl 文件错误引起接口放置在库中块。  
  
## 示例  
 下面的代码是特性块在接口定义之前使用 **双** :  
  
```  
// cpp_attr_ref_dual.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
  
[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), dual]  
  
__interface IStatic : IDispatch   
{  
   HRESULT Func1(int i);  
   [   propget,   
      id(1),   
      bindable,   
      displaybind,   
      defaultbind,   
      requestedit  
   ]   
   HRESULT P1([out, retval] long *nSize);  
   [   propput,   
      id(1),   
      bindable,   
      displaybind,   
      defaultbind,   
      requestedit  
   ]   
   HRESULT P1([in] long nSize);      
};  
  
[cpp_quote("#include file.h")];  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|**dispinterface**|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes by Usage](../windows/attributes-by-usage.md)   
 [custom](../windows/custom-cpp.md)   
 [dispinterface](../windows/dispinterface.md)   
 [object](../windows/object-cpp.md)   
 [\_\_interface](../cpp/interface.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)