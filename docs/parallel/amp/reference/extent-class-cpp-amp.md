---
title: "extent 类 (C++ AMP) | Microsoft Docs"
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
  - "amp/Concurrency::extent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extent 结构"
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
caps.latest.revision: 19
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# extent 类 (C++ AMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示指定原始为 0 的 *N* 维空间边界的 *N* 个整数值的矢量。  矢量中的值按最重要到最不重要的顺序排列。  
  
## 语法  
  
```  
template <  
   int _Rank>  
class extent;  
```  
  
#### 参数  
 `_Rank`  
 `extent` 对象的秩。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[extent::extent 构造函数](../Topic/extent::extent%20Constructor.md)|初始化 `extent` 类的新实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[extent::contains 方法](../Topic/extent::contains%20Method.md)|验证指定的 `extent` 对象是否具有指定的级别。|  
|[extent::size 方法](../Topic/extent::size%20Method.md)|返回该范围的总线性大小（以元素单位）。|  
|[extent::tile 方法](../Topic/extent::tile%20Method.md)|生成带特定维度的图标内容的 `tiled_extent` 对象。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[extent::operator\- 运算符](../Topic/extent::operator-%20Operator.md)|返回通过从对应的 `extent` 元素减去 `index` 元素创建的新 `extent` 对象。|  
|[extent::operator\-\- 运算符](../Topic/extent::operator--%20Operator.md)|递减 `extent` 对象中的每个元素。|  
|[extent::operator\(mod\)\= 运算符](../Topic/extent::operator\(mod\)=%20Operator.md)|在元素除以某个数时，计算出 `extent` 对象中每个元素的模数（余数）。|  
|[extent::operator\*\= 运算符](../Topic/extent::operator*=%20Operator.md)|将 `extent` 对象的每个元素乘以数字。|  
|[extent::operator\/\= 运算符](../Topic/extent::operator-=%20Operator1.md)|将 `extent` 对象的每个元素除以一个数字。|  
|[extent::operatorOperator](../Topic/extent::operatorOperator.md)|返回位于指定索引处的元素。|  
|[extent::operator\+ 运算符](../Topic/extent::operator+%20Operator.md)|返回通过对应的 `index` 和 `extent` 元素合并创建的新 `extent` 对象。|  
|[extent::operator\+\+ 运算符](../Topic/extent::operator++%20Operator.md)|递增 `extent` 对象中每个元素。|  
|[extent::operator\+\= 运算符](../Topic/extent::operator+=%20Operator.md)|将指定数字添加到 `extent` 对象的每个元素中。|  
|[extent::operator\= 运算符](../Topic/extent::operator=%20Operator.md)|将另一 `extent` 对象的内容复制到此对象中。|  
|[extent::operator\-\= 运算符](../Topic/extent::operator-=%20Operator2.md)|从 `extent` 对象的每个元素中减去指定数字。|  
  
### 公共常量  
  
|名称|描述|  
|--------|--------|  
|[extent::rank 常量](../Topic/extent::rank%20Constant.md)|获取 `extent` 对象的秩。|  
  
## 继承层次结构  
 `extent`  
  
## 要求  
 **标头：**amp.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)