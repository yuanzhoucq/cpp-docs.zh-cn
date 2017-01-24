---
title: "uint_2 类 | Microsoft Docs"
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
  - "amp_short_vectors/Concurrency::graphics::uint_2::set_xy"
  - "amp_short_vectors/Concurrency::graphics::uint_2::y"
  - "amp_short_vectors/Concurrency::graphics::uint_2::gr"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator-"
  - "amp_short_vectors/Concurrency::graphics::uint_2::get_x"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator-="
  - "amp_short_vectors/Concurrency::graphics::uint_2::r"
  - "amp_short_vectors/Concurrency::graphics::uint_2::yx"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator--"
  - "amp_short_vectors/Concurrency::graphics::uint_2::set_yx"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator="
  - "amp_short_vectors/Concurrency::graphics::uint_2::set_x"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator+="
  - "amp_short_vectors/Concurrency::graphics::uint_2::get_y"
  - "amp_short_vectors/Concurrency::graphics::uint_2::xy"
  - "amp_short_vectors/Concurrency::graphics::uint_2::x"
  - "amp_short_vectors/Concurrency::graphics::uint_2::get_xy"
  - "amp_short_vectors/Concurrency::graphics::uint_2::set_y"
  - "amp_short_vectors/Concurrency::graphics::uint_2"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator*="
  - "amp_short_vectors/Concurrency::graphics::uint_2::get_yx"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator/="
  - "amp_short_vectors/Concurrency::graphics::uint_2::g"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator++"
  - "amp_short_vectors/Concurrency::graphics::uint_2::rg"
dev_langs: 
  - "C++"
ms.assetid: 9fcc9129-72b1-4da7-9012-4d3be15f1c52
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# uint_2 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示四个无符号整数短矢量。  
  
## 语法  
  
```  
class uint_2;  
```  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|描述|  
|--------|--------|  
|`value_type`||  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[uint\_2::uint\_2 构造函数](../Topic/uint_2::uint_2%20Constructor.md)|已重载。  默认构造函数，初始化 0 的所有元素。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|uint\_2::get\_x 方法||  
|uint\_2::get\_xy 方法||  
|uint\_2::get\_y 方法||  
|uint\_2::get\_yx 方法||  
|uint\_2::ref\_g 方法||  
|uint\_2::ref\_r 方法||  
|uint\_2::ref\_x 方法||  
|uint\_2::ref\_y 方法||  
|uint\_2::set\_x 方法||  
|uint\_2::set\_xy 方法||  
|uint\_2::set\_y 方法||  
|uint\_2::set\_yx 方法||  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|uint\_2::operator\-\-运算符||  
|uint\_2::operator%\=运算符||  
|uint\_2::operator&\=运算符||  
|uint\_2::operator\*\=运算符||  
|uint\_2::operator\/\=运算符||  
|uint\_2::operator^\= 运算符||  
|uint\_2::operator&#124;\=运算符||  
|uint\_2::operator~运算符||  
|uint\_2::operator\+\+运算符||  
|uint\_2::operator\+\=运算符||  
|uint\_2::operator\<\<\=运算符||  
|uint\_2::operator\=运算符||  
|uint\_2::operator\-\=运算符||  
|uint\_2::operator\>\>\=运算符||  
  
### 公共常量  
  
|名称|描述|  
|--------|--------|  
|[uint\_2::size 常量](../Topic/uint_2::size%20Constant.md)||  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|uint\_2::g 常数数据成员。||  
|uint\_2::gr 常数数据成员。||  
|uint\_2::r 常数数据成员。||  
|uint\_2::rg 常数数据成员。||  
|uint\_2::x 数据成员||  
|uint\_2::xy 数据成员||  
|uint\_2::y 数据成员||  
|uint\_2::yx 数据成员||  
  
## 继承层次结构  
 `uint_2`  
  
## 要求  
 **页眉：**amp\_short\_vectors.h  
  
 **命名空间：**Concurrency::graphics  
  
## 请参阅  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)