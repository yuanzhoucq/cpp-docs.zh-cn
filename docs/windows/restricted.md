---
title: "restricted | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.restricted"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "restricted attribute"
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# restricted
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定模块、接口或调度接口的成员不能随机调用。  
  
## 语法  
  
```  
  
      [ restricted(  
   interfaces  
) ]  
```  
  
#### 参数  
 `interfaces`  
 在 COM 对象不能随机调用的一个或多个接口。  此参数只有效，在对类。  
  
## 备注  
 **限制** C\+\+ 特性具有与 [限制](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL 属性相同。  
  
## 示例  
 下面的代码演示如何使用 **限制** 属性:  
  
```  
// cpp_attr_ref_restricted.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface b  
{  
};  
  
[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]  
class c : public a, public b  
{  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|接口方法， `interface`， **类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|**coclass** \(当应用于 **类** 或 `struct`\)|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)