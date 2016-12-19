---
title: "string (C++) | Microsoft Docs"
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
  - "vc-attr.string"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "string attribute"
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# string (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示一维 `char`、 `wchar_t`、 **字节** \(或等效\) 数组或指针到此数组必须将字符串。  
  
## 语法  
  
```  
  
[string]  
  
```  
  
## 备注  
 **字符串** C\+\+ 特性具有与 [字符串](http://msdn.microsoft.com/library/windows/desktop/aa367270) MIDL 属性相同。  
  
## 示例  
 下面的代码演示如何使用 **字符串** 在接口与在 typedef:  
  
```  
// cpp_attr_ref_string.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export, string] typedef char a[21];  
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1)] HRESULT Method3([in, string] char *pC);  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|数组或指针数组，接口参数，接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Array Attributes](../windows/array-attributes.md)   
 [export](../windows/export.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)