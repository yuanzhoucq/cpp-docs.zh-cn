---
title: "async_uuid | Microsoft Docs"
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
  - "vc-attr.async_uuid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "async_uuid attribute"
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# async_uuid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定处理 MIDL 编译器定义 COM 接口的同步和异步版本的 UUID。  
  
## 语法  
  
```  
  
      [async_uuid (  
   uuid  
)]  
```  
  
#### 参数  
 *uuid*  
 标识接口的版本的 UUID。  
  
## 备注  
 **async\_uuid** C\+\+ 特性具有与 [async\_uuid](http://msdn.microsoft.com/library/windows/desktop/aa366735) MIDL 属性相同。  
  
## 示例  
  
```  
// cpp_attr_ref_async_uuid.cpp  
// compile with: /LD  
#include <Windows.h>  
[module(name="Test")];  
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),   
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|**双**， **dispinterface**|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Interface Attributes](../windows/interface-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)