---
title: "appobject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.appobject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "appobject attribute"
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# appobject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标识 coclass 为应用程序对象，与完整的 .exe 应用程序，并指示 coclass 的功能和特性是全局可用本 [类型库](../mfc/automation-clients-using-type-libraries.md)。  
  
## 语法  
  
```  
  
[appobject]  
  
```  
  
## 备注  
 **appobject** C\+\+ 特性具有与 [appobject](http://msdn.microsoft.com/library/windows/desktop/aa366726) MIDL 属性相同。  
  
## 示例  
 下面的代码演示包含 **appobject**的属性后的简单类定义块:  
  
```  
// cpp_attr_ref_appobject.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];  
  
[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]  
__interface ICustom {};  
  
[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]  
class A : public ICustom {  
   int i;  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`|  
|**可重复**|否|  
|**必需的特性**|**coclass**|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)