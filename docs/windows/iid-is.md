---
title: "iid_is | Microsoft Docs"
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
  - "vc-attr.iid_is"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iid_is attribute"
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# iid_is
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 COM 接口的 IID 指向接口指针。  
  
## 语法  
  
```  
  
      [ iid_is(  
   "expression"  
) ]  
```  
  
#### 参数  
 *表达式*  
 对. 指定 COM 接口的 IID 的语言表达式指向接口指针。  
  
## 备注  
 **iid\_is** C\+\+ 特性具有与 [iid\_is](http://msdn.microsoft.com/library/windows/desktop/aa367044) MIDL 属性相同。  
  
## 示例  
 下面的代码演示如何使用 **iid\_is**:  
  
```  
// cpp_attr_ref_iid_is.cpp  
// compile with: /LD  
#include "wtypes.h"  
#include "unknwn.h"  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]   
   IUnknown ** ppvObject);  
};  
  
[module(name="ATLFIRELib")];  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|接口参数，数据成员|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)