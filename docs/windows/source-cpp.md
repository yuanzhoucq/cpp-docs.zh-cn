---
title: "source (C++) | Microsoft Docs"
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
  - "vc-attr.source"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "source attribute"
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# source (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在类中，指定 COM 对象的源接口的连接点。  在属性或方法，指示成员返回作为事件源的对象或变量。  
  
## 语法  
  
```  
  
      [ source(  
   interfaces  
) ]  
```  
  
#### 参数  
 `interfaces`  
 您指定的一个或多个接口何时将源特性应用于类。  此参数，当源应用于属性或方法时，将不使用。  
  
## 备注  
 **源** C\+\+ 特性具有与 [源](http://msdn.microsoft.com/library/windows/desktop/aa367166) MIDL 属性相同。  
  
 可以使用 [默认](../windows/default-cpp.md) 属性为对象指定默认值源接口。  
  
## 示例  
  
```  
// cpp_attr_ref_source.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid(11111111-1111-1111-1111-111111111111)]  
__interface b  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]  
   HRESULT get_I([out, retval]long *i);  
};  
  
[object, uuid(11111111-1111-1111-1111-111111111131)]  
__interface c  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]   
   HRESULT et_I([out, retval]long *i);  
};  
  
[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]  
class N : public b  
{  
};  
  
[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]  
class NN : public b  
{  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`， `interface`|  
|**可重复**|否|  
|**必需的特性**|**coclass** \(在对类或结构\)|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [coclass](../windows/coclass.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)