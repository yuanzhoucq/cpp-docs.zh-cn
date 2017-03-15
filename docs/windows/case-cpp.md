---
title: "case (C++) | Microsoft Docs"
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
  - "vc-attr.case"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "case attribute"
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# case (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 [switch\_type](../windows/switch-type.md) 属性。 **联合**。  
  
## 语法  
  
```  
  
      [ case(  
   value  
) ]  
```  
  
#### 参数  
 *值*  
 要提供处理的一个可能的输入值。  **值** 的类型可为下列类型之一:  
  
-   `int`  
  
-   `char`  
  
-   **boolean**  
  
-   `enum`  
  
 或这样的类型标识符。  
  
## 备注  
 **用例** C\+\+ 特性具有与 **用例** MIDL 属性相同。  此属性仅用于 [switch\_type](../windows/switch-type.md) 属性。  
  
## 示例  
 下面的代码演示 **用例** 属性的用法:  
  
```  
// cpp_attr_ref_case.cpp  
// compile with: /LD  
#include <unknwn.h>  
[export]  
struct SizedValue2 {  
   [switch_type(char), switch_is(kind)] union {  
      [case(1), string]  
          wchar_t* wval;  
      [default, string]  
          char* val;  
   };  
    char kind;  
};  
[module(name="ATLFIRELib")];  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**类** 或 `struct`的成员|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关属性上下文的更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)