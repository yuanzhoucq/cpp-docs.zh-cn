---
title: "export | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.export"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "export attribute"
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# export
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 .idl 文件中创建一个数据结构将。  
  
## 语法  
  
```  
  
[export]  
  
```  
  
## 备注  
 **导出** C\+\+ 特性在 .idl 文件中创建一个数据结构将然后可用于类型库在能够为与所有语言的二进制兼容格式。  
  
 不能将 **导出** 特性应用于类，即使类只有公共成员 \( `struct`的等效项\)。  
  
 如果导出未命名的 `enum`的或 `struct`的，它们是从 **\_\_unnamed***x*开头的名称，其中 *x* 是序列号。  
  
 typedef 有效范围导出是基类型、结构、联合、枚举或类型标识符。  请参见 [typedef](http://msdn.microsoft.com/library/windows/desktop/aa367287) 有关更多信息。  
  
## 示例  
 下面的代码演示如何使用 **导出** 属性:  
  
```  
// cpp_attr_ref_export.cpp  
// compile with: /LD  
[module(name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|**联合**、 `typedef`、 `enum`、 `struct`或 `interface`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [Compiler Attributes](../windows/compiler-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)