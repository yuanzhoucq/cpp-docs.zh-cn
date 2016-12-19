---
title: "index 类 | Microsoft Docs"
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
  - "amp/Concurrency::index"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "index 结构"
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# index 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

定义一个 *N* 维的索引点。  
  
## 语法  
  
```  
template <  
   int _Rank  
>  
class index;  
```  
  
#### 参数  
 `_Rank`  
 秩或维数。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[index::index 构造函数](../Topic/index::index%20Constructor.md)|初始化 `index` 类的新实例。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[index::operator\-\- 运算符](../Topic/index::operator--%20Operator.md)|递减 `index` 对象中的每个元素。|  
|[index::operator\(mod\)\= 运算符](../Topic/index::operator\(mod\)=%20Operator.md)|在元素除以某个数时，计算出 `index` 对象中每个元素的模数（余数）。|  
|[index::operator\*\= 运算符](../Topic/index::operator*=%20Operator.md)|将 `index` 对象的每个元素乘以数字。|  
|[index::operator\/\= 运算符](../Topic/index::operator-=%20Operator2.md)|将 `index` 对象的每个元素除以一个数字。|  
|[index::operatorOperator](../Topic/index::operatorOperator.md)|返回位于指定索引处的元素。|  
|[index::operator\+\+ 运算符](../Topic/index::operator++%20Operator.md)|递增 `index` 对象中每个元素。|  
|[index::operator\+\= 运算符](../Topic/index::operator+=%20Operator.md)|将指定数字添加到 `index` 对象的每个元素中。|  
|[index::operator\= 运算符](../Topic/index::operator=%20Operator.md)|将指定的 `index` 对象的内容复制到此对象中。|  
|[index::operator\-\= 运算符](../Topic/index::operator-=%20Operator1.md)|从 `index` 对象的每个元素中减去指定数字。|  
  
### 公共常量  
  
|名称|描述|  
|--------|--------|  
|[index::rank 常量](../Topic/index::rank%20Constant.md)|存储 `index` 对象的秩。|  
  
## 继承层次结构  
 `index`  
  
## 备注  
 `index` 结构代表 *N* 整数的坐标向量，其指定 *N*\-维空间中的唯一位置。  矢量中的值按最重要到最不重要的顺序排列。  您可使用 [index::operator\= 运算符](../Topic/index::operator=%20Operator.md) 检索组件的值。  
  
## 要求  
 **标头：**amp.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)