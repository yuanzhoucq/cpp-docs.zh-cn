---
title: "idl_quote | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.idl_quote"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "idl_quote attribute"
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# idl_quote
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用在 Visual C\+\+ 的当前版本不支持的 IDL 构造并将它们传递到生成的 .idl 文件。  
  
## 语法  
  
```  
  
      [ idl_quote(  
   text  
) ]  
```  
  
#### 参数  
 *text*  
 属性名称要 Visual C\+\+ 编译器传递到生成的 .idl 文件，而无需返回编译器错误。  
  
## 备注  
 如果 **idl\_quote** C\+\+ 特性用作独立属性 \(与结束括号后面的分号\)，则 *文本* 在合并的 .idl 文件放置。  如果 **idl\_quote** 在符号使用， *文本* 在特性中放置为该符号块。  
  
## 示例  
 下面的代码演示如何使用 **在**，可以如何指定 \(的不支持的属性，支持\) 以及如何定义和使用未定义 .idl 构造:  
  
```  
// cpp_attr_ref_idl_quote.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
  
[export]  
struct MYFLOT {  
   int i;  
};  
  
[export]  
struct MYDUB {  
   int i;  
};  
  
[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \  
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];  
  
typedef struct _S1_TYPE {   
   long l1;   
  
union {   
   MYFLOT f1; MYDUB d2; } U1_TYPE;   
} S1_TYPE;  
  
[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]  
__interface IStatic{  
   HRESULT Func1([idl_quote("in")] int i);  
   HRESULT func( S1_TYPE* myStruct );  
};  
```  
  
 此代码产生 MYFLOT 和 MYDUB 和在生成的 .idl 文件上的文本输入。  *名称* 参数强制 *文本* 在引用在生成的 .idl 文件的 *名称* 的任何之前放置。  参数强制依赖项的 *依赖项* 列表在 *文本之前* 上的定义在生成的 .idl 文件。  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)