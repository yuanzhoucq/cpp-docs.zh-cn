---
title: "SafeInt::SafeInt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeInt::SafeInt"
  - "SafeInt"
  - "SafeInt.SafeInt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeInt 类, 构造函数"
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# SafeInt::SafeInt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造 `SafeInt` 对象。  
  
## 语法  
  
```  
SafeInt() throw  
  
SafeInt (  
   const T& i  
) throw ()  
  
SafeInt (  
   bool b  
) throw ()  
  
template <typename U>  
SafeInt (  
   const SafeInt <U, E>& u  
)  
  
I template <typename U>  
SafeInt (  
   const U& i  
)  
```  
  
#### 参数  
 \[in\] `i`  
 新的对象`SafeInt`值。  这必须是类型 T 或 U ，根据构造函数。  
  
 \[in\] `b`  
 新对象`SafeInt`的初始布尔值。  
  
 \[in\] `u`  
 U类型的`SafeInt`。  新 `SafeInt` 对象将包含和 `u`相同的值，但是，其类型为 T。  
  
 U  
 存储在`SafeInt`所述数据的类型。  它可以是字符、整数、布尔类型。  如果是整数类型，它可以带符号或无符号和在 8 位和 64 之间。  
  
## 备注  
 有关此类型的模板类型`T` 和 `E`的更多信息，请参见 [SafeInt 类](../windows/safeint-class.md)。  
  
 构造函数，`i` 或 `u`的输入参数，必须是布尔值、字符、整数类型。  如果是其他类型参数，`SafeInt` 类调用 [static\_assert](../cpp/static-assert.md) 指示无效的输入参数。  
  
 自动使用模板类型 `U` 的构造函数以转换输入参数为 `T`指定的类型。  `SafeInt` 类被转换数据，而无任何丢失数据。  如果它不能转换数据类型没有 `T` 数据丢失，`E` 报告其移到错误处理程序。  
  
 如果创建的布尔型参数的 `SafeInt`，需要直接初始化值。  使用代码 `SafeInt<bool> sb;`，不可以构造 `SafeInt`。   将产生编译错误。  
  
## 要求  
 **头文件:** safeint.h  
  
 **命名空间：** msl::utilities  
  
## 请参阅  
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeInt 类](../windows/safeint-class.md)   
 [SafeIntException 类](../windows/safeintexception-class.md)