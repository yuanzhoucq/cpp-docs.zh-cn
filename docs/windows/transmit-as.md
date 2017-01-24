---
title: "transmit_as | Microsoft Docs"
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
  - "vc-attr.transmit_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "transmit_as attribute"
ms.assetid: 53d0b8ab-5b06-423e-83eb-3d01a10424b2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# transmit_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示编译器关联客户端和服务器应用程序操作的一个存在的类型，使用一个传输的类型。  
  
## 语法  
  
```  
  
      [ transmit_as(  
   type  
) ]  
```  
  
#### 参数  
 `type`  
 指定传输是在客户端和服务器之间的数据类型。  
  
## 备注  
 **transmit\_as** C\+\+ 特性具有与 [transmit\_as](http://msdn.microsoft.com/library/windows/desktop/aa367286) MIDL 属性相同。  
  
## 示例  
 下面的代码演示 **transmit\_as** 属性的用法:  
  
```  
// cpp_attr_ref_transmit_as.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[export] typedef struct _TREE_NODE_TYPE {  
unsigned short data;   
struct _TREE_NODE_TYPE * left;  
struct _TREE_NODE_TYPE * right;   
} TREE_NODE_TYPE;  
  
[export] struct PACKED_NODE {  
   unsigned short data;   // same as normal node  
   int index;   // array index of parent  
};  
  
// A left node recursive built array of  
// the nodes in the tree.  Can be unpacked with  
// that knowledge  
[export] typedef struct _TREE_XMIT_TYPE {  
   int count;  
   [size_is(count)] PACKED_NODE node[];  
} TREE_XMIT_TYPE;  
  
[transmit_as(TREE_XMIT_TYPE)] typedef TREE_NODE_TYPE * TREE_TYPE;  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|`typedef`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)