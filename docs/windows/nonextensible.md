---
title: "nonextensible | Microsoft Docs"
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
  - "vc-attr.nonextensible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nonextensible attribute"
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nonextensible
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 `IDispatch` 实现接口中声明包括只有列表的属性和方法，而不能扩展与运行时的其他成员。  
  
## 语法  
  
```  
  
[nonextensible]  
  
```  
  
## 备注  
 **nonextensible** C\+\+ 特性具有与 [nonextensible](http://msdn.microsoft.com/library/windows/desktop/aa367120) MIDL 属性相同。  
  
 为 **nonextensible** 的使用还需要 [custom](../windows/oleautomation.md) 属性。  
  
## 示例  
 下面的代码演示 **nonextensible** 属性的一个用途:  
  
```  
// cpp_attr_ref_nonextensible.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export] typedef long HRESULT;  
  
[dual, nonextensible, ms_union, oleautomation,   
uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   HRESULT procedure (int i);   
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`|  
|**可重复**|否|  
|**必需的特性**|**双** 和 **custom**或 **dispinterface**|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)