---
title: "bindable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.bindable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bindable attribute"
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# bindable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示属性支持数据绑定。  
  
## 语法  
  
```  
  
[bindable]  
  
```  
  
## 备注  
 **可绑定** C\+\+ 特性具有与 [可绑定](http://msdn.microsoft.com/library/windows/desktop/aa366738) MIDL 属性相同。  您可以使用它在属性定义与 [propget](../windows/propget.md)、 [propput](../windows/propput.md)或 [propputref](../windows/propputref.md) 属性，也可以手动定义一个可绑定方法。  
  
 下面的 MFC 示例演示如何使用 **可绑定**:  
  
-   [控件示例:基于 MFC 的 Activex 控件](http://msdn.microsoft.com/zh-cn/a44adf86-0ba0-4504-bedb-512b6cba2e63)  
  
-   [CIRC 示例：ActiveX 控件](http://msdn.microsoft.com/zh-cn/9ba34d04-280e-49f4-90ae-41a6be44c95b)  
  
-   [TESTHELP 示例：具有工具提示和帮助的 ActiveX 控件](http://msdn.microsoft.com/zh-cn/d822861d-c6f0-4d0a-ad11-970eebb1e8cd)  
  
## 示例  
 下面的代码演示如何使用属性的 **可绑定** :  
  
```  
// cpp_attr_ref_bindable.cpp  
// compile with: /LD  
#include <windows.h>  
[  
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"),  
   dispinterface,  
   helpstring("property demo Interface")  
]  
__interface IPropDemo : IDispatch {  
  
   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);  
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);  
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);  
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);     
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();  
};  
  
[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];  
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
 [defaultbind](../windows/defaultbind.md)   
 [displaybind](../windows/displaybind.md)   
 [immediatebind](../windows/immediatebind.md)   
 [requestedit](../windows/requestedit.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)