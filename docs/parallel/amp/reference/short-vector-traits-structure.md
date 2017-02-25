---
title: "short_vector_traits 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_short_vectors/Concurrency::graphics::short_vector_traits"
dev_langs: 
  - "C++"
ms.assetid: cd9492da-9e02-4a6e-9d50-b61252cdb460
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# short_vector_traits 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

short\_vector\_traits 允许基本的向量长度和短的矢量类型或标量类型的标量类型复审  
  
## 语法  
  
```  
template<  
   typename _Type  
>  
struct short_vector_traits;  
template<>  
struct short_vector_traits<unsigned int>;  
template<>  
struct short_vector_traits<uint_2>;  
template<>  
struct short_vector_traits<uint_3>;  
template<>  
struct short_vector_traits<uint_4>;  
template<>  
struct short_vector_traits<int>;  
template<>  
struct short_vector_traits<int_2>;  
template<>  
struct short_vector_traits<int_3>;  
template<>  
struct short_vector_traits<int_4>;  
template<>  
struct short_vector_traits<float>;  
template<>  
struct short_vector_traits<float_2>;  
template<>  
struct short_vector_traits<float_3>;  
template<>  
struct short_vector_traits<float_4>;  
template<>  
struct short_vector_traits<unorm>;  
template<>  
struct short_vector_traits<unorm_2>;  
template<>  
struct short_vector_traits<unorm_3>;  
template<>  
struct short_vector_traits<unorm_4>;  
template<>  
struct short_vector_traits<norm>;  
template<>  
struct short_vector_traits<norm_2>;  
template<>  
struct short_vector_traits<norm_3>;  
template<>  
struct short_vector_traits<norm_4>;  
template<>  
struct short_vector_traits<double>;  
template<>  
struct short_vector_traits<double_2>;  
template<>  
struct short_vector_traits<double_3>;  
template<>  
struct short_vector_traits<double_4>;  
```  
  
#### 参数  
 `_Type`  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`value_type`||  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[short\_vector\_traits::short\_vector\_traits 构造函数](../Topic/short_vector_traits::short_vector_traits%20Constructor.md)||  
  
### 公共常量  
  
|名称|说明|  
|--------|--------|  
|[short\_vector\_traits::size 常量](../Topic/short_vector_traits::size%20Constant.md)||  
  
## 继承层次结构  
 `short_vector_traits`  
  
## 要求  
 **页眉：**amp\_short\_vectors.h  
  
 **命名空间：**Concurrency::graphics  
  
## 请参阅  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)