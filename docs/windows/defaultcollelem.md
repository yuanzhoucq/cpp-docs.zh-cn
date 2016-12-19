---
title: "defaultcollelem | Microsoft Docs"
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
  - "vc-attr.defaultcollelem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "defaultcollelem attribute"
ms.assetid: 3dbbd293-8b83-4f70-a36b-64cc1d0b6713
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# defaultcollelem
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于 Visual Basic 代码优化。  
  
## 语法  
  
```  
  
[defaultcollelem]  
  
```  
  
## 备注  
 **defaultcollelem** C\+\+ 特性具有与 [defaultcollelem](http://msdn.microsoft.com/library/windows/desktop/aa366792) MIDL 属性相同。  
  
## 示例  
 使用 **defaultcollelem** 属性，下面的代码演示一个接口方法:  
  
```  
// cpp_attr_ref_defaultcollelem.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyForm   
{     
   [propget, id(1), bindable, defaultcollelem, displaybind,   
   defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);  
   [propput, id(1), bindable, defaultcollelem, displaybind,   
   defaultbind, requestedit] HRESULT P1([in] long nSize);  
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
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)