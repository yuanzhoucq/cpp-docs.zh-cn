---
title: "readonly (C++) | Microsoft Docs"
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
  - "vc-attr.readonly"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "readonly 特性"
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# readonly (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

禁止分配给数据成员。  
  
## 语法  
  
```  
  
[readonly]  
  
```  
  
## 备注  
 **readonly** C\+\+ 属性具有与 [readonly](http://msdn.microsoft.com/library/windows/desktop/aa367152) MIDL 属性相同的功能。  
  
 如果要禁止修改方法参数，则使用 [in](../windows/in-cpp.md) 属性。  
  
## 示例  
 下面的代码演示的 **readonly** 属性的用法：  
  
```  
// cpp_attr_ref_readonly.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
  
[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]  
__interface IFireTabCtrl  
{  
   [readonly, id(1)] int i();  
};  
```  
  
## 要求  
  
### 特性上下文  
  
|||  
|-|-|  
|**适用对象**|接口方法|  
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见[特性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Data Member Attributes](../windows/data-member-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)