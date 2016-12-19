---
title: "call_as | Microsoft Docs"
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
  - "vc-attr.call_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "call_as attribute"
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# call_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使 [本地](../windows/local-cpp.md) 函数映射到远程功能，这样，当该远程函数调用时，将更新本地函数调用。  
  
## 语法  
  
```  
  
      [ call_as(  
   function  
) ]  
```  
  
#### 参数  
 *Function — 函数*  
 要调用的本地函数，当远程函数调用。  
  
## 备注  
 **call\_as** C\+\+ 特性具有与 [call\_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) MIDL 属性相同。  
  
## 示例  
 下面的代码演示如何使用 **call\_as** 映射一个不可远程控制的功能 \(**f1**\) 为一个可远程处理功能 \(**Remf1**\):  
  
```  
// cpp_attr_ref_call_as.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[dual, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMInterface {  
   [local] HRESULT f1 ( int i );  
   [call_as(f1)] HRESULT Remf1 ( int i );   
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
 [local](../windows/local-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)