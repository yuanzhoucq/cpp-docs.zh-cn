---
title: "defaultvalue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.defaultvalue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "defaultvalue attribute"
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# defaultvalue
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

允许默认的规范一个类型化可选参数的。  
  
## 语法  
  
```  
  
[ defaultvalue= value ]  
```  
  
#### 参数  
 *值*  
 参数的默认值。  
  
## 备注  
 **defaultvalue** C\+\+ 特性具有与 [defaultvalue](http://msdn.microsoft.com/library/windows/desktop/aa366793) MIDL 属性相同。  
  
## 示例  
 使用 **defaultvalue** 属性，下面的代码演示一个接口方法:  
  
```  
// cpp_attr_ref_defaultvalue.cpp  
// compile with: /LD  
#include <windows.h>  
  
[export] typedef long HRESULT;  
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;  
  
[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"),  
   dual, oleautomation,  
   helpstring("IFireTabCtrl Interface"),  
   helpcontext(122), pointer_default(unique) ]  
  
__interface IFireTabCtrl : IDispatch {  
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);  
   [bindable, propput] HRESULT put_Size([in] int nSize);  
};  
  
[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",  
      version="1.0", helpstring="ATLFire 1.0 Type Library") ];  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|接口参数|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [输出](../windows/out-cpp.md)   
 [retval](../windows/retval.md)   
 [in](../windows/in-cpp.md)   
 [pointer\_default](../windows/pointer-default.md)   
 [unique](../windows/unique-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)