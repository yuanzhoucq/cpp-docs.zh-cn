---
title: "uidefault | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.uidefault"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uidefault attribute"
ms.assetid: 200de0e0-2e34-40a2-bae4-8d485a62264d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# uidefault
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示该类型信息成员是显示的默认成员。用户界面。  
  
## 语法  
  
```  
  
[uidefault]  
  
```  
  
## 备注  
 **uidefault** C\+\+ 特性具有与 [uidefault](http://msdn.microsoft.com/library/windows/desktop/aa367292) MIDL 属性相同。  
  
## 示例  
 下面的代码演示 **uidefault**示例:  
  
```  
// cpp_attr_ref_uidefault.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom{  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
   [uidefault]HRESULT id0([in] long l);  
   [uidefault]HRESULT id1([in] long l);  
  
   [uidefault, propget] HRESULT get_y(int *y);  
   [uidefault, propput] HRESULT put_y(int y);  
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