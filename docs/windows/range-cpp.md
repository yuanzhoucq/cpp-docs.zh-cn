---
title: "range (C++) | Microsoft Docs"
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
  - "vc-attr.range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range attribute"
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# range (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为值设置在运行时的参数或字段指定允许值的大小。  
  
## 语法  
  
```  
  
      [ range(  
   low,   
   high  
) ]  
```  
  
#### 参数  
 *低*  
 低值范围。  
  
 *高*  
 上限值。  
  
## 备注  
 **范围** C\+\+ 特性具有与 [范围](http://msdn.microsoft.com/library/windows/desktop/aa367151) MIDL 属性相同。  
  
## 示例  
  
```  
// cpp_attr_ref_range.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);  
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|接口方法，接口参数|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Method Attributes](../windows/method-attributes.md)   
 [Parameter Attributes](../windows/parameter-attributes.md)   
 [Data Member Attributes](../windows/data-member-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)