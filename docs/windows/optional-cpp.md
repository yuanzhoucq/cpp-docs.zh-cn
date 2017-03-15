---
title: "optional (C++) | Microsoft Docs"
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
  - "vc-attr.optional"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "optional attribute"
ms.assetid: 86656a66-8e11-4589-8e30-9b0f34eeed03
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# optional (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于成员函数指定一个可选参数。  
  
## 语法  
  
```  
  
[optional]  
  
```  
  
## 备注  
 **选项** C\+\+ 特性具有与 [选项](http://msdn.microsoft.com/library/windows/desktop/aa367132) MIDL 属性相同。  
  
## 示例  
 下面的代码演示如何使用 **选项** :  
  
```  
// cpp_attr_ref_optional.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(1)] long procedure ([in, optional] VARIANT i);  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|接口参数|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)