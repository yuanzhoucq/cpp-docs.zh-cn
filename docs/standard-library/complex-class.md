---
title: "complex 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "complex"
  - "std::complex"
  - "std.complex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "complex 类"
  - "复数"
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
caps.latest.revision: 18
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# complex 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述模板类存储类型 **类型**两个对象，表示复数的重载表示虚部一个和一个。  
  
## 语法  
  
```  
  
   template<class   
   Type  
   >  
class complex  
```  
  
## 备注  
 **类型**类的对象：  
  
-   有一个公共默认构造函数、析构函数、复制构造函数和赋值运算符。常规行为的。  
  
-   可以分配整数或浮点值，转换为或类型的常规行为这样的值。  
  
-   定义算术运算符和算术函数，根据需要，对于与常规行为的浮点类型定义。  
  
 特别是，细微的差别可能不存在。分配和结构之间按照默认的复制构造。  在类 **类型** 对象的操作都可能不引发异常。  
  
 模板的显式专用化。类对复杂三个浮点类型存在。  在此实现中，其他类型值 **类型** 是类型转换为实际 **double** 计算的结果，其中 **double** 分配回 **类型**类型`.`的存储对象  
  
### 构造函数  
  
|||  
|-|-|  
|[复杂](../Topic/complex::complex.md)|构造一个复数具有指定的实际和虚部的或作为其他这些副本。|  
  
### Typedef  
  
|||  
|-|-|  
|[value\_type](../Topic/complex::value_type.md)|表示用于的数据类型表示复数的物理和虚部的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[imag](../Topic/complex::imag.md)|提取的复数加法的组件。|  
|[real](../Topic/complex::real.md)|提取它的实际组件。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\*\=](../Topic/complex::operator*=.md)|将目标复数乘以因素，可能很复杂的或作为类型与它的物理和虚部。|  
|[运算符 \+\=](../Topic/complex::operator+=.md)|将数字到目标复数，添加数可能很复杂或类型与添加它的物理和虚部。|  
|[operator\-\=](../Topic/complex::operator-=1.md)|从目标复数减去数字减去的数字，可以是复杂或类型与添加它的物理和虚部。|  
|[operator\/\=](../Topic/complex::operator-=2.md)|该除数划分目标复数，可能很复杂的或作为类型与它的物理和虚部。|  
|[operator\=](../Topic/complex::operator=.md)|分配编号为目标复数，分配数可能很复杂或类型与它分配复数的物理和虚部。|  
  
## 要求  
 **标题**: \<复杂\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [complex Members](http://msdn.microsoft.com/zh-cn/d5c4466c-43a0-4817-aca1-9a5d492dae28)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)