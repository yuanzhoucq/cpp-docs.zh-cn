---
title: "licensed | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.licensed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "licensed attribute"
ms.assetid: 09cf3b4a-d3f2-43e3-9180-d420333b23bf
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# licensed
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示其适用的 COM 对象授权，使用 **IClassFactory2**，并且必须实例化。  
  
## 语法  
  
```  
  
[licensed]  
  
```  
  
## 备注  
 **允许** C\+\+ 特性具有与 [允许](http://msdn.microsoft.com/library/windows/desktop/aa367070) MIDL 属性相同。  
  
## 示例  
  
```  
// cpp_attr_ref_licensed.cpp  
// compile with: /LD  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {  
   HRESULT f();  
};  
  
[coclass, version("2.1"), uuid(12345678-1111-2222-3333-123456789012),   
licensed, threading(free), progid(some.name)]  
class CSample : public IMyI {  
public:  
   int nSize;  
};  
  
[module(name="MyLibrary", version="1.0", helpstring="My Library Block")];  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|**coclass**|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)